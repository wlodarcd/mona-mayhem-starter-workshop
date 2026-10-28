# GitHub Copilot instructions for Mona Mayhem starter workshop

## Project context

This repository is a minimal Astro-based workshop starter for a GitHub contribution comparison app. The code is intentionally small and meant to be extended during the workshop. Most of the work happens under `src/pages`, with one landing page and one API route stub.

## Commands

Install dependencies:

```bash
npm install
```

Start the local dev server:

```bash
npm run dev
```

Create a production build:

```bash
npm run build
```

Preview the production build locally:

```bash
npm run preview
```

There are no dedicated test or lint scripts configured in `package.json`, so there is no single-test command in this repo today. When validating changes, prefer a focused `npm run build` check because it catches Astro/TypeScript integration issues without requiring a full custom harness.

## High-level architecture

- `astro.config.mjs` configures the Astro app with server output and the Node standalone adapter (`@astrojs/node`). This is a server app, not a static site, unless the workshop explicitly tells you to switch deployment modes.
- `src/pages/index.astro` is the root page. It is currently a minimal landing page and is the place to add the UI for the contribution comparison experience.
- `src/pages/api/contributions/[username].ts` is the API endpoint for fetching GitHub contribution data for a given username. It is intentionally a stub and currently returns a `501` JSON error response.
- `public/` is reserved for static assets such as icons or images.
- The app is intentionally a workshop skeleton: keep the project lean, file-based, and easy to understand. Avoid introducing large frameworks or architecture changes unless the task specifically requires them.

## Key conventions

- Use Astro file-based routing: pages go in `src/pages`, and route names match the file structure.
- Dynamic API routes use the `params` object and should return a `Response` with JSON content and an explicit `Content-Type` header.
- Server routes in this repository are explicitly non-prerendered (`export const prerender = false`), so code must be safe for server execution.
- The project is mostly documented and described in Polish; preserve the repository’s established tone in UI text and comments unless a task explicitly calls for English wording.
- Keep changes aligned with the workshop’s starter scope: small, focused, and in the same Astro conventions already used by the project.
- The README documents the expected Node version and deployment notes. When working on the app’s behavior, check that guidance before changing server/static output or deployment assumptions.
