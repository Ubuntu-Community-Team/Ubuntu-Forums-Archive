---
title: "Another NVIDIA driver (290.06) is out!"
date: 2011-11-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by portis on 2011-11-04
Release highlights since 290.03:

    Added support for the following GPU:
        * GeForce GTX 460 SE v2
[B]    Fixed a bug that would cause applications which export custom allocation functions to our driver (such as Adobe Flash in Firefox or Chrome) to crash.
[/B]

The 290.06 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86 is available for download via FTP.
The 290.06 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86_64 is available for download via FTP.

Please see the README (x86 / x86_64) for more information about this release.

Please note: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.

Please also note: If you encounter any problems with the 290.06 NVIDIA Linux graphics driver release, please start a new thread and include a detailed description of the problem, reproduction steps and generate/attach an nvidia-bug-report.log.gz file (please see [http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678) for details).

---

### Post by Harry33 on 2011-11-04
Yes I have noticed some odd behavior with adobe flash plugin.
So it might be due to the 290.03 driver.

And yes, I look forward to see this new driver in Xorg-edgers PPA.

---

### Post by portis on 2011-11-04
flashplugin 11.2 beta1 still crashes with this driver.
So it's flashplugin's own problem.

---

### Post by Harry33 on 2011-11-05
> **portis said:**
> flashplugin 11.2 beta1 still crashes with this driver.
So it's flashplugin's own problem.

That is a beta after all.

---

### Post by paul_in_london on 2011-11-07
290.06 is now available from xorg-edgers and flashplugin 11.2 beta1 is working here (64 bit) :)

---

### Post by Harry33 on 2011-11-07
> **paul_in_london said:**
> 290.06 is now available from xorg-edgers and flashplugin 11.2 beta1 is working here (64 bit) :)

Right, Ricotz has uploaded that great driver version today.
Thanks to him.

---

### Post by Harry33 on 2011-11-09
> **paul_in_london said:**
> 290.06 is now available from xorg-edgers and flashplugin 11.2 beta1 is working here (64 bit) :)

Nvidia-current and nvidia-settings (290.06) are in Xorg-edgers precise branch now too.

---

