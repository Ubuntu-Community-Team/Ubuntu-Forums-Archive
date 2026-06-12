---
title: "Widescreen monitors and ATI cards"
date: 2007-10-20
forum: Ubuntu Brainstorm
---

### Post by Super Nade on 2007-10-20
Maybe this has been addressed, maybe not, but it would be nice to see support out of the box for more widescreen monitors and the ATI cards. I had to force 800 x 600, uninstall fglrx and reinstall it to get ATI functionality. Can this be done out of the box?

My monitor is a Viewsonic VA1912WB (19.1 inch Wide screen) and with EVERY other distro, there was a black screen with X failing.

---

### Post by Zdravko on 2007-10-20
+1.

---

### Post by BungaMan on 2007-10-23
Monitors are already autodetected.  There is a mechanism in place so that video cards can query for the monitor capabilities.  Not all monitors correctly support this mechanism.  This makes the driver guess at what is possible.  As long as X doesn't hang, it will display the "bulletproof X" app.  However, the app itself is far from bullet proof.

---

