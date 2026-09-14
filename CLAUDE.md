# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal portfolio website for Max, a Senior AI & Full Stack Developer. Static single-page application built with vanilla HTML5, CSS3, and JavaScript featuring responsive design with sections for About, Resume, Projects, and Contact.

## Project Structure

```
/
├── index.html           # Main HTML file containing all page sections
├── assets/
│   ├── css/
│   │   └── style.css    # Main stylesheet with CSS custom properties
│   ├── js/
│   │   └── script.js    # Client-side interactivity and form handling
│   └── images/          # Portfolio images, icons, and avatars
```

## Architecture

### Single-Page Application Structure

The entire application is in `index.html`. The page uses a tab-based navigation system where:
- All sections (About, Resume, Projects, Contact) are present in the DOM simultaneously
- Navigation toggles `.active` class on sections via `data-nav-link` and `data-page` attributes
- JavaScript in `assets/js/script.js` manages visibility and transitions

### Key Data Attributes

| Attribute | Purpose |
|-----------|---------|
| `data-sidebar` / `data-sidebar-btn` | Sidebar toggle (mobile) |
| `data-page` | Identifies page sections (about, resume, projects, contact) |
| `data-nav-link` | Navigation buttons that switch pages |
| `data-filter-item` / `data-category` | Project filtering system |
| `data-filter-btn` / `data-select-item` | Filter controls (desktop buttons / mobile dropdown) |
| `data-form` / `data-form-input` / `data-form-btn` | Contact form validation |

### Navigation System

Page navigation (`assets/js/script.js:136-155`) matches navigation button text with `data-page` attributes:
- Button text in navbar must match exactly (case-insensitive) with corresponding article's `data-page` value
- Always add/remove the `active` class to both the navigation link and the page

### Project Filtering

Filter categories: "web development", "applications", "web design"

Each project item requires:
- `data-filter-item` attribute on the `<li>` element
- `data-category` attribute matching one of the categories above

## Development Workflow

### No Build Process

Static site with no build step, bundler, or package manager. All files are served directly.

### Local Development

```bash
# Python 3
python -m http.server 8000

# Node.js
npx http-server
```

Navigate to `http://localhost:8000`

## External Dependencies (CDN-hosted)

1. **Google Fonts**: Poppins font family
2. **Ionicons 5.5.2**: Icon library
3. **jQuery 1.8.3**: Used for Google Maps integration
4. **Google Maps JavaScript API**: Map display on contact page
5. **EmailJS**: Contact form email service

## Implementation Details

### Contact Form (EmailJS)

- Service ID: `service_lcsy86w`
- Template ID: `template_bqjxq9e`
- Public Key: `aS1yx_eVEJZ79IYYF`
- Form validation enables/disables submit button dynamically via `data-form-input` event listeners

### Google Maps

- API Key: `AIzaSyCjAk1CI42wcBeAzmwE8knNNj0WTG3-M8U`
- Default location: Scarborough, Ontario, Canada (43.7950, -79.2661)
- Initialized via async `initMap()` function called by Google Maps callback

## Styling Conventions

CSS in `assets/css/style.css`:
- CSS custom properties (variables) defined in `:root` for theming (colors, typography, shadows, transitions)
- Mobile-first responsive design with media queries for larger breakpoints
- BEM-like naming (`.service-item`, `.timeline-list`, `.filter-select-box`)
