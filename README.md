## Content for theanalyticsai project

### Steps to setup github pages for custom domain:

#### Step 1: Create GitHub repo and turn on GitHub Pages

1. If it does not exist yet, create a repository using the naming pattern your-github-username.github.io. Since my username is benwiz my repository is called example.github.io .
2. Click the Settings tab and scroll down the GitHub Pages section
3. From the Source dropdown select master branch
4. Click Save

#### Step 2: Push source code to GitHub

1. Clone the repo to your local machine

```bash
git clone git@github.com:your-github-username/your-github-username.github.io.git && cd your-github-username.github.io
```

2. Create an index.html file with some content

```bash
echo "Hello GitHub Pages!" > index.html
```

3. Looking forward, we will need to have a file named CNAME that contains a single row: your custom domain. My CNAME file has the following contents.

```text
example.com
```

4. Push the files to GitHub

```bash
git add . && git commit -m 'Create content and CNAME record' && git push
```

#### Step 3: Confirm that GitHub pages has been deployed

Visit http://your-github-username.github.io and https://your-github-username.github.io. You should see the contents of your index.html file at both the unsecured and secured addresses.

#### Step 4: Configure AWS Route 53 to use your custom vanity domain

- Log into the AWS console and go to the Route 53 dashboard.
- Click Hosted zones
- Click the domain you would like to use

Set A name record

- Click Create Record Set
- Do not enter anything into the Name field
- Under the Type dropdown, select A — IPv4 addresses
- The Alias toggle should be set to No
- Enter the following four IP addresses into the value text area. Then click Save Record Set.
  185.199.108.153
  185.199.109.153
  185.199.110.153
  185.199.111.153
- save record

Set CNAME record

- Click Create Record Set
- Enter www into the Name field. If you want to setup at a subdomain, enter the subdomain name here.
- Under the Type dropdown, select CNAME
- The Alias toggle should be set to No
- Enter the value as your-github-username.github.io
- Save record

#### Step 5: Configure GitHub to serve over your custom domain

- Return to your GitHub repository’s settings tab
- Scroll down to the GitHub Pages section
- In the Custom domain field enter your custom domain: your-custom-domain.com
- Click Save
- Check Enforce HTTPS

#### Step 6: Confirm that your page is accessible at your custom domain

Visit https://your-custom-domain.com. You should see the contents of your index.html.

### Creating a GitHub Pages site with Jekyll

#### Setup

Follow the instructions at https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll

#### Testing your GitHub Pages site locally with Jekyll

Follow the instructions at https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll
