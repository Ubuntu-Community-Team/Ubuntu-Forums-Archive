---
title: "[SOLVED] Slack installation with EIDE(ata 6) DVD-ROM"
date: 2008-04-08
forum: Slackware and derivatives
---

### Post by dynamethod on 2008-04-08
Hi there,

Heres my scenario, ive downloaded the slackware v.12 iso(everything) and burnt as an image on a DVD with my DVD-ROM thats connected to my logic board via EIDE(ata-6).

My hardware:

Asus P5K SE Motherboard
Marvell 88SE6111 IDE Controller
1 x SATA-2 HD
1 x EIDE(DVD-ROM device connected)

Ive successfully booted the image, and loaded the kernel(hugesmp.s)

Partitioned the space on my (only) Hard drive being a SATA-2 connection

Ive entered the setup interface, and got as far as selecting the source media

However slack cannot detect my DVD-ROM with the image(which i assume contains the source media)

I've read elsewhere that the Marvell IDE controller is problematic, so i passed this option to the kernel when i boot = "hugesmp.s all-ide-generic"
But that does not help either.

so im stuck at this point, any advice much appreciated

---

### Post by digger95 on 2008-04-08
Sorry to hear you are having trouble.  I used the cd-rom so I can't help you.  I would ask your question at the official Slackware forums as you will get a much quicker response there.

[http://www.linuxquestions.org/questions/slackware-14/](http://www.linuxquestions.org/questions/slackware-14/)

Dig

---

### Post by dynamethod on 2008-04-09
Well i managed to install ok after i found a work around, i just extracted the slackware dir from the image and placed it on the winxp partition at c:/, so that worked ok.

But slack still doesnt recognise my DVD-ROM as yet, which kinda sucks cause i use it quite often

---

### Post by dynamethod on 2008-04-14
solved, just downloaded the lastest Kernel that being 2.6.24.4-smp
and ran upgradepkg

now DVD-ROM works fine

---

