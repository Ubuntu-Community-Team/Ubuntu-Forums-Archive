---
title: "HELP! with boot"
date: 2015-12-01
forum: Server Platforms
---

### Post by luke59 on 2015-12-01
i guets install ubuntu server but win i boot i get '_' flasfing.

---

### Post by oldfred on 2015-12-01
Do you have a video card?
What are system specs?

Do not know server install, but often related to needing a boot parameter for video card.

---

### Post by T.J. on 2015-12-01
if you are using the AMD Catalyst driver, it is possible that your X11 display manager is not configured properly.  Do you get a login prompt if you press ctrl+alt+F1?  If so, login on the prompt and type "startx" (which may or may not work depending on what Canonical broke.  Don't be discouraged if it doesn't work.)  If you get your desktop, great - all we need to fix is the display manager and that's easy.

Please post back with your results.

---

