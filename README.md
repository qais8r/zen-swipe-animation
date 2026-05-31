# Dia-Style Swipe Animation

A Zen Browser mod that restyles the native two-finger back/forward swipe indicator to feel closer to Dia: a dark translucent circular chevron slides in from the active edge, strengthens when the gesture will navigate, and lightly moves the page while swiping.

## What it changes

- Uses Zen/Firefox's built-in history swipe overlay instead of JavaScript injection.
- Restyles `#historySwipeAnimationPreviousArrow` and `#historySwipeAnimationNextArrow` into a larger dark circular indicator.
- Mirrors the indicator for forward navigation.
- Adds optional subtle page motion through the active `.browserStack`.

Because this is CSS-only, it cannot add a true Dia-style page snapshot transition if Dia implements that with browser internals. It only restyles Zen's existing swipe animation surface.

## Preferences

- `mod.dia_swipe.enabled`: enables or disables the mod. Default: `true`.
- `mod.dia_swipe.page_motion`: `subtle` or `off`. Default: `subtle`.
- `mod.dia_swipe.indicator_size`: any valid CSS length. Default: `64px`.

Zen exposes the string preference as `--mod-dia_swipe-indicator_size`, which `chrome.css` uses with a `64px` fallback.

## Local testing

1. Open `about:support` in Zen and click **Open Profile Folder**.
2. Create a `chrome` folder if it does not exist.
3. Copy the contents of `chrome.css` into `chrome/userChrome.css`.
4. In `about:config`, set `toolkit.legacyUserProfileCustomizations.stylesheets` to `true`.
5. Restart Zen, then test two-finger back and forward swipes on pages with available history.

For direct `userChrome.css` testing, create these prefs manually in `about:config`. The enabled pref matters because the mod uses Zen's documented negative `-moz-pref` check for the disable branch:

- `mod.dia_swipe.enabled` as boolean `true`
- `mod.dia_swipe.page_motion` as string `subtle` or `off`
- `mod.dia_swipe.indicator_size` as string `64px`

## Notes for submission

Zen's submission guidelines require a README and a 600x400 PNG screenshot. Add the screenshot URL to `theme.json` before submitting to the Mods Registry if the registry form requires a hosted image.
