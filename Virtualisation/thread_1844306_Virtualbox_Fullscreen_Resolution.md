---
title: "Virtualbox Fullscreen Resolution"
date: 2011-09-14
forum: Virtualisation
---

### Post by gunit888 on 2011-09-14
I'm running Xubuntu 11.04 and I have VirtualBox 4.0.4 installed, running Xubuntu 11.04 as a guest, with Guest Additions installed.  I'm trying to set up the resolution so that the guest OS takes up the fullscreen on my second monitor, and to do that I need to use xrandr to create a mode, add that to the output, and switch to that mode.  

However, when I run xrandr, I notice that I get this message:

```
xrandr: Failed to get size of gamma for output default
```I noticed that on my host OS, when I call xrandr, the output is named LVDS1, and I understand that this will differ among installations depending on what your individual set up is.  But, the Virtualbox listing default makes me think that perhaps something isn't set up correctly.

When I try to do all my setup:
```
cvt 1280 1024
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode default "1280x1024_60.00"
xrandr --output default --mode "1280x1024_60.00"
```I don't get any change in resolution, and instead get these error messages:
```
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed
```I'm not sure exactly what is wrong or how to fix it.  Has anyone come across this before?

---

### Post by overdrank on 2011-09-15
Moved to Virtualization :)

---

