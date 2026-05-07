# TM Café — Capstone Prototype

Mobile-first clickable prototype for the TrulyMadly TM Café capstone, with an embedded ElevenLabs AI Triage voice agent.

## Live demo

Once deployed: `https://truly-madly.onrender.com` (or your Render URL).

## What's in this folder

- `index.html` — the entire prototype (single file, no build step)
- `assets/` — Stitch frame reference PNGs
- `render.yaml` — Render Static Site config
- `_redirects` — Netlify redirect config (for SPA routing if used)

## Deploy to Render (recommended)

1. Push this folder to GitHub (already done if you're reading this from the repo).
2. Go to https://render.com → sign up with GitHub.
3. Click **New** → **Static Site**.
4. Connect your GitHub account → select the `TrulyMadly` repo.
5. Configure:
   - **Name:** `tm-cafe`
   - **Branch:** `main`
   - **Root directory:** `tm-cafe-final` (if pushed as subfolder) OR leave blank if at repo root
   - **Build command:** (leave empty — no build needed)
   - **Publish directory:** `.` (single dot — or `tm-cafe-final` if using subfolder)
6. Click **Create Static Site**.
7. Wait ~60 seconds for first deploy.
8. Render gives you a public URL like `tm-cafe-xxxx.onrender.com`.

## Deploy to Netlify (fastest alternative)

1. Go to https://app.netlify.com/drop
2. Drag the entire `tm-cafe-final` folder onto the page.
3. Done — instant URL.

## Mobile view

The prototype is mobile-first:
- On desktop browsers (>900px wide): renders inside a 390×844 phone frame with iOS-style notch
- On mobile browsers (≤900px): fills the full screen, looks like a native app
- HTTPS is required for microphone permissions (both Render and Netlify provide this automatically)

## ElevenLabs voice integration

The voice agent appears as a floating microphone widget in the bottom-right corner ONLY on the In-Call screen (Frame 6). Mount/unmount logic:
- When user navigates to Frame 6 (`/call`), the widget is dynamically mounted and the script loads
- When user leaves Frame 6, the widget is unmounted and the session is ended

**Agent ID:** `agent_8401kqzfx7n9ev78hx24a0gyy9g4` (configured in the script).

## Demo flow

```
Frame 1 (Homepage) — tap "Explore Café" →
Frame 2 (What brings you here?) — pick language + emotional state →
Frame 5 (Listeners list, Niharika BEST MATCH) — tap "Audio" on Niharika →
Frame 6 (In-call) — tap the floating ElevenLabs mic widget → speak →
Frame 7 (Session-end) — tap "Rebook in 3 days" →
Frame 8 (Day-3 push + UPI rebook) — tap "Pay ₹199 via GPay" → loops to Frame 6
```

Side branches:
- **Demo menu** (top-right ⋮ icon) → Reset to Homepage / Simulate trigger
- **Frame 4** (Homepage with trigger card) — reachable via Demo menu

## Mobile + voice testing

1. Open the live URL on your **phone** (not laptop) — mic permissions are most reliable on mobile Chrome/Safari
2. Navigate to Frame 6 (Audio call)
3. Tap the small microphone widget in the bottom-right corner
4. Grant microphone permission
5. Wait 2-3 sec → Niharika should greet you in Hindi/Hinglish
6. Speak: *"Mera breakup ho gaya hai"*
7. Agent should respond, recommend Niharika, hand over

## Key copy (verbatim)

- Trigger card H1: "Tough week? You don't have to sit with it alone."
- Triage safety: "You can end this any time. No questions asked. We don't record. We don't store."
- Call quote: "Take your time. There's nothing you can say here that will surprise me."
- Session-end H1: "Thank you for showing up for yourself today."
- Footer: "You don't have to figure it all out tonight."
