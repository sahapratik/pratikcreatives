# Pratik Saha — Creative Design

A standalone creative design portfolio — static campaign/poster design and
short-form video edits — built on the same single-file architecture as the
main portfolio and the photography site. No framework, no build step.

## What's inside

- `index.html` — the entire site (HTML + CSS + JS in one file)
- `assets/design/static/` — 13 static designs, each as `-thumb.jpg` (grid,
  ~1000px) and full-quality `.jpg` (lightbox, ~2000px)
- `assets/design/video/` — 5 video edits, each as three files:
  - `-poster.jpg` — a still frame shown before the video plays
  - `-preview.mp4` — a small, silent, downscaled copy used for autoplay in
    the grid (keeps the page light — nothing full-quality loads until you
    open it)
  - `.mp4` — the original, untouched, full-quality file, used in the
    lightbox and the reel
- `assets/design/hero-loop.mp4` + `hero-poster.jpg` — a 10-second loop cut
  from "Not Loud. Just Legendary." for the autoplaying hero background
- `vercel.json` — same deploy config as the other two sites

Every asset is used exactly once in the grid/reel; none are duplicated.

## Features

- Same dark, cinematic visual system as the main portfolio and photography
  site (Hanken Grotesk, custom cursor, film-grain, animated preloader,
  scroll progress bar) — built as a genuine companion site, not a reskin
- Full-bleed autoplaying video hero (muted, looped, no controls)
- True masonry/bento grid using each asset's real aspect ratio
- **Auto-playing video, tastefully done**: grid and reel videos are muted
  and only play while actually on screen — an IntersectionObserver starts
  playback the moment a video scrolls into view and pauses it the moment it
  scrolls out, so nothing burns bandwidth or CPU off-screen
- Category filters: All / Static Designs / Video Edits
- Per-cell scroll reveal + 3D hover tilt
- Pinned, horizontal-scroll cinematic showreel (GSAP ScrollTrigger) mixing
  static and video work — swipes natively on mobile instead of pinning
- Lightbox with full-quality playback (video plays with sound, since that's
  a deliberate click) and keyboard/swipe navigation
- **No download option anywhere**: no download button or link in the
  lightbox; native video controls have their download affordance suppressed
  via `controlslist="nodownload"`; right-click and drag are disabled on
  every image and video. (Worth knowing honestly: nothing client-side can
  make web media truly impossible to save — a determined visitor can always
  find a way. This removes the obvious, one-click paths.)
- Every animation degrades gracefully if a CDN script fails to load

## Deploying

Push this folder to Vercel, or drag-and-drop it into the Vercel dashboard.
`vercel.json` is already set up for static hosting with long-cache headers
on `/assets`.

## Local preview

```
npx serve .
```

Opening `index.html` directly via `file://` also works — no build step, no
server-side code.
