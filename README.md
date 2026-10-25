# SAHAYAK GRID — Offline-first prototype

A black-and-purple, responsive field coordination dashboard for a **fictional emergency scenario**.

## Features in this prototype
- **Offline shell:** service worker caches the interface after first load (serve over localhost/HTTPS; `file://` does not enable service workers).
- **Local incident reports:** create reports with type, source, location, confidence, details and timestamp. They persist in `localStorage` and add an item to the pending queue.
- **Medical triage:** simulated cases include vitals and clinician-assigned urgency. “Simulate vital change” and each row action change urgency and reorder the queue.
- **Fictional hazard map:** roads, a reported blockage, a medical point, safe zone, recommended route, and an unverified route. This is illustrative SVG, not real navigation.
- **Trust-aware reports:** source, confidence, age and potentially stale labels are visible. Report age is recalculated on refresh.
- **Conflict review:** demo conflict keeps both source versions for review instead of silently overwriting them.
- **Sync simulation:** the ⇄ button toggles online/offline display. This is not a real multi-device network; when toggled online, the app can mark queued demo updates as synced only through the sync control logic if expanded later.

## Run locally
Use a local server, for example:
```bash
python -m http.server 8000
```
Open `http://localhost:8000`. After first load, refresh once so the service worker can cache the shell.

## Deploy on GitHub Pages
1. Create a GitHub repository named `sahayak-grid`.
2. Upload `index.html`, `styles.css`, `app.js`, `manifest.json`, `sw.js`, and this README to the repository root.
3. In **Settings → Pages**, deploy from the `main` branch and `/ (root)`.
4. Open the Pages URL online once before testing offline mode.

## Important limitations
This is a front-end demonstration, not a safety-critical medical or operational system. Patient details and map data are fictional. Data is stored per browser/device; no backend, authentication, secure multi-user sync, cryptographic signatures, conflict merge protocol, GPS, or real routing is implemented. The “online” toggle is a UI simulation and does not establish connectivity or send data to a server. Do not use for real emergencies or clinical decisions.
