---
title: "Is it possible to install Ubuntu on (32 bit) Sparc Station 20?"
date: 2007-07-18
forum: Sun Sparc Users
---

### Post by chris_andrew on 2007-07-18
Hi,

Anyone know if it's possible to install Ubuntu on a 32 bit SS20?

Cheers,

Chris.

---

### Post by mips on 2007-07-20
I dont see why not. Try google and see if others have done it.

---

### Post by benx009 on 2007-07-21
may be possible, but you'd have to be running an older version of ubuntu for sure (like ubuntu 5.04, maybe even older) for it to work since its cpu is so slow.

just curious, do you actually have a [SS20]("http://en.wikipedia.org/wiki/SPARCstation_20")?

---

### Post by Arwen on 2007-07-23
OMG I thought only univerisities have such pcs..Anyway as you can see in the link of benx009 it can run a lot of distros but it's a quite slow computer.(I hope it does ,that solaris thing is creepy :-P :-D)

---

### Post by Bored_Kiwi on 2007-07-23
You would be better off with NetBSD as just about anything esle modern will be far too slow.

---

### Post by chris_andrew on 2007-09-24
Still trying to find out if anyone has installed Ubuntu on an SS20. It would be great to get it working :-).

Anybody?

Cheers,

Chris.

---

### Post by KCPokes on 2007-09-24
Your biggest issue is going to be whether the SCSI controllers are identified as everything in a Sparc station is SCSI based.  Wasn't until the Ultra series that they moved more to the IDE drives for workstations.  Your next hurdle will be video as you are talking about an ancient graphics card.  Best case would be a headless server to achieve anything useful.

---

### Post by mips on 2007-09-25
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/sparc/hardware-supported.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/sparc/hardware-supported.html)

Why don't you just try Ubuntu on it, might want to go with a lightweight WM thoug.

---

### Post by Moulton on 2007-10-20
I run Debian Sparc on the 32-bit Sun 4m machines.  This runs OK, and even supports the GUI desktop if you use XFCE.  Don't bother with KDE or Gnome on those machines.

To the best of my knowledge, there is no version of Ubuntu for the 32-bit Sun 4m platform.

As far as I know, Ubuntu for the Sparc only runs on the Sparc 64 (e.g. Sparc Ultra and newer) models.

You can also run NetBSD or OpenBSD on the Sparc 5/10/20 platforms.

---

