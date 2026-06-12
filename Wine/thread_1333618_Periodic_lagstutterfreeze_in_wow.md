---
title: "Periodic lag/stutter/freeze in wow"
date: 2009-11-21
forum: Wine
---

### Post by Ameneon on 2009-11-21
A problem I thought resolved has crept back in again the last few weeks;

Wow will periodically stutter (audio and video), as often as every few seconds, making the game not unplayable but very much less enjoyable for certain. Previously, this problems seemed to be tied to xorg leaping in cpu usage every so often, and was foremost seen when the system monitor was started. Now however I'm getting the problem even without the system monitor running (although granted the issue is exaggerated when system monitor is running as well).

Running 9.04 gnome without any visual effects, gxapi set to opengl and the usual fixes.

Anybody with the same problem or with good ideas as to what it could be? Result is the same whether I run with addons or clean wow.

---

### Post by Xog on 2009-11-21
open terminal and type

```
wine --version
```

to see your latest version of wine. if it's not the latest version, update it.

try turning down the resolution to see if that helps
also see if you have the latest drivers for your video card.
what kind of video card do you have?

---

### Post by jaymzw on 2009-11-25
Try playing with your power management settings as detailed in this thread:

[http://ubuntuforums.org/showthread.php?t=1312185](http://ubuntuforums.org/showthread.php?t=1312185)

---

