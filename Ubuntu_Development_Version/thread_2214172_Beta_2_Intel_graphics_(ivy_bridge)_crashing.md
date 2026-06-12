---
title: "Beta 2: Intel graphics (ivy bridge) crashing"
date: 2014-03-30
forum: Ubuntu Development Version
---

### Post by Luke M on 2014-03-30
I get a blank screen when I boot. I can get a console with c-a-F1, and there are a bunch of graphics driver errors, like "stuck on render ring".

---

### Post by cariboo on 2014-03-30
It would help if you let us know what graphics chipset and driver you are trying to use.

---

### Post by Luke M on 2014-03-31
> **cariboo907 said:**
> It would help if you let us know what graphics chipset and driver you are trying to use.

Intel ivy bridge (HD4000)

[http://en.wikipedia.org/wiki/Intel_HD_Graphics](http://en.wikipedia.org/wiki/Intel_HD_Graphics)

---

### Post by Luke M on 2014-03-31
For future reference:
acceleration can  be disabled by placing this in /etc/X11/xorg.conf:

Section "Device"
   Identifier "Intel Graphics"
   Driver "intel"
   Option "NoAccel" "True"
EndSection

(source: [https://wiki.archlinux.org/index.php/Intel_Graphics](https://wiki.archlinux.org/index.php/Intel_Graphics))

---

