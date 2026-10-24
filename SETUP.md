# Singapore Neurodynamics holding page: Vercel setup

This folder is a plain static site (no build step): `index.html` and `vercel.json`.
Keep this repo to the public website only.

## 1. Create the GitHub repo (Andy, about 2 minutes)

1. Go to https://github.com/new. (Done.)
2. Name: `singaporeneurodynamics-site` (or any name you like). Private is fine; Vercel's free plan deploys private repos.
3. Tick "Add a README" so the repo isn't empty. Click Create.
4. Tell Claude the repo name. Claude attaches it and pushes these files on a branch with a PR.

## 2. Create the Vercel account (Hobby, free)

1. Go to https://vercel.com/signup.
2. Choose **Hobby** ("I'm working on personal projects"), enter your name.
3. Click **Continue with GitHub** and authorise.
4. When asked to install the Vercel GitHub app, choose **Only select repositories** and pick `singaporeneurodynamics-site` only.

Note: Hobby is for non-commercial use under Vercel's terms. A simple holding page is usually fine; once the site is used for business (selling, client work), Vercel expects the Pro plan (about US$20/month).

## 3. Import the project

1. In Vercel: **Add New → Project → Import** `singaporeneurodynamics-site`.
2. Framework preset: **Other**. Leave build command and output directory empty.
3. Click **Deploy**. You get a URL like `singaporeneurodynamics-site.vercel.app`.

## 4. Point your domain at Vercel (if you have one)

1. Vercel project → **Settings → Domains** → add `singaporeneurodynamics.com` (and `www.`).
2. Vercel shows the DNS records to add at your registrar. Typically:
   - apex `@`: **A** record → `76.76.21.21`
   - `www`: **CNAME** → `cname.vercel-dns.com`
   (Use whatever values Vercel shows you; they are authoritative.)
3. Keep existing **MX** records untouched so email keeps working.
4. HTTPS certificates are issued automatically once DNS resolves (minutes to a few hours).

### Second domain as a redirect (neurodynamics.sg)

1. Add `neurodynamics.sg` and `www.neurodynamics.sg` in the same Vercel project's Domains page.
2. For each, choose **Redirect to** `singaporeneurodynamics.com` (308 permanent).
3. At GoDaddy, add the same A and CNAME records for neurodynamics.sg as above.
4. .sg registrations need a Singapore presence (SGNIC rules) and the registrant must be verified after purchase, so watch for a verification email and complete it promptly or the domain can be suspended.

## 5. How Claude develops on it afterwards

- The repo is connected to Vercel, so every push to `main` deploys production, and every pull request gets its own **preview URL** (Vercel posts it on the PR).
- Workflow: you ask in this project, Claude works on a branch, opens a PR, you check the preview link, and you merge. Merging is the go-live step, so nothing goes public without you.
- Later, if the site grows (contact form, blog, app), Claude can switch it to Next.js or similar in the same repo; Vercel picks that up automatically.
- Optional: a Vercel access token would let Claude query deploy status directly. It isn't needed; the GitHub integration covers everything above.

## Placeholders to confirm in index.html

- Tagline: set (image solutions, AI, calibrated probabilities)
- Contact email: andywhittaker@gmail.com (confirmed; swap for a domain address later)
- Domain (for step 4)
