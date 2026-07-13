# HANAN TRADE Monitor

**Real-time global intelligence dashboard** — AI-powered news aggregation, geopolitical monitoring, market tracking, and infrastructure intelligence in a single situational-awareness interface.

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=flat&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![YouTube](https://img.shields.io/badge/YouTube-HANAN%20TRADE-FF0000?style=flat&logo=youtube&logoColor=white)](https://www.youtube.com/@HANANTRADE)

> Customized build of the open-source [World Monitor](https://github.com/koala73/worldmonitor) project (AGPL-3.0), rebranded and streamlined for **HANAN TRADE**.
> Follow on YouTube: **[youtube.com/@HANANTRADE](https://www.youtube.com/@HANANTRADE)**

---

## What It Does

- **500+ curated news feeds** across 15 categories, AI-synthesized into daily briefs
- **Dual map engine** — interactive 3D globe (globe.gl) and WebGL flat map (deck.gl) with 56 map layer types (conflicts, military bases, pipelines, undersea cables, ports, and more)
- **Cross-stream correlation** — military, economic, disaster, and escalation signals converged into a single alert view
- **Country Instability Index (CII)** — stress scoring for 31 Tier-1 countries with trend tracking
- **Finance radar** — 29 stock exchanges, commodities, forex, crypto, and a 7-signal market composite
- **Trade & supply chain intelligence** — trade routes, chokepoints, commodity flows, and shipping (AIS) tracking
- **Local AI support** — run summarization fully offline with Ollama; no API keys required for core features
- **6 site variants** from one codebase: World, Tech, Finance, Commodity, Energy, and Good News
- **Native desktop app** (Tauri 2) for Windows, macOS, and Linux
- **25 languages** with native-language feeds and RTL support

### HANAN TRADE customizations

This build differs from upstream World Monitor:

- Rebranded UI: header, footer, browser title, meta tags, and settings all read **HANAN TRADE Monitor**
- Community links point to the **[HANAN TRADE YouTube channel](https://www.youtube.com/@HANANTRADE)** instead of Discord
- Pro/paywall surfaces removed: no upgrade banners, no locked "Sign in to unlock" panels, no API-Keys settings tab, no sign-in buttons
- Footer/header external links and personal credits removed for a cleaner interface

---

## Support Status

| Surface | Status | Notes |
|---------|--------|-------|
| Local development (`npm run dev`) | Supported | Primary way to run this build |
| Self-hosted deployment (Vercel / Docker / static) | Supported | See `SELF_HOSTING.md` in this repo |
| Desktop binaries (Tauri 2) | Buildable | `npm run desktop:build:full` — not distributed as releases here |
| Upstream public deployments (`worldmonitor.app` and variants) | Not this repo | Operated by the upstream project |

This is a personal customized build maintained by HANAN TRADE. For upstream fixes and new features, see the [original project](https://github.com/koala73/worldmonitor).

---

## Quick Start

```bash
git clone https://github.com/thehananasif/HANAN-TRADE-Monitor.git
cd HANAN-TRADE-Monitor
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000). The app runs with **no environment variables** — feature-specific data sources may require credentials (see `.env.example` for the full list; override the dev port with `DEV_PORT` in `.env.local`).

For variant-specific development:

```bash
npm run dev:tech       # Tech industry dashboard
npm run dev:finance    # Markets & trading dashboard
npm run dev:commodity  # Commodity & supply chain dashboard
npm run dev:energy     # Energy infrastructure atlas
npm run dev:happy      # Good-news dashboard
```

Useful checks:

```bash
npm run typecheck      # TypeScript type checking
npm run build:full     # Production build (full variant)
```

---

## Tech Stack

| Category | Technologies |
|----------|-------------|
| **Frontend** | Vanilla TypeScript, Vite, globe.gl + Three.js, deck.gl + MapLibre GL |
| **Desktop** | Tauri 2 (Rust) with a Node.js sidecar |
| **AI/ML** | Ollama / Groq / OpenRouter for summarization, Transformers.js (in-browser ML) |
| **API contracts** | Protocol Buffers (281 protos, 35 services) with sebuf HTTP annotations |
| **Backend/Serverless** | Vercel Edge Functions (60+), Railway relay, Convex |
| **Caching** | Redis (Upstash), 3-tier cache, CDN, service worker (PWA) |
| **Testing** | Playwright (E2E + visual regression), Vitest, node:test |
| **Linting** | Biome, markdownlint, custom architecture guardrail scripts |

---

## Programmatic Access

The codebase ships agent- and script-friendly interfaces alongside the browser UI:

- **MCP server** — Model Context Protocol server code included; the upstream public endpoint is `https://worldmonitor.app/mcp` (Streamable HTTP)
- **REST API** — OpenAPI 3 spec in [`docs/api/`](docs/api/), served at `/openapi.yaml` on any deployment
- **CLI** — a command-line client in [`cli/`](cli/):

  ```sh
  npx worldmonitor tools    # list every MCP tool (no key needed)
  ```

- **SDKs** — zero-dependency client libraries in [`sdk/`](sdk/) for **Python**, **Ruby**, and **Go**

Note: the hosted API endpoints above are operated by the upstream World Monitor project. If you self-host this build, point clients at your own deployment.

---

## Flight Data

Flight data provided graciously by [Wingbits](https://wingbits.com), the most advanced ADS-B flight data solution.

---

## Data Sources

Aggregates **65+ external providers and APIs** across:

- **Geopolitics** — GDELT, ACLED-style event feeds, protest & conflict trackers
- **Finance** — stock exchanges, commodities, forex, crypto markets, prediction markets
- **Energy** — pipelines, LNG terminals, storage, chokepoint flows, fuel prices
- **Climate & disasters** — earthquakes (USGS), wildfires (NASA FIRMS), storms, power outages
- **Aviation & maritime** — ADS-B flight tracking (Wingbits), AIS ship positions, port activity
- **Cyber & military** — threat intelligence feeds, military bases, exercises, sirens
- **News** — 500+ curated RSS feeds in 25 languages across 15 categories

All source lists live in [`src/config/feeds.ts`](src/config/feeds.ts) and the [`data/`](data/) directory, with a freshness monitor covering 35 source groups.

---

## License

**AGPL-3.0-only** — same license as the upstream project this build derives from.

| Use Case | Allowed? |
|----------|----------|
| Personal / research / educational | Yes, under AGPL-3.0-only |
| Self-hosted instance | Yes, under AGPL-3.0-only |
| Fork and modify | Yes — share source under AGPL-3.0-only when required |
| Commercial use / SaaS | Yes, when you comply with AGPL copyleft and source-availability terms |

See [LICENSE](LICENSE) for the full text.

- Original work: Copyright (C) 2024–2026 [Elie Habib](https://github.com/koala73) — [World Monitor](https://github.com/koala73/worldmonitor)
- Modifications: Copyright (C) 2026 HANAN TRADE — [youtube.com/@HANANTRADE](https://www.youtube.com/@HANANTRADE)

---

<p align="center">
  <strong>HANAN TRADE Monitor</strong> &nbsp;·&nbsp;
  <a href="https://www.youtube.com/@HANANTRADE">YouTube: @HANANTRADE</a>
</p>
