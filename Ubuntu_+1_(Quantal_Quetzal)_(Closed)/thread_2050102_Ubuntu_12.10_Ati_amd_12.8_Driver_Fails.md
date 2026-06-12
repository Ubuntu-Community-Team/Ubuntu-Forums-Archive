---
title: "Ubuntu 12.10 Ati amd 12.8 Driver Fails"
date: 2012-08-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mahajanudit on 2012-08-30
I have installed 12.8 (new) Ati Amd driver for my Mobility Radeon HD 7550.
After installing I configured xorg.conf using "aticonfig --initial" and restarted the laptop.
I got the screen saying the system is running in low graphics mode. graphics drivers etc could not be determined. And gives me 4 options:  1. Run in low graphics mode for just one session 2. Recofigure graphics 3. Troubleshoot error 4. Exit to console login. Re configuring graphics doesn't help either.

Contents of my xorg.conf file are:

> Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection



Any idea what to do next?

---

### Post by sffvba[e0rt on 2012-08-30
*Thread moved to **Ubuntu +1 (Quantal Quetzal)**.*


404

---

### Post by jfernyhough on 2012-08-30
Two things:

1) fglrx (i.e. the AMD proprietary drivers) doesn't support xserver 1.13 yet.

2) Your card needs the "legacy" drivers.

Hint: search this section for fglrx.

---

### Post by defconoii on 2012-08-30
just delete your /etc/X11/xorg.conf and use the legacy driver for now unless anyone comes up with a hack to get it working, videos and gnome shell work fine with legacy, not sure about 3D though

---

### Post by jfernyhough on 2012-08-30
Whoa, whoa, hold on there! :) The "legacy" drivers are not the same as the open-source drivers.

AMD stopped supporting older cards (HD2000-HD4000) in their normal driver package. For those older cards there's another driver package - the so-called "legacy" drivers (which I can not test as I have an HD5650). These drivers are those you install via jockey or download from AMD (which probably also need to be patched). The kernel module is named "fglrx".

The open-source drivers are those that are used by default when you have not installed the AMD drivers. IIRC the packages are something like xserver-xorg-video-ati and these "should" work well for everything other than 3D applications (and they may also still lack some of the power saving features of the AMD driver). These drivers are already installed. The kernel module is named "ati".

---

### Post by QIII on 2012-08-30
"Whoa" is right.  The current ATI driver most certainly does support HD 2000 - 4000 series cards.   For a list of cards that require the legacy driver, please see the wiki in my signature in the "Using the Ubuntu repository, alternate command line method" section.  I have included a link to ATI's website listing the legacy cards. Not that the legacy driver is of any use, since it hasn't worked with x server since 2009.

The driver in the Precise repo, the one you are offered by the GUI, is 12.4 and is NOT the legacy driver.

A bet I would take to the bank is this:  ATI will be sure that the 12.10 driver works flawlessly with Ubuntu and has made it available for inclusion in the repo before the RC is released.  Canonical and AMD/ATI are virtually in bed together, much to the chagrin of much of the rest of the Linux community, which has to wait until after Ubuntu is released to get the xx.4 and xx.10 drivers.

Currently, however, the driver will not work with Quantal without some patching and this pattern has been the case during Ubuntu development cycles for a long time.

---

### Post by FlipStonE on 2012-10-16
Hello,

Is there yet a hack to make this driver work on 12.10?  Just installed, still small screen resolution, and no unity showing up...

Greetz,
FlipStonE

---

