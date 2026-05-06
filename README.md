# kickoffsa.com

Static micro-site for **Kickoff** — amateur football tournaments in Riyadh.

Two pages: a single-screen landing (`index.html`) and two legal pages (`privacy.html`, `terms.html`). Pretty URLs (`/privacy`, `/terms`) handled via Cloudflare Pages `_redirects`.

## Deploy (push to GitHub, connect Cloudflare Pages)

1. **Create a GitHub repo** (e.g. `kickoffsa/site`) on github.com — empty, no README.
2. **Push this directory** to it:
   ```bash
   git remote add origin git@github.com:<your-org>/<your-repo>.git
   git branch -M main
   git push -u origin main
   ```
3. **Connect Cloudflare Pages**:
   - Go to <https://dash.cloudflare.com/> → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
   - Select the GitHub repo.
   - **Build settings:** framework preset = *None*, build command = *(blank)*, build output directory = `/` (or the subfolder if this directory is nested).
   - Deploy.
4. **Custom domain:** in the Pages project → **Custom domains** → add `kickoffsa.com` and `www.kickoffsa.com`. Cloudflare will provision the DNS records automatically if the domain is on your Cloudflare account.

The `_redirects` file rewrites `/privacy` → `/privacy.html` and `/terms` → `/terms.html` with a 200 (no client redirect, clean URLs).

## TODOs before launch

- Swap placeholder legal copy in `privacy.html` / `terms.html` for the rendered markdown from `legal/privacy-policy.md` and `legal/terms-of-service.md`.
- Replace the placeholder App Store CTA in `index.html` with the official Apple-provided App Store badge SVG and real App Store URL.
- Set the `Last updated:` date on both legal pages.
