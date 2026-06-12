---
title: "Beware of linux 4.2.0-15.17 (proposed repos., at the moment)"
date: 2015-10-07
forum: Ubuntu Development Version
---

### Post by fthx on 2015-10-07
Hi,

This kernel just freezes completely GDM. Hard reboot needed.
(I don't know if it is related but I use an integrated usual Intel GPU.)

---

### Post by rrnbtter on 2015-10-07
Greetings,
Same here but 4.3 RC4 seems to be ok.

System:    Host: rrnbtter-Satellite-L305 Kernel: 4.3.0-040300rc4-generic i686 (32 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily
Machine:   System: TOSHIBA product: Satellite L305 v: PSLB8U-0JG037
           Mobo: TOSHIBA model: Portable PC
           Bios: INSYDE v: 2.20 date: 12/09/2009
CPU:       Single core Intel 585 (-UP-) cache: 1024 KB speed: 2161 MHz (max)
Graphics:  Card: Intel Mobile 4 Series Integrated Graphics Controller
           Display Server: X.Org 1.17.2 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1280x800@60.00hz
           GLX Renderer: Mesa DRI Mobile Intel GM45 Express x86/MMX/SSE2
           GLX Version: 2.1 Mesa 11.0.0

---

### Post by dino99 on 2015-10-07
lightdm+nvidia-355; no issue with that kernel ):P

---

### Post by P-I H on 2015-10-07
I had to use the power button to reboot. Kernel 4.3 RC4 is working fine. I have proposed enabled and kernel 4.2.0-15 will crash. My graphic card is Radeon R9 380.

---

### Post by zika on 2015-10-07
(Alsmost) same here...
But, it works if You choose not to boot into GUI.
```
systemd: systemd.unit=multi-user.target 
upstart: text
```in kernel boot line.
GDM freezes tad bit later.
With other DMs (via xinit) all is good.
All is good with 4.3-999, 4.2-pf, 4.2-gnu...

---

### Post by harry332 on 2015-10-08
My setup (only Gnome-shell with GDM is installed) works well with the kernell 4.2.0-15.17.
However there is a new one available in proposed now: 4.2.0-15.18:

[https://launchpad.net/ubuntu/+source/linux/4.2.0-15.18](https://launchpad.net/ubuntu/+source/linux/4.2.0-15.18)

---

### Post by tista on 2015-10-08
@harry332,

Thanks for the head up, just now I've tried proposed 4.2.0-15.18 and seems works well on my Dell XPS11 (Haswell graphics).
But I'm running Gdm 3.18.0, Gtk+ 3.19.0, Gnome-Shell 3.18.0, Wayland 1.9.90 and Weston 1.9.90 though, anyway both "Gnome" and "Gnome on Wayland" worked on this kernel as we expected (XWayland and Weston surely works).

Regards.

---

### Post by dino99 on 2015-10-08
Discovered an issue with that kernel: 
the sound input device (hda nvidia in my case) is not identified; so no way to get sound
booting with an other kernel (14) and the sound is back as expected.
[https://bugs.launchpad.net/vlc/+bug/1503998](https://bugs.launchpad.net/vlc/+bug/1503998)

device sound detection problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1504078](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1504078)

---

### Post by awamunro on 2015-10-08
Yes the upgrade to [COLOR=#000000]4.2.0-15.18 fixes it for me[/COLOR]

---

### Post by rrnbtter on 2015-10-09
Greetings,
Kernel 4.2.0-16.19 with this morning's mesa updates and all is good with my Intel chipset. 
I will test it for a few days then back to 4.3 for me.

---

