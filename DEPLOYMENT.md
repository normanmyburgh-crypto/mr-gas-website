# Deployment Guide for Mr Gas Website

This guide provides step-by-step instructions for deploying the Mr Gas website to various hosting platforms.

## Table of Contents

1. [Pre-Deployment Checklist](#pre-deployment-checklist)
2. [GitHub Pages Deployment](#github-pages-deployment)
3. [Netlify Deployment](#netlify-deployment)
4. [Vercel Deployment](#vercel-deployment)
5. [Traditional Hosting (cPanel)](#traditional-hosting-cpanel)
6. [Post-Deployment Tasks](#post-deployment-tasks)

---

## Pre-Deployment Checklist

Before deploying, ensure you have completed the following:

- [ ] **Replace placeholder logo** with actual Mr Gas logo
- [ ] **Verify all contact information** (phone, email, address)
- [ ] **Test website locally** on multiple devices/browsers
- [ ] **Update business hours** if different from template
- [ ] **Review all content** for accuracy
- [ ] **Add real customer testimonials** (with permission)
- [ ] **Optimize images** if you've added any
- [ ] **Test contact form** functionality
- [ ] **Set up email forwarding** for form submissions
- [ ] **Prepare Google Analytics** tracking ID (optional)
- [ ] **Review SEO meta tags** in index.html

---

## GitHub Pages Deployment

### Method 1: Using GitHub Web Interface (Easiest)

1. **Create a GitHub Account** (if you don't have one)
   - Go to https://github.com
   - Sign up for free

2. **Create a New Repository**
   - Click the "+" icon → "New repository"
   - Name it `mr-gas-website` (or any name you prefer)
   - Make it **Public**
   - Click "Create repository"

3. **Upload Files**
   - Click "uploading an existing file"
   - Drag and drop all website files:
     - index.html
     - styles.css
     - script.js
     - logo.svg
     - README.md
     - LICENSE
     - .gitignore
   - Click "Commit changes"

4. **Enable GitHub Pages**
   - Go to repository **Settings** (gear icon)
   - Scroll to **Pages** section (left sidebar)
   - Under "Source", select **main** branch
   - Click **Save**

5. **Access Your Website**
   - Wait 1-2 minutes for deployment
   - Your site will be at: `https://YOUR-USERNAME.github.io/mr-gas-website/`
   - GitHub will show you the URL in the Pages settings

### Method 2: Using Git Command Line

```bash
# 1. Initialize Git repository
cd mr-gas-website
git init

# 2. Add all files
git add .

# 3. Commit files
git commit -m "Initial commit - Mr Gas website"

# 4. Add remote repository (replace with your repo URL)
git remote add origin https://github.com/YOUR-USERNAME/mr-gas-website.git

# 5. Push to GitHub
git branch -M main
git push -u origin main

# 6. Enable GitHub Pages through Settings (see Method 1, step 4)
```

### Custom Domain Setup (Optional)

1. **Buy a domain** (e.g., www.mrgas.co.za)

2. **Add CNAME file** to your repository:
   ```
   www.mrgas.co.za
   ```

3. **Configure DNS** at your domain registrar:
   - Add a CNAME record pointing to `YOUR-USERNAME.github.io`

4. **Update GitHub Pages settings**:
   - Enter your custom domain
   - Enable "Enforce HTTPS"

---

## Netlify Deployment

### Method 1: Drag and Drop (Fastest)

1. **Visit Netlify Drop**
   - Go to https://app.netlify.com/drop

2. **Drag Your Folder**
   - Drag the entire `mr-gas-website` folder onto the page
   - Wait for upload to complete (usually 30 seconds)

3. **Your Site is Live!**
   - Netlify provides a URL like: `https://random-name-12345.netlify.app`
   - You can change this in Site settings

### Method 2: GitHub Integration

1. **Connect Netlify to GitHub**
   - Sign up at https://app.netlify.com
   - Click "New site from Git"
   - Choose "GitHub"
   - Authorize Netlify

2. **Select Repository**
   - Choose your `mr-gas-website` repository
   - Click "Deploy site"

3. **Automatic Deployments**
   - Every push to GitHub will auto-deploy
   - No manual updates needed!

### Custom Domain on Netlify

1. **Domain Settings**
   - Go to Site settings → Domain management
   - Click "Add custom domain"
   - Enter your domain (e.g., www.mrgas.co.za)

2. **Configure DNS**
   - Netlify provides DNS instructions
   - Add records at your domain registrar
   - SSL certificate is automatic and free

### Netlify Forms (Bonus)

Enable serverless form handling:

1. **Update form in index.html**:
   ```html
   <form class="contact-form" id="contactForm" name="contact" method="POST" data-netlify="true">
     <input type="hidden" name="form-name" value="contact">
     <!-- rest of form -->
   </form>
   ```

2. **Deploy**
   - Forms will appear in Netlify dashboard
   - Get email notifications for submissions
   - Spam filtering included

---

## Vercel Deployment

### Method 1: Vercel CLI

1. **Install Vercel CLI**
   ```bash
   npm install -g vercel
   ```

2. **Deploy**
   ```bash
   cd mr-gas-website
   vercel
   ```

3. **Follow Prompts**
   - Login/signup when prompted
   - Accept defaults
   - Site is live instantly!

### Method 2: GitHub Integration

1. **Import Project**
   - Go to https://vercel.com/new
   - Import your GitHub repository

2. **Configure**
   - Framework: None (or Other)
   - Root directory: ./
   - Click "Deploy"

3. **Automatic Deployments**
   - Push to GitHub = automatic deploy
   - Preview deployments for branches

---

## Traditional Hosting (cPanel)

### Requirements
- Web hosting with cPanel access
- FTP credentials
- Domain name

### Steps

1. **Access cPanel**
   - Login to your hosting control panel
   - Usually at: `yourdomain.com/cpanel`

2. **File Manager Method**
   - Open **File Manager**
   - Navigate to `public_html` folder
   - Click **Upload**
   - Upload all files:
     - index.html
     - styles.css
     - script.js
     - logo.svg
   - Verify files are uploaded

3. **FTP Method** (Alternative)
   - Use FTP client (FileZilla, Cyberduck)
   - Connect using your FTP credentials:
     - Host: ftp.yourdomain.com
     - Username: your-username
     - Password: your-password
     - Port: 21
   - Navigate to `public_html`
   - Drag and drop all website files

4. **Verify Deployment**
   - Visit your domain in a browser
   - Check all pages and links work
   - Test on mobile devices

### Setting Up SSL Certificate

1. **In cPanel**
   - Find "SSL/TLS Status"
   - Click "Run AutoSSL"
   - Wait for certificate installation

2. **Force HTTPS** (Recommended)
   - Create/edit `.htaccess` file in public_html:
   ```apache
   RewriteEngine On
   RewriteCond %{HTTPS} off
   RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
   ```

---

## Post-Deployment Tasks

### 1. Verify Website Functionality

- [ ] All pages load correctly
- [ ] Navigation works on mobile
- [ ] Contact form submits properly
- [ ] Phone numbers are clickable
- [ ] Email links open mail client
- [ ] Logo displays correctly
- [ ] Images load (if added)

### 2. Set Up Analytics

**Google Analytics 4**
1. Create account at https://analytics.google.com
2. Get Measurement ID (G-XXXXXXXXXX)
3. Add tracking code to index.html before `</head>`:

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

### 3. Google Search Console

1. Go to https://search.google.com/search-console
2. Add your website
3. Verify ownership (multiple methods available)
4. Submit sitemap (create one at https://www.xml-sitemaps.com/)

### 4. Google My Business

1. Claim/update listing at https://business.google.com
2. Ensure NAP (Name, Address, Phone) matches website
3. Add website URL
4. Upload photos
5. Encourage customer reviews

### 5. Social Media Integration

1. **Facebook**
   - Link to Facebook page from website
   - Add website URL to Facebook business page
   - Create Facebook posts about new website

2. **WhatsApp Business** (Optional)
   - Add WhatsApp click-to-chat button
   - Code to add to contact section:
   ```html
   <a href="https://wa.me/27835316527?text=Hi%20Mr%20Gas" class="btn btn-outline">
     WhatsApp Us
   </a>
   ```

### 6. Performance Testing

Test your site:
- **PageSpeed Insights**: https://pagespeed.web.dev/
- **GTmetrix**: https://gtmetrix.com/
- **Mobile-Friendly Test**: https://search.google.com/test/mobile-friendly

Aim for:
- 90+ Performance score
- < 2 second load time
- Mobile-friendly rating

### 7. Security Checklist

- [ ] HTTPS is enabled (SSL certificate)
- [ ] Force HTTPS redirect working
- [ ] Contact form has spam protection
- [ ] No sensitive data in code
- [ ] Regular backups configured

### 8. Monitoring & Maintenance

**Weekly:**
- Check website loads correctly
- Review form submissions
- Monitor analytics for traffic

**Monthly:**
- Update business hours (if changed)
- Add new testimonials
- Review and respond to reviews
- Check for broken links

**Quarterly:**
- Update content for seasonal offers
- Review SEO performance
- Check competitor websites
- Consider adding blog posts

---

## Troubleshooting

### Website Not Loading

**GitHub Pages:**
- Wait 2-5 minutes after enabling
- Check Settings → Pages for green checkmark
- Verify files are in root directory

**Netlify:**
- Check deploy logs for errors
- Ensure index.html is in root

**cPanel:**
- Verify files are in public_html
- Check file permissions (should be 644)
- Clear browser cache

### Contact Form Not Working

1. Check spam folder for submissions
2. Verify email address in form code
3. Test with different email addresses
4. Consider using Formspree or EmailJS for reliable delivery

### Mobile Menu Not Opening

- Clear browser cache
- Check JavaScript console for errors
- Verify script.js loaded correctly
- Test on different mobile browsers

### Images Not Showing

- Check file paths are correct
- Verify image files uploaded
- Check file extensions match (case-sensitive on Linux)
- Use browser developer tools to see 404 errors

---

## Need Help?

- **GitHub Pages Issues**: https://docs.github.com/pages
- **Netlify Support**: https://answers.netlify.com/
- **Vercel Help**: https://vercel.com/support
- **General Questions**: Open an issue on the GitHub repository

---

## Quick Reference: Deployment Commands

```bash
# GitHub Pages
git add .
git commit -m "Update website"
git push origin main

# Netlify (if using CLI)
netlify deploy --prod

# Vercel
vercel --prod
```

---

**Remember**: After any changes, always test locally before deploying!

Good luck with your deployment! 🚀
