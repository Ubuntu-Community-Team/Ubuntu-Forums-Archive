---
title: "Debian grub splash?"
date: 2012-03-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by MG&amp;TL on 2012-03-11
Running updated Precise, I noticed this morning that the Grub splash has gone....debian-ey...:D

Star fun, etc. It gave me quite a laugh, I have to tell you. I just wanted to check that somebody else has this bug before reporting it.

The splash is attached.

---

### Post by MacUntu on 2012-03-11
I doubt that's a bug. You probably installed the desktop-base package. Uninstall, run `sudo update-grub`, should be gone.

---

### Post by MG&amp;TL on 2012-03-11
> **MacUntu said:**
> I doubt that's a bug. You probably installed the desktop-base package. Uninstall, run `sudo update-grub`, should be gone.

Thanks, yeah, it was that. No idea why it got installed, something to do with lisp I think. :confused:

---

