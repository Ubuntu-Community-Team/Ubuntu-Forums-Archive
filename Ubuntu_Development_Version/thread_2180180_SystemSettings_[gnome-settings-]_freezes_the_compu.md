---
title: "SystemSettings [gnome-settings-] freezes the computer"
date: 2013-10-11
forum: Ubuntu Development Version
---

### Post by VMC on 2013-10-11
This has been happening for some time now. 
Opening the SystemSettings (gnome-settings-), and activating any of the settings will usually freeze my pc. Some times I can move back and forth, setting or viewing any of the icons, but always when I try to close the window - clicking on the close button, it freezes.

[bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1239010")

---

### Post by VMC on 2013-10-12
I think now the problem lies in my graphics chip (yet again).

I realized that is crash occurs both in Ubuntu Unity and Ubuntu Gnome. So installing nvidia-304 [COLOR=#333333][FONT=UbuntuRegular]proprietary [/FONT][/COLOR]driver fixed the SystemSettings freeze, but the open-source ***nouveau*** driver still needs to be fixed. I just added the bug report to the wrong area.

---

### Post by Baldrick_NZ on 2013-10-12
I have the same problem, but using an intel sandybridge chip. I had to kill the system settings process as it was hogging RAM. But would prefer a better fix...

---

### Post by VMC on 2013-10-12
Using the nvidia-304.88 proprietary driver. Now my system is "jerky". If I try to move any window, or playing a board game the movements are sluggish. They were smooth using nouveau.

One thing compounds another. I prefer nouveau.  nvidia-304.88 also increases boot time.

---

### Post by philinux on 2013-10-12
just to be clear. System settings is gnome-control-center .

---

### Post by VMC on 2013-10-12
> **philinux said:**
> just to be clear. System settings is gnome-control-center .
that's strange, on my Ubuntu ps shows gnome-settings-, but on Gnome3 ps does show gnome-control-center.

I just tried nvidia-173 on Gnome3 and everything is smooth. I'll next try 173 on Ubuntu and see if that makes a difference.

---

### Post by VMC on 2013-12-31
There has been some development in the area. If you look at [post #72 of the bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1242767/comments/72"). Using the "soft" IOMMU works.

Edit:so this [workaround]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563481/comments/24") fixed the gnome-control-center freezes.

I have no idea how the value was determined. I just inserted the same value into mine.

Here is the manual from the kernel.org boot options:

Under the heading:
IOMMU (input/output memory management unit) >  [FONT=Verdana]swiotlb=<pages>[,force] explanation.

Edit2: More discussion on the messy [IOMMU soft hack]("https://bbs.archlinux.org/viewtopic.php?id=168555") .[/FONT]

---

