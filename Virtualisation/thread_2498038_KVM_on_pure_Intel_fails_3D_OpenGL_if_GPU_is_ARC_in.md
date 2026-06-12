---
title: "KVM on pure Intel fails 3D OpenGL if GPU is ARC in new Intel Core Ultra"
date: 2024-05-27
forum: Virtualisation
---

### Post by codelion on 2024-05-27
It almost works.  See the screenshot.  Can&#8217;t read a thing.  But the elements are there, if you know where to click and what to type.  If logging into the desktop, it continues to be messy and noisy like this.  But, things are there.  The colors are approximately right.  It&#8217;s not usable, but it seems close enough, this should be fixable.

[ATTACH=CONFIG]293818[/ATTACH]

Ubuntu 22.04.4 kernel 6.5 on host and same in guest VM.  For this VM in Virtual Machine Manager have selected Display Spice, Video Virtio.

Equivalent settings work on an 11th gen Dell XPS 13 with also pure Intel iGPU, in that case being the older Xe.

If running without enabling 3D this VM is borderline usable if needed, with visual tearing or so when actually using.  Also, without enabling 3D the VM is a CPU hog when drawing in the display.

The failure is on a brand new Dell Precision.  Bought with Ubuntu.  Then had to do a clean install of 22.04.4.  Had to use linux-oem-22.04d for it to work well.  Using the internal screen only, no external screen is connected.

Tried mainline 6.8.11 and 6.9.2, not any better results with VM and 3D, went back to signed 6.5.  I also made another VM on the same host, a cleanly installed 22.04.4 operating system.  Same symptoms.

This could be classified as a regression, with the new CPU / iGPU not working as well as the older CPU / iGPU.  Unless it is specific to new Dell Precisions.

Should I file a bug somewhere?  Can I help fix this?

---

### Post by codelion on 2024-05-28
Same problem if host and guest are Ubuntu 24.04.

Does anyone recognize the distinct visual pattern in above provided screenshot and knows what could consistently cause that kind of malfunction of display rendering?  What you see in the screenshot is instead of the little bit white and orange on mostly black initial screen when Ubuntu comes up.  That same kind of pattern continues to make it unusable when blindly logging into the desktop of Ubuntu.

How could we (myself, someone working with me, someone else) start debugging this and find a cause in source code?

---

### Post by codelion on 2024-05-29
A relevant issue has been going on for some time already at [https://gitlab.freedesktop.org/mesa/mesa/-/issues/9022](https://gitlab.freedesktop.org/mesa/mesa/-/issues/9022) and possibly also at [https://gitlab.com/qemu-project/qemu/-/issues/2282](https://gitlab.com/qemu-project/qemu/-/issues/2282) .

---

### Post by arabern0002 on 2024-10-09
Same problem on a brand new frame.work 13 inch laptop (running linux Mint 24 ), guest VM running linux mint 20.3

CPU: Intel(R) Core(TM) Ultra 7 155H, 
Integrated GPU: Intel Corporation Meteor Lake-P [Intel Graphics] (rev 08).

---

