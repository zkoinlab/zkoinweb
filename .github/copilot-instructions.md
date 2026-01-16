# Copilot Instructions for zen koin lab Web Presence

## Project Overview

**zen koin lab** is a deep-technology research organization focused on privacy-enhanced cryptographic infrastructure and AI integration for decentralized systems. This repository contains the public web presence, consisting primarily of static HTML pages that serve as landing pages and information hubs.

### Architecture

- **Root Landing Page** ([index.html](index.html)): Main organizational website featuring mission, vision, values, and contact information. Built with vanilla HTML/CSS/JavaScript with a responsive sidebar navigation.
- **16 Words of Web3** ([16words-of-web3/index.html](16words-of-web3/index.html)): Comprehensive guide exported from Notion as a static HTML document (~723 lines). Serves as a resource hub with styling for print and screen rendering.
- **16 Words Embed** ([16words/index.html](16words/index.html)): Simple iframe redirecting to Notion document.

## Core Patterns & Conventions

### Frontend Architecture
- **No build system**: Pure static HTML/CSS/JavaScript - all files are self-contained
- **Single-page navigation**: Uses anchor links (`#section-id`) with vanilla JavaScript scroll handling
- **Responsive design**: Mobile-first breakpoint at 768px (`@media (max-width: 768px)`)
- **Styling approach**: Inline `<style>` tags in HTML; no separate CSS files

### Navigation & Interaction

Key JavaScript patterns in [index.html](index.html#L413):
1. **Menu Toggle** (`toggleMenu()` / `closeMenuOnMobile()`): Sidebar navigation visibility on mobile devices
2. **Active Link Highlighting**: Scroll event listener updates `.active` class on nav items based on viewport position
3. **Smooth Scrolling**: Intercepts internal anchor links to use `scrollIntoView({ behavior: 'smooth' })`
4. **External Link Handling**: Preserves default behavior for HTTP/HTTPS links (opens in new tabs with `target="_blank"`)

### Design System
- **Color Palette**: Primary dark blue `#0e2439`, light cream background `#fbf9ed`
- **Sidebar**: Fixed 250px width, dark blue background, left-aligned on desktop (hidden/togglable on mobile)
- **Transitions**: Smooth 0.3s ease for all interactive elements
- **Typography**: Segoe UI / system fonts, line-height 1.6

## Critical Content Structure

### 16 Words of Web3 Document
The [16words-of-web3/index.html](16words-of-web3/index.html) is auto-exported from Notion and serves as:
- Complete reference guide with extensive styling for multi-format rendering
- Includes CSS rules for print (`@page`, `@media only print`)
- Image optimization (`max-width: 100%`)
- Nested styling for tables, lists, and figures

**Important**: Treat this file as read-only unless re-exporting from Notion. Direct edits may be overwritten.

### Navigation Structure
Main menu items (from [index.html](index.html#L266)):
1. Introduction
2. Mission
3. Vision
4. Values
5. Strategic Focus
6. 16words-of-web3 (external Notion link)
7. Contact Us

## Development Notes

### Deployment
- **Platform**: Cloudflare Pages - serves static HTML files directly
- **Build**: No build step required; files are deployed as-is
- **Caching**: Leverage Cloudflare's global CDN caching for static assets
- **Deployment Flow**: Push changes to repository → Cloudflare automatically detects and deploys

### Mobile Responsiveness
- Sidebar transforms off-screen and toggles on mobile (768px breakpoint)
- Menu toggle button appears only on mobile
- All sections adapt to 100% width with reduced padding (10px)

### Link Handling
- Internal navigation: Uses smooth scroll with scroll-spy active state
- External links: Opens in new tabs with `rel="noopener noreferrer"` security attributes
- Notion link in navigation: Primary resource for "16words-of-web3" content

### Assets
- Logo: [logo.png](logo.png) - Referenced in both sidebar and header
- Images: Directory [16words-of-web3/](16words-of-web3/) contains numbered image assets (image 1.png through image 21.png)

## When Modifying

### Main Landing Page
- Update `<title>`, meta descriptions in `<head>` for SEO
- Modify section `id` attributes consistently across navigation links and scroll-spy logic
- Ensure color/spacing changes apply to both sidebar and mobile menu toggle

### Adding New Sections
1. Create `<section id="section-name">` in main content
2. Add `<li><a href="#section-name">Section Name</a></li>` to nav menu
3. Scroll-spy automatically handles highlighting if structure is consistent

### Notion Content Updates
- Re-export [16words-of-web3/index.html](16words-of-web3/index.html) from Notion when content changes
- Preserve existing styling classes and structure
- Ensure image paths relative to the HTML file location
