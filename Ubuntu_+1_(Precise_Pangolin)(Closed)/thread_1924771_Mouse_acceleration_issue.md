---
title: "Mouse acceleration issue"
date: 2012-02-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by t1497f35 on 2012-02-13
Hi,
I set the mouse acceleration to the lowest possible value but it still moves too fast for me. Anyone knows if it's being worked on?

On Ubuntu 11.10 the situation is better but still sucks.
Using a usual USB "Genius" laser mouse.

---

### Post by andrek on 2012-02-13
Same here, did anyone fill a bug report on this?

---

### Post by xyzzyman on 2012-02-13
Oddly enough I've found my touchpad is slower in PP no matter what settings I use. I just haven't taken the time to look into it.

---

### Post by t1497f35 on 2012-02-14
The Gnome3 devs probably didn't implement properly the acceleration range algorithm cause I remember that I had no issues with the Gnome2/Gtk2-based mouse acceleration interface.

---

### Post by kaldor on 2012-02-14
If I modify the mouse accel/sensitivity on a fresh session and then restore it to default, the mouse is super slow. Same for touchpad. This is pretty frustrating considering I'm a casual gamer.

Bug report [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/918071").

---

### Post by mc4man on 2012-02-14
> **kaldor said:**
> If I modify the mouse accel/sensitivity on a fresh session and then restore it to default, the mouse is super slow. Same for touchpad. This is pretty frustrating considering I'm a casual gamer.

Bug report [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/918071").

At least here the touchpad settings do nothing, havent since early 11.10 dev

As far as the mouse - have you tried resetting the defaults thru gsettings or gconf-editor, the defaults are -1.0 & -1, neither of which can be set in System Settings where the far left is 1.0 & 1

---

