---
title: "Cannot view video clips"
date: 2011-07-05
forum: System76 Support
---

### Post by hkarl629 on 2011-07-05
Am running a Serval - Serp2 with Ubuntu 10.04, Gnome 2.30.2, 2Gb memory, Intel dual Core CPU T5600 @ 1.83 GHz.

If I put a DVD in the drive, Totem runs it just fine. Audio and Video.

If I go to a website which has a video clip and I click to play it, all I get is a black, white or gray rectangle. No picture, no audio.

I know this is something this computer can do, but something is missing and I don't know what it is.

Your help is appreciated.

Karl

---

### Post by nomko on 2011-07-05
Did you install:
- **flashplugin-nonfree**
- **ubuntu-restricted-extras**
 
These packages can be foudn in synaptic.
The there's a site called medibuntu: [http://medibuntu.org/](http://medibuntu.org/). Just look at this site how to add the repository to your software sources. 
From this site you need to install:
- **w32codecs (for 32-bit)**
- **w64codecs (for 64-bit) **
- **libdvdcss2**
- **non-free-codecs**

---

