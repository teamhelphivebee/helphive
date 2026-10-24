---
name: helphive-video
description: HelpHive video style guide. Use for every video edit — whenever the user sends raw footage, asks for a Reel/TikTok/short, or asks to edit, cut, caption, or post a video.
---

# HelpHive Video Style Guide

Apply this to every HelpHive video. The goal is a polished creator brand — cinematic, modern, natural — not a generic business ad and not over-edited or AI-looking.

## Tools
- **FFmpeg** for cuts, color, and audio.
- **HyperFrames** (HTML + GSAP) for all text and motion.
- Render a finished **1080×1920 MP4** (9:16, optimized for Instagram Reels).

## Edit
- Transcribe with word-level timings.
- Cut dead air and mistakes. Speed up silent action to 2x.
- Keep natural skin tones — never orange.
- Level voice to about **-14 LUFS**.
- **No music.** The user adds trending audio in Instagram.
- **Never overwrite the original video.** Work on copies; write outputs to new files.

## Hook (0–2s)
- The user's own words only — never invented.
- Small **DM Sans** uppercase kicker in cream `#FFFBF4`, wide letter-spacing.
- Then a big **Playfair Display 800** headline in butter yellow `#F8E38C`.
- Plus a **Playfair Display italic** accent line in cream `#FFFBF4`.
- Words pop in one by one as they are spoken (driven by word timings).

## Text rules
- **No full captions.** Highlight key words only.
- All text sits in the **top third** — above the user's head and clear of Instagram's UI buttons — with a soft dark gradient behind it and a soft text shadow.
- Key words become **butter-yellow pills** (DM Sans 700, off-black text) that pop in on cue.
- Quiet sections get a small **italic label** with a yellow underline that draws in.
- **3–4 text moments max.** Never busy.

## Ending
- An italic setup line, then one huge butter-yellow serif payoff word with a quick punch-in zoom.

## Motion and sound
- Slow push-in zooms that reset on every cut.
- Soft bell on the hook.
- Soft pop on each pill.

## Palette
| Use | Color |
|---|---|
| Butter yellow (headline, pills, underline, payoff) | `#F8E38C` |
| Cream (kicker, accent line, labels) | `#FFFBF4` |
| Off-black (pill text) | near-black, e.g. `#1A0E04` (site's dark brown-black) |

## Deliverables (every video)
1. Finished 1080×1920 MP4.
2. A cover-frame pick (timestamp + still image).
3. A post caption with search keywords worked in naturally (e.g. Boca Raton, Parkland, South Florida, babysitter, college sitters, backup childcare).
4. 5 hashtags.

## Approval
- **Show the user everything before posting or scheduling anything.** Never publish or schedule (e.g. via Metricool) without explicit approval.

## Implementation notes
- Transcription: `faster-whisper` with `word_timestamps=True` (pip-installable).
- HyperFrames: `npx hyperframes` (npm package `hyperframes`).
- Fonts: DM Sans and Playfair Display from Google Fonts; load them in the HyperFrames HTML.
- Keep the original footage untouched; put working files and renders in the session scratchpad, not the repo (videos are large and the repo is the public website).
- Sound effects (bell, pop) must be royalty-free or synthesized; keep them soft, under the voice.

## Lessons from past edits
- In cloud sessions, CDNs and model hosts may be blocked. What worked: fonts from npm (`@fontsource/dm-sans`, `@fontsource/playfair-display`) copied into `assets/fonts/` with `@font-face`; GSAP copied from the `gsap` npm package into `assets/`; render with `HYPERFRAMES_BROWSER_PATH` pointed at the pre-installed Chromium headless shell. Whisper models need `huggingface.co` allowed in the environment's network settings.
- If footage has no speech (Live Photos, b-roll), ask the user for their words (a sentence or voice memo) before writing any text. Spread their sentence across the Reel: hook, then pill, then payoff.
- Before placing text, check every shot for faces in the top third. If a shot has faces there, reorder the shots so text only lands where nobody is covered.
- Before posting, flag consent for any identifiable children, officers, or bystanders.
