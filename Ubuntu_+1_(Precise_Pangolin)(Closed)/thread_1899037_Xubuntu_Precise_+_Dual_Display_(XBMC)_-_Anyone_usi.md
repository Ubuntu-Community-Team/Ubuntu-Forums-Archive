---
title: "Xubuntu Precise + Dual Display (XBMC) - Anyone using it?"
date: 2011-12-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-12-22
This is not work, it's about my home HTPC.

My current setup is running Ubuntu PP (Unity Session). I have one standard 19" LCD/VGA monitor usable at a Unity (3D) session, plus 2 LCD TVs, with no desktop session, running different instances of xbmc and lircd, controlled by 2 infrared remotes. 

The TVs connect via HDMI and have independent sound channels via pulseaudio. So each TV can watch any media and have separate video/audio/IR Control while keeping the HTPC 19" monitor usable (mouse, keyboard, sound, etc). 

This is important to me cause the 19" monitor runs a maximized browser that shows a summary of new usenet releases, available/failed/finished downloads, etc. I use it to program media, playlists, downloads, that are automatically processed to the NAS and accessible on the two TVs libraries. 

Although it's not so heavy on the hardware, cause most of the real work is done on VDPAU on the GFXs, I'd like to replace this small server distro to a lighter one. It makes no sense to have it running unity.

But I know it seems like XUbuntu/Lubuntu had problems with multi screen in the past. Does anyone knows if current development version works with such a setup and Nvidia proprietary drivers? The important thing is that it must be able to have 3 independent screens in xorg, on which I can open apps with DISPLAY=:0.1 xeyes, DISPLAY=:0.2 xeyes, etc.

Thanks,
Effenberg

---

### Post by effenberg0x0 on 2011-12-23
To provide some info for anyone that may eventually reach this thread: I had no luck on setting 2 instances of xbmc to use maximized $DISPLAYs (:0.1, :0.2) with Xubuntu, even on two exactly equal NVidias VGAs (9500GT/PCIe/8x/no-sli,Hdmi) and was too tired to keep working on it. There probably is some way but I was not in the mood.

On the other hand, it worked almost out-of-the-box, with minimum adjustments to nvidia-settings on a default PP (Alpha) **Lubuntu** install. Both TVs are running xbmc and the primary monitor is displaying the desktop, as it was supposed to be. Lubuntu is a nice and light option for a HTPC anyway.

Now, getting Linux devinput to recognize and work simultaneously with two IR receivers, directing each receiver data to only one instance of xbmc, is a whole different game, and demands recompiling lircd to allow for two completely separated instances to be ran simultaneously, even though they might share the same config files (in case both receivers/remotes are of the same brand, model, buttons, protocol, ir-keytable, etc - which of course is the case here).

---

