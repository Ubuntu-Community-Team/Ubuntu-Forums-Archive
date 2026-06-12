---
title: "Horizontal Scroll on Touchpad"
date: 2013-02-17
forum: Ubuntu Development Version
---

### Post by superchar42 on 2013-02-17
13.04 doesn't have the horizontal scrolling options in the mouse and touchpad options, where would this be found now? (and why was it changed?)

---

### Post by mc4man on 2013-02-17
Maybe it's been decided it's no longer needed..(file bug if desired
To enable (per session, add to startup for persistent
```
synclient  HorizEdgeScroll=1
```
To see avail & current
```
synclient -l
```

---

### Post by EgoGratis on 2013-02-17
GNOME did some  changes:

[http://www.omgubuntu.co.uk/2013/02/ubuntu-13-04-gains-improved-mouse-touchpad-settings](http://www.omgubuntu.co.uk/2013/02/ubuntu-13-04-gains-improved-mouse-touchpad-settings)

And it looks like feature (checkbox) you are looking for was removed. This is common nowadays and seen before in for example Nautilus and elsewhere:

[http://ubuntuforums.org/showthread.php?t=2116588](http://ubuntuforums.org/showthread.php?t=2116588)

According to this report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1084737](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1084737)

You can at last enable the feature with command and it's (not yet) completely gone:

```
dconf write /org/gnome/settings-daemon/peripherals/touchpad/horiz-scroll-enabled true

```

But don't feel bad abut it it won't help. ;)

---

### Post by superchar42 on 2013-02-17
Ego, thanks! I'm sliding sideways now! , and thanks mc4man for the other option, I decided to use EgoGratis' solution, though.

---

### Post by nomenkultur on 2013-02-20
removing necessary stuff = typical gnome devs

---

