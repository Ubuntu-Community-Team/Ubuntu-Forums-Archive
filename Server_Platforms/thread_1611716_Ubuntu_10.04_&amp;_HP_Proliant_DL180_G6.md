---
title: "Ubuntu 10.04 &amp; HP Proliant DL180 G6"
date: 2010-11-02
forum: Server Platforms
---

### Post by pvanberlo on 2010-11-02
Hi,

does anyone have any experience with installing Ubuntu 10.04 on a HP Proliant DL180 G6, especially via the LO100 virtual KVM? I can boot almost any linux distro with it, but unfortunately whenever I boot the Ubuntu server cd the screen gets garbled. I did some searching on the net, and found some references to older versions of Ubuntu where one had to add vga=771 to the boot options, but this still doesn't work with 10.04. I tried several vga modes, all to no avail (with vga=normal the screen gets garbled, with anything else the screen just stays black).

Anyone got any idea on how to fix this?

Thanks!

-Paul

---

### Post by pvanberlo on 2010-11-04
For anyone running into this issue, this is caused by the framebuffer. To get it working boot with vga16fb.modeset=0.

---

