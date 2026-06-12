---
title: "Ubuntu Studio doesn't detect sound or network card"
date: 2011-10-16
forum: Ubuntu Studio
---

### Post by Drakmor on 2011-10-16
Hey all, I've been struggling with Ubuntu studio for the greater part of today, and I still don't have it working. I tried 10.04 first because I thought it was the most recent one with a realtime kernel, but when I tried installing it it didn't detect my integrated sound card (An intel HDA card on a ASUS P8Z68-V PRO mobo), though it did detect my usb headset. It also didn't detect the intel ethernet card on the same mobo. After some conversations on the irc I tried installing 10.10, but got pretty much the same thing. However, when it didn't detect my network hardware I tried to go into the expert mode and set it manually, but it did nothing when I selected it. 

I know the sound and network card works because I'm running another install of kubuntu on it right now, and everything's fine. Thanks in advance!

---

### Post by sgx on 2011-10-16
> **Drakmor said:**
> Hey all, I've been struggling with Ubuntu studio for the greater part of today, and I still don't have it working. I tried 10.04 first because I thought it was the most recent one with a realtime kernel, but when I tried installing it it didn't detect my integrated sound card (An intel HDA card on a ASUS P8Z68-V PRO mobo), though it did detect my usb headset. It also didn't detect the intel ethernet card on the same mobo. After some conversations on the irc I tried installing 10.10, but got pretty much the same thing. However, when it didn't detect my network hardware I tried to go into the expert mode and set it manually, but it did nothing when I selected it. 

I know the sound and network card works because I'm running another install of kubuntu on it right now, and everything's fine. Thanks in advance!
Hi, all the same audio apps will work in kubuntu, mint ubuntu etc
Take advantage of your good fortune, and use what works. :popcorn:
Any apps not in the main ubuntu repositories, can be found in falk and autostatic PPAs, or debian/tango unstable audio repositories, or google

[http://packages.debian.org/unstable/sound/](http://packages.debian.org/unstable/sound/)

[http://download.tuxfamily.org/tangostudio/dists/lucid-unstable/main/binary-i386/sound/](http://download.tuxfamily.org/tangostudio/dists/lucid-unstable/main/binary-i386/sound/)

[https://launchpad.net/~autostatic/+archive/ppa](https://launchpad.net/~autostatic/+archive/ppa)

Cheers

---

### Post by Drakmor on 2011-10-16
Thanks for the response! I already have a lot of the studio apps on my current install, but the main reason I am trying to add studio is so I can get a low latency kernel.  From what I read, I was under the impression that one didn't exist for 11.04, but if you could show me how to set one up on here, I'd be fine with using that instead of installing Studio.

---

### Post by sgx on 2011-10-17
Hi, some official docs are here

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

a link to liquorix kernel, and a discussion is here:

[http://linuxaudio.org/mailarchive/lau/2011/1/7/177380](http://linuxaudio.org/mailarchive/lau/2011/1/7/177380)

and more RT install info here:

[http://wiki.linuxmusicians.com/doku.php?id=system_configuration](http://wiki.linuxmusicians.com/doku.php?id=system_configuration)
Cheers

Debian rt kernels will likely work in what you have. I used one
in Macpup to make a fast tiny audio setup. Just used

sudo dpkg -i to install the kernel package and headers package.
Cheers

---

