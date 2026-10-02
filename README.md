# Do You Love Me?

A one-question pixel game. Pink background, two buttons. Clicking **No** swaps the
buttons, clicking **Yes** locks the answer in. Static site, no build step.

## Deploy to GitHub Pages

1. Create an empty repo on GitHub (no README, no `.gitignore` — this folder has both).

2. In this folder:

   ```powershell
   git init
   git add .
   git commit -m "pixel love questionnaire"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
   git push -u origin main
   ```

3. On GitHub, open the repo → **Settings** → **Pages** → **Source**:
   *Deploy from a branch* → branch `main`, folder `/ (root)` → **Save**.

4. Wait ~1 minute. The site goes live at:

   ```
   https://YOUR_USERNAME.github.io/YOUR_REPO/
   ```

Send her that link.

## Customizing

All of it is in `index.html`. The bits worth touching:

| What | Where |
| --- | --- |
| The question text | `<h1>` near the bottom of the file |
| Taunt lines after a wrong answer | `TAUNTS` array in the script |
| How many wrong answers before "No" is removed | `FORCE_AT` (currently 5) |
| Lines shown once both buttons say Yes | `FORCED_LINES` array |
| Opening line above the question | `.kicker` |
| Footer line | `<footer>` |
| Confetti colors | `CONFETTI_COLORS` |

Colors live in the `:root` block at the top of the `<style>`. Every text/background
pair was checked against WCAG AA, so text stays readable — if you change a color,
keep the dark ink `#4A0D2A` on the light pinks.

## Notes

- Works on phones. Buttons are sized for tapping, and hover-only tricks are absent
  on purpose.
- `prefers-reduced-motion` turns off the confetti and floating hearts.
- No analytics, no tracking. The only network request at runtime is the Google Fonts
  stylesheet for Press Start 2P and VT323.
- `.nojekyll` keeps GitHub Pages from ignoring folders starting with an underscore.