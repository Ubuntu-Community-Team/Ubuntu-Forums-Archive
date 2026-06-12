---
title: "Router on USB Flash Memory"
date: 2008-08-05
forum: The Cafe
---

### Post by tcpip4lyfe on 2008-08-05
I've been running IPcop as a router for 3 or 4 years now and my hard drive is getting really loud as it wears out.  I've been looking at installing IPcop or Smoothwall or (some other easy to use distro) on a USB thumb drive but I can't find any good documentation on how to do it.  I did find a German How-to on creating a IPcop image and dd'ing it to the flash drive but it's not booting correctly in my PC and it's in German so it's kind of hard to follow.  

Does anyone know of any Linux router distros that install to USB stick or does anyone have any other ideas on how I can make my IPcop box silent?

---

### Post by mips on 2008-08-05
[http://blog.myfenris.net/?p=366](http://blog.myfenris.net/?p=366)

---

### Post by tcpip4lyfe on 2008-08-05
> **mips said:**
> [http://blog.myfenris.net/?p=366](http://blog.myfenris.net/?p=366)

Damn I've been googling for 3 days and haven't seen this.  I'll give it a shot.  Thanks.

---

### Post by ssam on 2008-08-05
not all BIOSs can boot from USB.

one solution is to use compactflash. the compactflash interface is the same as IDE, so all you need is a cheap adapter that has the right size connecters. I run a mini-itx machine like this.

---

### Post by tcpip4lyfe on 2008-08-05
Yeah I've read read about the compact flash interfaces.  I want at least a gig of space to move around in so I'll have to research the adapter and flash sizes.  The previous link worked great for putting the install CD of IPcop but when I tried installing it I got a "no hard drives found."   I think CF is the right way to go because I can just set it as /dev/hda when I get it.

---

