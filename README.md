# index.html — LocalSearch Australia (Homepage)

## Purpose
This file is a developer-ready homepage for LocalSearch Australia. It demonstrates accessible-first design, local SEO, EEAT signals, VOC hooks and a flexible media module that supports both 16:9 and 9:16 video.

## Files
- `index.html` — self-contained HTML with inline CSS and minimal JS for accessibility toggles.
- Media assets referenced in the markup (logo, video, captions, transcript) should be uploaded to:
  - `/media/logo.png`
  - `/media/v1.mp4`
  - `/media/v1.webm`
  - `/media/v1-thumb.jpg`
  - `/media/v1-captions.vtt`
  - `/media/v1-transcript.txt`
  - `/media/og-localsearch.jpg`

## Key features & rationale
- **SEO:** descriptive title & meta description; canonical link; Open Graph and Twitter card tags; JSON-LD for `LocalBusiness` and `VideoObject` to support rich results.
- **EEAT:** Case studies and author links show expertise; author pages planned to list credentials and experience; testimonials with names and businesses; explicit contact details and policies.
- **WCAG 2.1 Level AAA (practical):**
  - Skip link for keyboard users.
  - Focus-visible styles (high contrast, large outline).
  - All interactive elements reachable by keyboard.
  - Video includes captions and link to transcript.
  - High contrast toggle available.
  - Text sizes and line spacing tuned for readability.
  - Forms include labels (hidden visually when needed) and `aria-required`.
  - Colour tokens selected to provide high contrast — test combinations and provide alternate theme where required.
- **VOC:** simple one-question feedback form; subscription capture; feedback endpoint (`/_feedback`) should persist responses to a VOC queue.
- **Media module:** `.media-box` accepts `data-vertical="true"` for vertical (9:16) video. Server-side upload pipeline should inspect video orientation/metadata and set `data-vertical` accordingly. The CSS switches aspect ratio to 9:16 on small screens when vertical.

## Accessibility & QA notes
- Manual tests recommended with NVDA, VoiceOver and JAWS. Test keyboard-only journeys for:
  - Search and form submission.
  - Video captions on/off, transcript accessibility.
  - Modal/flyout interactions (if added).
- Run automated tests: axe-core, pa11y, Lighthouse accessibility.
- Contrast checks: ensure foreground/background pairings meet AAA thresholds. Adjust tokens if necessary.

## Developer handoff notes
- Convert inline CSS tokens to design system variables (Sass/JSON tokens) in production.
- Replace inline script with modular JS and unobtrusive progressive enhancements.
- Use server-side rendering or hydrated partials for dynamic content (listings, ratings, case studies).
- Implement structured data per template (listing pages, author pages, video pages).
- Capture UTM and referrer details in the audit signup and VOC forms.
- Ensure CSP headers allow media and captions sources.

## Performance
- Deliver images in WebP/AVIF fallback to JPG/PNG.
- Use responsive `srcset` for hero and listing images.
- Defer non-critical JS. Use HTTP/2 and a CDN to serve media.
- Lazy load offscreen images and media.

## Notes on video orientation handling
- On upload, detect orientation and set `data-vertical` to `true` if video height > width.
- Provide transcoded WebM and MP4 for broader compatibility.
- Provide .vtt captions and full text transcripts for every video.
- Do not autoplay audio. Autoplay muted is acceptable for previews; always provide controls.

## Next steps (recommended)
1. Create templates for: listing pages, author pages, search results, pricing, support and terms.
2. Implement server-side schema injection for each page type.
3. Implement review moderation and verification flows.
4. Run WCAG AAA remediation pass for full site; prioritise core user journeys first.
5. Add analytics events for CTA clicks, video plays, form submissions and VOC responses.

---

If you'd like, I will now produce the next page (`how-it-works.html`) with the same structure: inline CSS, JSON-LD where needed and a companion `README.md`. I can also convert this homepage CSS into a shared component style-guide file for developers (SCSS or JSON tokens) if you prefer.
