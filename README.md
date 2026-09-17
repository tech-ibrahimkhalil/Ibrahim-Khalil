# Ibrahim Portfolio — README

A single self-contained HTML file (`Ibrahim Portfolio V2.6.html`) that serves as the personal portfolio site for **MD. Ibrahim Khalil**, Industrial Automation Specialist / Certified BMS Programmer / SCADA Engineer.

No build step, no dependencies, no external frameworks — open the file directly in any modern browser and it works, online or offline.

---

## 1. What's inside the file

Everything lives in one `.html` file:

- **`<style>`** — all CSS (neumorphic light/dark theme, layout, responsive rules)
- **`<body>`** — all page markup
- **`<script>`** — all JavaScript (no external libraries, no build tools)

The only external network calls are to Google Fonts (`Plus Jakarta Sans`, `JetBrains Mono`). Everything else, including the profile photo, is embedded inline.

## 2. Sections

| Section | ID | What it does |
|---|---|---|
| Sidebar | `#sidebar` | Profile photo, contact info, nav links, dark/light theme toggle. Auto-hidden off-canvas drawer on every screen size — opened with the edge tab, closed by re-pressing it, clicking the backdrop, choosing a nav link, or pressing Escape. |
| Hero | — | Name, tagline, intro copy, CTA buttons, skill chips |
| Metrics | — | Animated count-up stats, triggered when scrolled into view |
| About | `#about` | Education timeline + certifications list |
| Competencies | `#competencies` | Grid of skill-matrix cards (Siemens automation, multi-vendor integration, protocols, BMS/HVAC, motion & robotics, data & software, instrumentation & calibration, protocol converters, solar + SCADA, AI-based automation) |
| Projects | `#projects` | Filterable grid (All / Siemens & SCADA / BMS & HVAC / Motion & Robotics / IIoT & Data) with modal popups showing Objective → Architecture → Hardware & Protocols → Control Logic → Results |
| Code Lab | `#codelab` | Tabbed, syntax-highlighted code snippets (Python PLC polling, Delta Controls GCL+, SQL shift report, Structured Text interlocks) |
| Field Tool | `#calculator` | Three interactive engineering tools (see §3) |
| Downloads | `#downloads` | Download cards for CV / topology drawing / shift report template |
| Contact | `#contact` | Contact card with email & phone |
| Social | `#social` | Social/channel links |
| Footer | — | Social icon row + copyright |

## 3. Interactive field tools

All three live under **Field Tool** and are pure vanilla JS — no external charting library.

1. **4–20 mA → PV & PLC scaling calculator** — live conversion from loop current to an engineering value and PLC raw count.
2. **PID loop simulator** — discrete PID controller (Kp, Ki, Kd) driving a first-order process; redraws an SVG step-response chart on every input change, with settled value, overshoot %, and settling time readouts.
3. **Water tank level control simulator** — an animated SVG tank with an inlet valve and a gravity discharge. Switch between:
   - **Auto (PID)** — the inflow valve is driven by a PID loop holding a setpoint level
   - **Manual** — you set a fixed inflow valve position directly
   A live trend chart plots level, setpoint, and valve output over time.

## 4. Customizing content

Everything is plain HTML/CSS/JS — search for these markers to make common edits:

- **Personal details / contact info** — in the sidebar and hero markup near the top of `<body>`.
- **Profile photo** — embedded as a base64 `data:image/jpeg;base64,...` string inside `.profile-photo-img`. To replace it, re-encode a new image and swap the string (or ask for it to be swapped).
- **Projects** — defined as a JS array (`var projects = [...]`) near the bottom `<script>`. Each entry has `category`, `tag`, `name`, `org`, `summary`, `specs`, and the five modal fields (`objective`, `architecture`, `hardware`, `logic`, `results`). Add a new object to add a new project card automatically.
- **Competency cards** — plain HTML blocks inside `#competencies` (`.matrix-card`). Copy an existing card to add a new one.
- **Download links** — inside `#downloads`, each card has an `<!-- PLACEHOLDER -->` comment and an `href="#"` — point it at your actual file.
- **Image placeholders** — anywhere an image is expected but not yet supplied, look for `<!-- PLACEHOLDER: ... -->` comments with an example `<img>` tag to drop in.

## 5. Theme & responsiveness

- Light/dark mode toggle in the sidebar, persisted via `localStorage`, and respects the OS preference on first load.
- Fully responsive from mobile to desktop; the sidebar behaves identically (auto-hidden drawer) at every breakpoint.
- No JavaScript framework — counters, filters, modals, tabs, calculators, and the tank simulator are all implemented with plain DOM APIs.

## 6. Versioning

Each round of updates ships as a new file named `Ibrahim Portfolio Vx.y.html`, with the minor version incremented per change (e.g. V2.5 → V2.6). Keep only the latest version unless you want a change history.

## 7. Browser support

Built with standard HTML5/CSS3/ES6 — works in all current versions of Chrome, Edge, Firefox, and Safari. No polyfills included; very old browsers (IE11 and earlier) are not supported.
