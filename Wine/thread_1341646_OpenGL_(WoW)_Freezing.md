---
title: "OpenGL (WoW) Freezing?"
date: 2009-11-29
forum: Wine
---

### Post by GJLenon on 2009-11-29
First, let me apologize for posting this.  I've searched the forums in depth, and the web, in general, and I've yet to come up with a reliable solution.

**Problem:**
When I run WoW under WINE, I seem to have random freezes.  I'm 95% sure the video card is seizing up.  Does anyone have any idea what to do?


**System:** 
[LIST]
[*]ubuntu 9.10 (Karmic Kaola) 32-bit
[*]Linux Kernal 2.6.31-15-generic
[*]AMD Athalon 64 X2 Dual Core Processor 5600+
[*]2 GiB RAM
[*]NVIDIA GeForce 9500 GT
[*]Latest NVIDIA drivers.
[/LIST]


**Background:**
During 8,10 and 9.04 I had zero problems with WoW.  It wasn't until 9.10 came out that I instantly developed problems.  Only two things have changed. (1)  I upgraded to 9.10, and (2)  I got rid of Ventrilo in favor of Mangler.  I don't think it's Mangler that's the issue, however.

~~~~~~~~~~~~~~~

Anyone else having this issue?  Am I alone?  Did my noob self mess something up?!

---

### Post by sorkan on 2009-11-30
Try to downgrade NVidia Drivers 173. The problem is Nvidia 180 drivers OpenGL.

I've done it and it works for me.

---

### Post by GJLenon on 2009-11-30
I appreciate the advice.  I downloaded the 173 drivers and installed them.  WoW does not work with those drivers any longer. :(  It says I need a 3D Accelerator with Dual-TMU support.

---

### Post by hikaricore on 2009-11-30
Why would you ever recommend downgrading drivers for WoW?
The 180 series should be fine but may be buggy depending on your card.

However you should be using the latest official:

> # Nvidia Drivers
deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main

Be sure to completely remove any old driver before installing 190.42.
And after installing try a native 3d application before wow to ensure they're working properly.

---

### Post by GJLenon on 2009-12-02
As dumb as this sounds, I believe I solved the problem by disabling the power saver features associated with monitor's in Linux.  By turning them from 5 minutes to Never, the problem seems to be fixed.

*(Warning, the following is done in my terminology, not in actual computing terms)*

I would assume this is due to WINE placing a "layer" over the Linux OS forcing all key pressing and mouse movement to be associated with WINE and ignored by ubuntu.

---

### Post by PariahVayne on 2009-12-02
x

---

### Post by 68pontiac on 2009-12-02
I'm having the same issue using an ATI Radeon 4350. I have the ATI proprietary drivers and I experience a lot of random freezing. Sometimes it'll take 10 minutes, other times it'll take several hours. I'll try the suggestion above regarding power saving. Never had any problems before switching to Karmic, though.

And for what's it worth I've read that a lot of low framerate problems have been fixed in the upcoming patch 3.3: Fall of the Lich King. :D

---

### Post by 68pontiac on 2009-12-03
Reporting back on my last comment - changing the power saving settings did nothing for me. The game locked up on me once in Howling Fjord and once on the zepplin from Orgrimmar to Warsong Hold within a 3 hour window. I hope somebody else has a more concrete solution.

---

### Post by GJLenon on 2009-12-03
Yes, I have Triple Buffering enabled.

The problem seems to have not gone away, now I'm wondering if the issue isn't the RAM on the Video Card.

---

### Post by 68pontiac on 2009-12-03
> **GJLenon said:**
> Yes, I have Triple Buffering enabled.

The problem seems to have not gone away, now I'm wondering if the issue isn't the RAM on the Video Card.

I'm no expert but it seems like if you didn't have a GPU problem in Jaunty you shouldn't have a GPU problem in Karmic. I read somewhere else that having WINE emulate a virtual desktop helped them with random crashes. I'll try it and report back later. I'll just set a virtual desktop to the same resolution as my X Desktop and continue to run fullscreen.

---

