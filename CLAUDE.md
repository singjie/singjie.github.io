# CLAUDE.md

## Project Overview

This is a **personal portfolio website** for Lee Sing Jie, a Software Engineer from Singapore. The site is hosted on GitHub Pages at [singjie.com](https://singjie.com) (also accessible via singjie.github.io).

The entire site is a single-page static website with no build process, no external dependencies, and no JavaScript frameworks.

## Repository Structure

```
singjie.github.io/
├── CNAME            # Custom domain config (singjie.com)
├── _config.yml      # Jekyll config (theme: jekyll-theme-slate)
├── favicon.png      # Site favicon (16x16 PNG)
├── index.html       # Complete single-page site (~590 lines)
├── robots.txt       # Crawler configuration
└── sitemap.xml      # XML sitemap for SEO
```

There are no subdirectories, build folders, or dependency files. All HTML, CSS, and JavaScript live in `index.html`.

## Architecture

- **Framework:** Jekyll (GitHub Pages default), using `jekyll-theme-slate` theme declaration in `_config.yml`. In practice the site is fully self-contained static HTML.
- **Styling:** Embedded CSS using custom properties (`--color-bg`, `--color-accent`, etc.), Flexbox, CSS Grid, and media queries for responsive design.
- **JavaScript:** Minimal vanilla JS for mobile hamburger menu toggle. No frameworks or libraries.
- **Assets:** Inline SVG icons for social links. Favicon is the only external asset file.

## Page Sections (in order)

1. **Navigation** - Fixed top bar with hamburger menu on mobile
2. **Hero** - Name, tagline, social media links (GitHub, Twitter, Facebook, YouTube, Photos)
3. **About** - Interest/skill tags
4. **Education** - NUS, University of Oulu (Finland), Ngee Ann Polytechnic
5. **Projects** - Work projects (BeeTalk, Garena Live, Garena+) and personal projects
6. **Baking** - Recipe cards with external links
7. **Contact** - Email link
8. **Footer** - Copyright

## Development Workflow

### Local Development

No build step is required. Open `index.html` directly in a browser or use any local HTTP server:

```bash
# Python
python3 -m http.server 8000

# Node.js (if npx available)
npx serve .
```

### Deployment

- Push to the `master` branch triggers GitHub Pages deployment automatically.
- No CI/CD pipelines or GitHub Actions are configured.
- The CNAME file maps the site to `singjie.com`.

### Git Conventions

- The primary branch is `master`.
- Feature branches use the pattern `claude/<description>-<id>` for AI-assisted changes.

## Key Conventions

- **Single-file architecture:** All content, styles, and scripts are in `index.html`. Do not split into separate CSS/JS files without explicit instruction.
- **No external dependencies:** Do not introduce package.json, npm modules, or CDN-hosted libraries.
- **Inline SVGs:** Social media icons are inline SVG elements, not image files or icon fonts.
- **CSS custom properties:** Use existing CSS variables for colors and theming rather than hardcoded values.
- **Mobile-first responsive:** All layout changes must work across desktop and mobile. The breakpoint is at `600px`.
- **Semantic HTML:** Sections use `<section id="...">` with matching navigation anchors.

## Common Tasks

### Adding a new project

Add a new `<a>` element inside the appropriate `.project-list` div in the Projects section of `index.html`.

### Adding a new section

1. Add a nav link in the `<nav>` element
2. Add a `<section id="section-name">` block in the appropriate position
3. Style with existing CSS patterns or add rules in the `<style>` block

### Updating content

Edit the relevant section directly in `index.html`. All text content is plain HTML.

## Testing

There is no automated testing. Verify changes by:

1. Opening `index.html` in a browser
2. Checking both desktop and mobile viewports (responsive breakpoint at 600px)
3. Verifying all navigation anchor links scroll to the correct section
4. Confirming external links open correctly
