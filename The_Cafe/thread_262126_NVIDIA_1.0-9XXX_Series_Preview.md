---
title: "NVIDIA 1.0-9XXX Series Preview"
date: 2006-09-21
forum: The Cafe
---

### Post by plb on 2006-09-21
From: [http://www.phoronix.com/scan.php?page=article&item=551&num=1](http://www.phoronix.com/scan.php?page=article&item=551&num=1)

First off, NVIDIA's proprietary drivers in the upcoming 1.0-9XXX release should finally support the GLX_EXT_texture_from_pixmap extension. This extension is required in order to use AIGLX, which has been sought after by many Linux desktop users. To this date, ATI and their proprietary fglrx drivers don't support the extension. At this point, it's up in the air as to what company will first deliver this support in their closed-source drivers. The open-source Intel and ATI drivers already support GLX_EXT_texture_from_pixmap.

Also added in the upcoming NVIDIA driver is support for a few new products. The NVIDIA MCP61 is the replacement to the GeForce 6100 integrated graphics, and this Chipset will be supported in the next release. The driver should also append support for the few GeForce 7 products not presently supported (e.g. 7950GT) and the Quadro Plex VCS.

Supported in the 1.0-8XXX drivers is support for Scalable Link Interface when using two GPUs. However, the 1.0-9XXX drivers will be the first to support Quad SLI. With Quad SLI support coming, we can only hope that we will see other long awaited SLI improvements. It would be ideal if new SLI optimizations were implemented along with other features, but that has yet to be confirmed. A single NVIDIA GPU performs approximately the same under the Windows and Linux drivers, however, once SLI is enabled the Linux drivers can barely provide any advantages.

The NVIDIA Linux Control Panel (nvidia-xsettings) will also possess a few major changes. The control panel should add some additional options for controlling the TV-out screen size, HDTV, and other display settings. We take it the new nvidia-xsettings options for the TV control will look similar to what ATI had done in the past with their control panel (fireglcontrolpanel) when having the TV-out tab. Other changes will likely come to nvidia-xsettings in order to support recent NV-CONTROL changes. NVIDIA will possibly deliver dynamic display possibilities for enabling real-time display devices such as LCDs or TVs without needing to restart X. This option was delivered to ATI's fglrx drivers a few releases ago. NVIDIA hasn't yet commented on any other possible video/XvMC changes. With nvidia-xsettings being improved, we will likely see a few changes occur to nvidia-xconfig.

Coming in the 1.0-9XXX drivers is support for OpenGL 2.1 and GLSL 1.2. A week ago the Khronos Group had publicly delivered the specification to OpenGL 2.1, as well as announcing its approval by the OpenGL ARB (Architecture Review Board).

The first release candidate for X.Org 7.2 is due out this October, but there has been no word yet from NVIDIA on their position for support. The next releases of Fedora and Ubuntu (Core 6 and Edgy Eft 6.10, respectively) will use X.Org 7.1 while OpenSuSE/SuSE looks like it will be the first major distribution to ship with X.Org 7.2. If X.Org 7.2 ends up breaking the API/ABI, it is not known when NVIDIA intends to deliver a supportive driver.

For what it's worth, the NVIDIA 1.0-9XXX drivers will fix a Google Earth rendering bug. Other miscellaneous bug fixes including addressing a full screen bug presented with the 1.0-8774 drivers, pfVideoRate bug, memPhysBase bug, broken stereo on NV25, and a blinking desktop cursor issue.

One of the items we can only speculate on at this point is whether the NVIDIA Linux drivers will finally offer a revamped installer. ATI has certainly has the leading installer at this point, with its graphical install mode and ability to generate packages for specific distributions. ATI has worked very well with the community in the respect of installation support.

With many of these changes we would expect the Solaris change-log to look very similar. The NVIDIA FreeBSD drivers will likely be similar with the exception of Scalable Link Interface (SLI) support. The changes do look hefty and promising at this point, but how long you will have to wait before seeing this driver is still unknown. The initial 1.0-8XXX driver was expected in the September ~ November timeframe last year, but that driver had been delayed until the start of December.

---

