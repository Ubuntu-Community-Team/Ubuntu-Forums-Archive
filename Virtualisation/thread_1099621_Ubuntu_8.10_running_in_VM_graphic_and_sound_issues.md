---
title: "Ubuntu 8.10 running in VM graphic and sound issues"
date: 2009-03-18
forum: Virtualisation
---

### Post by cecil68 on 2009-03-18
Host OS Win XP SP3
Guest OS Ubuntu 8.10

My PC is a clone running an AMD Athlon XP AM2 CPU and my video card in an ATI AIW 2005 and Sound is a Creative Labs Audigy. I dont need anything advanced with sound or graphics to work I would just like to have sound and be able to change my resolution to something I dont have to scroll for days on.

I have tried both MS Virtual PC 2007 and VirtualBox 2.1.4 and I get no sound and very low resolution for video.

I am a linux/Ubuntu newbie so you may have to dumb it down for me, sorry.

Anyway I have tried editing xorg.conf as numerous sites tell you to, no success.  I have attempted to install VMadditions for Linux in VPC and VboxAdditions in VirtualBox, I was able to get the Vboxadditions installed successfully but the additions in VPC never did install.

Even after installing the VBoxAdditions I still only have a choice of 800x600 or 640x480 resolution in the VirtualBox VM, what am I missing or doing wrong?  I tried VirtualBox because after spending days trying to get VPC 2007 with Ubuntu guest working I cam across a post where someone said they just run the Ubuntu install and graphics and sound worked.

---

### Post by bodhi.zazen on 2009-03-18
Hmm ...

Usually one installs the VirtualBox Additions (on the guest not the host) and then reboot the guest.

If it is not working , may I suggest the virtualbox forums ?

---

