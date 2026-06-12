---
title: "[Xorg]Intel-2.99.914 upstream bug-fix"
date: 2014-09-14
forum: Ubuntu Development Version
---

### Post by tista on 2014-09-14
Hi guys,

A couple of days ago, we've experienced newer Xorg 1.16 series. And I've encountered an ugly bug as well:
(In Arch Linux)
[https://bugs.archlinux.org/task/41443]("https://bugs.archlinux.org/task/41443")

**[details]**
 Once SNA acceleration was enabled, seemed to got a segmentation-fault with i965-dri.so. My Baytrail-M uses i965 DRI2/3 driver so, I got "trap" and "seg-fault" on gnome-shell as well. Gnome-shell suddenly crashed and restarted automatically but it seems to die mutter at all...

**[upstream patch]**
 Already Xorg team solved this bug with this patch:
[https://bugs.freedesktop.org/attachment.cgi?id=105160]("https://bugs.freedesktop.org/attachment.cgi?id=105160")

But today, our Utopic's latest 2:2.99.914-1~exp1ubuntu2 (and previous d2:2.99.914-1~exp1ubuntu1, too) didn't applied that patch yet (I've confirmed that because I now see the source package).

**[workaround]**
 We could avoid those SNA/DRI2 crach by switching accel-method to UXA or GLAMOR. I now applied GLAMOR with re-building glamor option. Anyway SNA seems to break something. And I didn't rebuild it with that patch, but I suppose it would solve this issue...

Best Regards,
Tista


**EDITED #1**
 OMG. that patch didn't fix this issue (means on my Baytrail-M instead of Optimus)
Still dmesg says:
```
traps: gnome-shell[9385] trap int3 ip:7ffc40da1c90 sp:7fff917696e0 error:0
gnome-shell[10361]: segfault at 20 ip 00007f1d89ee8003 sp 00007fff2b9206a0 error 4 in i965_dri.so[7f1d89bd1000+51a000]
```
And I saw 1 error Xorg.0.log:
```
(EE) intel(0): intel_set_pixmap_bo: size of buffer object does not 
match constraints: size=512, must be greater than 8192, but less than 67108864
```

I'm not sure what's happening, but I would keep tracking this issue down because GLAMOR uses super-slow LLVMPIPE to run mutter.;)

---

