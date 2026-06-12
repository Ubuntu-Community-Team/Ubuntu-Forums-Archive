---
title: "Please help, Ubuntu server 17.10 No Network interfaces"
date: 2017-12-13
forum: Server Platforms
---

### Post by majesticunicorns99 on 2017-12-13
I have just installed ubuntu server on a Dell Poweredge 2650, ubuntu cannot see the network interfaces, the onboard ethernet cards (intel Pro 10/100/1000) the usb cards (Tp Link TL-WN722N) I used this to install the OS. Or another, Ralink something or other both of which is causing hangs on the boot, or loops with the TP-Link card. This is very annoying, every effort I've tried to get this server online has been shot down in flames.

System configurations - 

Single Xeon 3.06GHz
2GB ECC Memory
5x 36GB SCSI harddrives
Remote management module

Thats about it, can anyone help me? 

(probably posted in the wrong place, apologies if I did)

Reinstalled with DVD, after finding a compatible one, network adapter causing issues with boot still, ethernet isn't visible still at this point I have tried everything. I am new to ubuntu but not new to debian, this has puzzled me

Reinstalled multiple times, same issues. ath9k cannot start HTC services, trying CentOS now..

---

### Post by howefield on 2017-12-13
Thread moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2017-12-13
During install there is a step to set up the networking. Does it detect any adapters there? That is an easy way to tell if it can detect your NICs even before you continue installing it.

If it doesn't detect the NICs that is a sign they will not be detected even after installing.

---

### Post by majesticunicorns99 on 2017-12-13
Says something about needing additional software? Run the 'discovery' a few times and the wifi adapters pop up, then they work fine, no isses whatsoever, after installations tho, wifi adapters stop working entirely, ubuntu sees on the lsusb and that about it, I tried adding the ethernet manually too, still to no avail. CentOS is having the same issues, works fine on live and install, after install all networks stop working.

it must see them on install because they work..?

Many thanks for help

---

### Post by darkod on 2017-12-13
"Works on live"? You are installing Ubuntu Server, right? That has no live CD option.

Also, have you tried with a LTS version like 16.04 instead of 17.10?

For a server I would never use wifi, so I would focus on the ethernet ports. If it says they need additional software then they probably need a driver. You need to get the model and chipset and then search for drivers.

---

