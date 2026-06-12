---
title: "=-=Raspberry-PI=-="
date: 2012-07-18
forum: The Cafe
---

### Post by rk0r on 2012-07-18
Hi

Just ordered a "Raspberry Pi" has anyone managed to get their hands on one ?
If you have a " Raspberry-PI"  what OS are you using ?

I hope that Ubuntu will be available for the Raspberry in the future, if anyone is developing or hacking away to get it working post us a link  :)

---

### Post by rg4w on 2012-07-18
My understanding is that the Pi is able to keep costs down by using a version of ARM too low to run Ubuntu.  At least that's the official word from Canonical; I've stumbled across accounts of some who claim to have run Ubuntu on Pi, but I don't recall which version.

If you're able to get Ubuntu running on it please let us know.

---

### Post by sanderj on 2012-07-18
> **rk0r said:**
> Hi

Just ordered a "Raspberry Pi" has anyone managed to get their hands on one ?
If you have a " Raspberry-PI"  what OS are you using ?

I hope that Ubuntu will be available for the Raspberry in the future, if anyone is developing or hacking away to get it working post us a link  :)

Yes, I've got a Raspi.

I'm running Debian Wheezy on it.

No, it won't run Ubuntu: recent Ubuntu's require ARMv7 family CPU, and the Raspi has an ARMv6 familiy CPU (an ARM11). Furthermore, the Raspi only has 256MB RAM ... too little for Ubuntu 12.04


FYI: 
the Raspi is great with command line Debian
the Raspi is a bit slow running X (xfce window manager?). It has the Midori webbrowser, which does not do HTML5 AFAIK. Running Firefox is quite hard, I don't know if Chromium is available.
the Raspi does not do flash.

In other words: the Raspi is great device, but don't expect it to replace your 4GB 3Ghz super-duper monster machine

---

### Post by aerojh on 2012-07-18
I have three, all using Arch. I'm using them mostly as an embedded platform where I'd like a full embedded Linux install.

I would much rather that the Raspberry Pi people made cuts elsewhere to allow for an ARM v7 CPU, but for a $35 Linux box I'm not complaining. It's certainly cheaper than a Gumstix.

---

### Post by mechanismnine on 2012-07-18
from what i understand you can get rasbian (debian for the pi) ferdora and a version of android

---

### Post by aerojh on 2012-07-18
> **mechanismnine said:**
> from what i understand you can get rasbian (debian for the pi) ferdora and a version of android

Their [downloads page](http://www.raspberrypi.org/downloads) offers images for Raspbian, Arch, and QtonPi (some embedded Linux for Qt 5 dev, not sure what it's based on.).

---

### Post by epikvision on 2012-07-18
Quite a promising system for its ultraportability.  If it won't run ubuntu, I'll consider for some other time.

---

### Post by pe7er on 2012-07-18
> **sanderj said:**
> I'm running Debian Wheezy on it.

No, it won't run Ubuntu: recent Ubuntu's require ARMv7 family CPU, and the Raspi has an ARMv6 familiy CPU (an ARM11).
Raspbian “wheezy” is Debian optimized for the Raspberry Pi: [http://www.raspberrypi.org/archives/1605](http://www.raspberrypi.org/archives/1605)

> **aerojh said:**
> I have three, all using Arch. I'm using them mostly as an embedded platform where I'd like a full embedded Linux install.
I have one device, but multiple SD Cards that are easy to switch:
One with OpenELEC (a XBMC mediacentre) which I compiled from source (took 6 hours, only to find out later that there's a binary for the RP available :D) and
the other has Arch Linux (ArchLinuxARM) with only OpenSSH (no GUI).

---

### Post by Bucky Ball on 2012-07-18
Enjoy the wait. I started a thread about this already you may be interested in:

[http://ubuntuforums.org/showthread.php?t=2021289](http://ubuntuforums.org/showthread.php?t=2021289)

You'll find plenty of info about what people are doing with the RP there ...

---

