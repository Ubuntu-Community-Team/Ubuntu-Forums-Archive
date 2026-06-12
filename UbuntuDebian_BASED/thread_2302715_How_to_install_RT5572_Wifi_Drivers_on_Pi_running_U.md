---
title: "How to install RT5572 Wifi Drivers on Pi running Ubuntu"
date: 2015-11-12
forum: Ubuntu/Debian BASED
---

### Post by cake_bob on 2015-11-12
How do i install drivers onto my rpi?

So far ive managed to use ```
wget -O RT5572.tar.bz2 http://cdn-cw.mediatek.com/Downloads/linux/DPO_RT5572_LinuxSTA_2.6.1.3_20121022.tar.bz2
``` And ive used ```
tar xvjf RT5572.tar.bz2
``` So far all i have achieved is downloading the file and decompressing it. How do i now install this driver into the os so that it appears when i run the command ```
lsmod
```

I'm trying to turn my Rpi into a wireless AP passing the ```
wlan0
``` traffic through ```
eth0
``` so far everything works apart from the driver which is required. My device ID is 148f:5370 - Ralink Tech Corp. RT5370

The drivers I'm trying to download are suppost to support the RT5370 wifi dongle stick. 

This is the driver package I'm trying to install/use [ATTACH]265526[/ATTACH]

---

### Post by cake_bob on 2015-11-16
Bump

---

### Post by Vladlenin5000 on 2015-11-16
Hi and welcome.

What Ubuntu version are you running exactly?
RT5370 is natively supported since a long time ago. The drivers version you're trying to install were made for 2.4 and 2.6 kernel lines only.

---

### Post by cake_bob on 2015-11-26
Hi, sorry but it turns out i was running Raspian Jessie not a distro of Ubuntu
The reason for this thread was because I was trying to set up a WiFi AP on my Raspebrry Pi. I ran into problems when I needed to set up a driver to use for this dongle. I tried using all of the drivers that were built-in individually, but I had no luck.

We are now in the process of creating a **WIRED** Media Center with Kodi Helix. 
Thank you for your time Vladlenin5000

Cheers cake_bob

---

### Post by howefield on 2015-11-26
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

