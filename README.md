# Personal Portfolio — María Gálvez

🔗 **Live site:** <https://xmariia55x.github.io/portfolio/>

A small, static personal portfolio and CV website. It presents an overview of who
I am, my professional experience, skills, projects, and education, with a single-page
layout, smooth in-page navigation, and a mobile-friendly responsive design.

The site is built with plain HTML, CSS, and a tiny bit of vanilla JavaScript — no
framework, no build step. It's deployed automatically to GitHub Pages on every push
to `main`.

## Tech stack

- **HTML5** — single-page layout ([index.html](index.html))
- **CSS3** — custom styles, no framework ([styles.css](styles.css))
- **Vanilla JavaScript** — mobile nav toggle and scroll-based active link ([main.js](main.js))
- **Docker + nginx** — for serving the site locally
- **GitHub Actions** — automatic deploy to GitHub Pages

## Project structure

```
.
├── index.html        # Page content and structure
├── styles.css        # All styling
├── main.js           # Mobile nav + active-link-on-scroll
├── assets/           # Images and CV (profile picture, cv.pdf, ...)
├── Dockerfile        # nginx:alpine image serving the static files
├── docker-compose.yml
└── .github/workflows/deploy.yml   # GitHub Pages deployment
```

## Running it locally

Because it's a fully static site, you have a few options.

### Option 1 — Docker (recommended)

Mirrors how the site is served in production (nginx). From the project root:

```bash
docker compose up
```

Then open <http://localhost:8080>.

The container mounts the project directory read-only, so edits to `index.html`,
`styles.css`, or `main.js` show up on refresh — no rebuild needed.

To stop it:

```bash
docker compose down
```

### Option 2 — Any static file server

No Docker required. From the project root, pick whichever you have installed:

```bash
# Python 3
python3 -m http.server 8080

# Node.js
npx serve .
```

Then open <http://localhost:8080>.

### Option 3 — Open the file directly

You can also just open `index.html` in your browser. Everything works except
features that rely on a server context; for this project that's fine, but Options 1
or 2 are closer to the real thing.

## Deployment

Deployment is fully automated. Every push to the `main` branch triggers the
[GitHub Actions workflow](.github/workflows/deploy.yml), which publishes the site to
GitHub Pages at <https://xmariia55x.github.io/portfolio/>. There's no build step — the
repository contents are uploaded as-is.
