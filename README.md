# Pour — Marketing & Legal Site

Static, no-build site for **Pour** — a private journal for the drinks you love (beer, cocktails, wine, **and non-alcoholic**). Plain HTML/CSS/JS; every page is one self-contained file. Deploy to Netlify as-is.

## Files
| File | Purpose |
|---|---|
| `index.html` | Landing page |
| `about.html` | Founder story |
| `support.html` | Support / FAQ (Apple-required support URL) |
| `privacy.html` | Privacy Policy |
| `terms.html` | Terms of Service / EULA |
| `404.html` | Branded not-found page (Netlify serves it automatically) |
| `favicon.svg` | Site icon (on-brand amber dot) |
| `robots.txt` · `sitemap.xml` | SEO / crawler basics |
| `netlify.toml` | Security headers + caching |
| `_redirects` | Clean URLs (`/privacy` → `/privacy.html`) |

## Deploy to Netlify
Drag the `pour-site` folder into Netlify, or connect a repo with **Build command:** *(blank)* and **Publish directory:** `.`. No npm, no framework, no build step. `netlify.toml` + `_redirects` are picked up automatically.

---

## 🔍 Audit pass (done — 2026)
A full pass added/fixed:
- **Robustness:** `<noscript>` fallback so the landing page isn't blank with JS off; Apple-logo SVG in the store badges.
- **Accessibility:** darker `--muted` for WCAG contrast, `:focus-visible` keyboard outlines, a **skip-to-content** link + `<main id="main">` landmark on every page, `aria-expanded`/`aria-controls` on the mobile menu.
- **SEO:** favicon, per-page `canonical`, `author`/`color-scheme` meta, Twitter Card + JSON-LD (`MobileApplication`) on the landing page, `robots.txt`, `sitemap.xml`.
- **Infra:** `netlify.toml` security headers (CSP, X-Frame-Options, Referrer-Policy, Permissions-Policy), `_redirects` clean URLs, branded `404.html`.

> ⚠️ **NEW must-do — set your real domain.** `https://example.com` is now used in several SEO files. Find-replace it everywhere once you have the domain:
> `grep -rl "example.com" .` → `index.html`, `about/support/privacy/terms.html` (canonical/OG), `robots.txt`, `sitemap.xml`.

---

## ✅ Already filled in (draft values — review & change if needed)
These were placeholders; I filled them with reasonable drafts so the site reads as finished. **Confirm each one:**

- **Name / entity:** `Noah Mehrle` (footers + legal). → If you launch under an LLC or different legal entity, change it.
- **Contact email:** `noah.mehrle2@gmail.com` (support + legal + mailto links). → ⚠️ This is your personal Gmail and will be public/scrapeable. Strongly consider a dedicated address (e.g. `hello@yourdomain`) and find-replace it.
- **Effective / updated date:** `June 1, 2026` (privacy + terms). → Set to your real launch date.
- **Governing law / venue:** `Ohio` (terms). → Confirm this is your state.
- **Lifetime Pro price:** `$9.99` (pricing card). → This is a *suggestion*. Set your real price.
- **Founder story** (`about.html`): a complete first-person draft in your voice. → Read it and make it actually yours; tweak any detail that isn't true.
- **NA / drinks framing:** copy across all pages now says "drinks" and explicitly includes non-alcoholic, with beer still front-and-center.

## 🔧 Still need you before launch

**Must do:**
- [ ] **App Store links** — every store badge / "Get Pour" button is `href="#"`. Replace with your real listing URL. *(index ×3, about ×1, plus the pricing button.)* Grep: `grep -rn 'href="#"' *.html`
- [ ] **Screenshots** — replace the placeholder gradient boxes (search `TODO` / `[ Screenshot` in `index.html`): hero phone (`.screenshot` block → `<img>`), and the 3 feature tiles. Drop images in a `screenshots/` folder.
- [ ] **OG tags** (`index.html`) — set `og:url` and a real `og:image` (currently `https://example.com/...`).
- [ ] **Terms: have counsel review** — see the note at the top of `terms.html` (warranty / liability / governing law / arbitration decision).

**Verify these statements I wrote match your shipped app** (I inferred them from the codebase — confirm before relying on them):
- [ ] *privacy:* "We rely on Apple's built-in App Analytics and crash reporting and do not use third-party advertising or analytics SDKs." → true only if you haven't added Sentry/Firebase/etc.
- [ ] *privacy + support:* account/data deletion path is **Profile → Settings → Delete Account**. → Confirm that's the real in-app path (Apple requires a deletion path for account-based apps).
- [ ] *support:* restore path is **Profile → Restore Purchases**. → Confirm the real location.
- [ ] *privacy:* synced data = "pours, photos, profile, companions, location pins"; "exact coordinates are coarsened before shown to others"; "AI provider does not use recap data to train models." → Confirm each matches reality + your Anthropic/Supabase agreements.
- [ ] *privacy:* age gate "blocks anyone under 21." → Confirm your DOB gate.

## Screenshots (index.html)
Search `TODO` in `index.html`:
1. **Hero phone** — `.screenshot` block inside `.screen` → swap for `<img src="screenshots/home.png" alt="Pour home screen">`.
2. **Logging a drink** — `.tile` (Feature 1).
3. **Your map** — `.tile.map` (Feature 2).
4. **A saved memory** — `.tile` (Feature 3).

Tip: include at least one **non-alcoholic** example in your screenshots so the NA positioning shows visually (the hero mock already lists an Athletic N/A pour).

## Design notes
- Palette lives in the `:root` of each file (warm paper `#FAF8F4`, copper accent `#B96E2C`). Duplicated per file (no shared CSS) — keep in sync if you retune.
- Motion (scroll-reveal + hero parallax) auto-disables under `prefers-reduced-motion`.
- Responsive; nav collapses to a "Menu" toggle under 720px.

## Pre-launch checklist
- [ ] App Store links real · screenshots in · OG image set
- [ ] Email swapped to a dedicated address (recommended)
- [ ] Price + governing state + founder story confirmed
- [ ] Privacy statements verified against the shipped app
- [ ] Terms reviewed by counsel
- [ ] Tested on real iOS Safari + desktop
