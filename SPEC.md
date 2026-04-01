# Bumper Pool v2 — Complete Rebuild Spec

## What This Is
A **single-file HTML bumper pool game** with WebRTC multiplayer. Must be deployable to GitHub Pages (static hosting, no server).

## Reference
- `original-v14.html` — the current version (working but basic looking)
- Keep ALL existing game mechanics that work (physics, rules, multiplayer)
- This is a VISUAL and POLISH upgrade, not a mechanics rewrite

## Core Requirements

### 1. REALISTIC TABLE RENDERING
Make it look like a **real bumper pool table**, not a basic canvas game:
- **Felt texture** — deep green felt with subtle texture/noise pattern
- **Wood grain rails** — rich mahogany/walnut rails with visible wood grain, beveled inner edge
- **Rail diamonds/sights** — small inlaid diamond markers on rails like a real table
- **Realistic lighting** — subtle vignette, overhead light effect casting soft shadows
- **Table legs** hint — small shadow at bottom suggesting table depth
- **Bumper posts** — shiny chrome/brass cylindrical bumpers with reflective highlights, not flat circles
- **Pocket cuts** — realistic pocket openings with leather/rubber pocket liner look

### 2. BALL RENDERING
- **3D glossy balls** — proper sphere shading with specular highlight, ambient occlusion shadow underneath
- **Ball shadows** — soft circular shadow beneath each ball on the felt
- **Marked balls** — clear dot/star marking distinguishing the marked ball
- **Smooth rolling animation** — subtle rotation hint when moving
- **Red balls** = solid deep red with gloss. **White balls** = pearl white with gloss.

### 3. SHOT MECHANICS (keep existing, polish)
- **Cue stick visualization** — instead of just a dotted line, show an actual cue stick graphic when aiming
- **Power indicator** — elegant arc or bar showing shot power
- **Ghost ball** — faint preview of where the ball will go (first collision point)
- **Shot trail** — brief fading trail after ball is struck

### 4. SOUND EFFECTS (Web Audio API)
Generate procedural sounds (no external audio files needed):
- Ball-ball collision (sharp click, volume based on impact speed)
- Ball-rail collision (softer thud)
- Ball-bumper collision (metallic ping)
- Ball sinking in pocket (satisfying drop sound)
- Shot/strike sound (cue hitting ball)
- Win fanfare (simple celebratory tone)

### 5. MULTIPLAYER (PeerJS — keep existing pattern, improve)
- Keep PeerJS WebRTC approach (no server needed)
- Keep create/join with 4-letter codes
- Keep auto-join via URL parameter (?join=CODE)
- Keep share/copy link functionality
- **Add**: Connection quality indicator (green/yellow/red dot)
- **Add**: "Opponent disconnected" overlay with rejoin option
- **Add**: Ping display (small, unobtrusive)
- **Add**: State sync — if states diverge, host is authoritative
- **Add**: Smoother opponent shot rendering (interpolate positions)
- Keep iOS reconnect-on-focus fix

### 6. UI/UX POLISH
- **Lobby screen** — elegant dark theme with gold accents (keep current vibe but elevate)
- **Player names** — "Player 1" and "Player 2" (NOT Justin/Morpheus — make it generic)
- **Scoreboard** — show remaining balls as miniature ball icons, not dots
- **Turn indicator** — glowing border or subtle table edge light showing whose turn it is
- **Win screen** — particle effects (confetti/sparkle), winning player announced with flair
- **Smooth transitions** — fade between lobby and game states
- **Mobile-first** — responsive canvas sizing, comfortable touch targets, haptic feedback (navigator.vibrate on shot)

### 7. GAME RULES (preserve from v14)
- 5 red balls, 5 white balls (1 marked each)
- Simultaneous break — both players aim marked ball, fire at same time
- Must pocket marked ball first before others
- Pockets are player-specific (top pocket = red's target, bottom = white's target)
- Wrong pocket = ball bounces out
- Closest to own pocket after break goes first
- No sunk ball = turn passes to opponent
- First to pocket all 5 balls wins

### 8. TECHNICAL
- **Single index.html file** — all CSS, JS, HTML in one file
- **No external assets** except PeerJS CDN (https://unpkg.com/peerjs@1.5.4/dist/peerjs.min.js)
- **Canvas API** for all rendering (no WebGL required, but use it if you want)
- **60fps target** — smooth requestAnimationFrame loop
- **Mobile-optimized** — touch events, viewport meta, no zoom
- Works on iPhone Safari, Chrome, Firefox

## What NOT to Change
- Don't add a single-player/AI mode (multiplayer only)
- Don't change the fundamental physics (friction, bounce, collision) — they feel good
- Don't add accounts/auth/databases — this is a simple static game
- Don't add chat (they'll use iMessage alongside)

## Deployment
The output `index.html` will be pushed to GitHub Pages. That's it.

## Quality Bar
This should look like something you'd see on a premium casual gaming site, not a weekend hackathon project. The table should make people go "whoa, that looks real."
