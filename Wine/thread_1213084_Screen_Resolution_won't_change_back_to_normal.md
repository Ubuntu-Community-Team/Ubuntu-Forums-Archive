---
title: "Screen Resolution won't change back to normal"
date: 2009-07-14
forum: Wine
---

### Post by ubudog on 2009-07-14
Hi, every time I play a game in fullscreen in wine when I exit the Screen Resolution is all messed up.  When I log off and log back in everything is fine.  Is there a way to set it to automatically go back to the correct Screen Resolution when I close a game?

---

### Post by DoktorSeven on 2009-07-14
Not automatically but I bind a key shortcut that runs the following to fix that after a Wine or native game doesn't exit cleanly, which sounds like your problem:

xrandr -s 1 && xrandr -s 0

(Two since doing straight to 0 sometimes doesn't work; you might have a different xrandr mode to set, so look at xrandr -q and its man page.  0 is the highest resolution/refresh available.)

---

### Post by ubudog on 2009-07-14
Thanks so much!

---

