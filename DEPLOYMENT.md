# Deploy Your Portfolio to adityabthakur.com.np

This project is set up to deploy to **GitHub Pages** via GitHub Actions. Follow these steps to make your site live on your domain.

---

## 1. Push to GitHub

Make sure your code is pushed to a GitHub repository:

```bash
git add .
git commit -m "Add GitHub Pages deployment"
git push origin main
```

---

## 2. Enable GitHub Pages

1. Go to your repo on GitHub → **Settings** → **Pages**
2. Under **Build and deployment**:
   - **Source**: Select **GitHub Actions**
3. Save (no need to pick a branch or folder)

---

## 3. Add Your Custom Domain

1. Still in **Settings** → **Pages**
2. Under **Custom domain**, enter: `adityabthakur.com.np`
3. Click **Save**
4. Check **Enforce HTTPS** once it becomes available (after DNS propagates)

---

## 4. Configure DNS in Cloudflare

Your domain uses Cloudflare. Add/update these DNS records:

| Type | Name | Content              | Proxy status |
|------|------|----------------------|--------------|
| CNAME | `@` or `adityabthakur` | `YOUR_USERNAME.github.io` | Proxied (orange cloud) |
| CNAME | `www` | `YOUR_USERNAME.github.io` | Proxied (orange cloud) |

Replace `YOUR_USERNAME` with your GitHub username.

**Note:** Some registrars don't allow CNAME on the root (`@`). If that fails, use GitHub's A records instead:

| Type | Name | Content         |
|------|------|-----------------|
| A    | `@`  | `185.199.108.153` |
| A    | `@`  | `185.199.109.153` |
| A    | `@`  | `185.199.110.153` |
| A    | `@`  | `185.199.111.153` |
| CNAME | `www` | `YOUR_USERNAME.github.io` |

---

## 5. Wait for Deployment

- The workflow runs automatically on every push to `main`
- Check **Actions** in your repo to see deployment status
- DNS can take a few minutes to 48 hours to propagate

Your site will be live at **https://adityabthakur.com.np** when both the deployment and DNS are ready.
