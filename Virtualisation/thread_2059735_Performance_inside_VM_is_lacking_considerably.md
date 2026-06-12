---
title: "Performance inside VM is lacking considerably"
date: 2012-09-18
forum: Virtualisation
---

### Post by schwim on 2012-09-18
Hi there everyone,

On the problem machine, I've got 6 VM's installed.

XP
Zorin 6 Ultimate
Fedora 17
Mac OSX(Snow Leopard)
Mint Debian
Ubuntu 12.04

All VM's except for the Ubu install runs very well and I'm able to use them to work in.  My attempts to use the Ubu VM results in very poor performance, sluggish response and jerky window scrolling.  I am unable to use it for my purposes.

I've allocated more resources to the Ubu VM(4 cores, 2gb mem, 3d accel, 128 vid) but it's running much worse than the other VM's which are alloted 1/4 of the system resources.  I have tried logging into 2d, but the problem persists.

Might anyone have some suggestions on how to get Ubuntu to run more smoothly in a VM?

Thanks a bunch for your time!

---

### Post by oldos2er on 2012-09-18
Moved to Virtualization.

---

### Post by afz12 on 2012-09-18
I found something similar with Ubuntu 12.10 beta 1. The 64 bit version was jerky in Virtualbox but the 32 bit version was fine. I allocated 4 cores and 3450 MB of memory - same outcome. Interestingly, Mint Cinnamon ans Mint Mate ran fine as 64 bit machines.

---

### Post by CharlesA on 2012-09-18
12.04 x64 runs perfectly fine on both the boxes I have it running as a VM on.

One has 1 core allocated, the other has 2 cores.

---

### Post by schwim on 2012-09-18
I tried 12.10 beta 1 before 12.04 and the experience was even worse for me that what I'm experiencing in .04.  I rolled back before trying to resolve the issue because of the problem with guest additions not installing properly in .10.

Also, I'm using 32 bit host and VM.

---

### Post by afz12 on 2012-09-18
The clues so far seem that CharlesA has U 12.04 64 bit and this VM is OK - presumably his host is 64 bit. This notebook is an hp i5 64 bit quad-core running Ubuntu 12.04 and I only had jerky results on a particular U 12.10 beta download - I might try the same with  U 12.04 64 bit but I suspect this will be OK (as other 64 bit OS' run fine in Virtualbox). However schwim's machine is only 32 bit - perhaps it has some hardware limitations?

Also is the vrtualization based on Virtualbox or VMWare or some other?

I have found that when difficulties occur in Virtualbox for any reason, changing internal settings won't make much difference. The main issue Virtualbox has these days is with USB support - I have always found that some syntax needs to be entered through the terminal to add me as a Vbox user. The "filters" inside Virtualbox don't serve this purpose.

I have another notebook running Mint and has Virtualbox installed now. I think I'll try an Ubuntu VM on it say Ubuntu 12.04 64 Bit and see if it does the same as Ubuntu 12.10 64 bit beta-1

---

### Post by CharlesA on 2012-09-19
I am using VirtualBox on both machines.

One is running Windows 7 x64 and the other is running 12.04 x64. The Ubuntu box is an i7 and the Windows box is an i5 laptop.

---

### Post by afz12 on 2012-09-19
Thanks for the info CharlesA. The topic is quite interesting. As an experiment I made a XP VM on this notebook (hp i5 4-core running Ubuntu 12.04 and once updated etc I exported it to a USB drive. I then used another notebook (Acer 5920 i3 dual core) running Mint Cinnamon  and an Ubuntu version of Virtualbox to import this VM from the USB drive. Everything went fine except that Internet access didn't work in this VM (confirming a report by a previous post on this topic). However all installed programs worked fine, shared folders showed up as expected and the SD card drive also worked fine. As a VM, XP evened opened a picture I had drawn in Inkscape using Ubuntu Inkscape! Apparently some things just seem to work we we think they should not :)

---

