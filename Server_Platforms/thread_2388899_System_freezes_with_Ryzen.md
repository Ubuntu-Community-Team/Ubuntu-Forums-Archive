---
title: "System freezes with Ryzen"
date: 2018-04-09
forum: Server Platforms
---

### Post by mattiash on 2018-04-09
Hello all!
I built a new server last week with these parts:
ASUS PRIME B350-PLUS
AMD Ryzen 5 1400 3.2 GHz 10MB
MSI GeForce GT 710 2GB LP
Crucial 16GB (2x8GB) DDR4 2400MHz CL16 Ballistix
I also got a noname PCI SATA card installed.


I installed Ubuntu Server 17.10.1 on a 2,5" drive, in the case I got 6 2TB drives setup as RAID6 using btrfs as its filesystem.
All is updated to the latest thought apt update.

When I start the machine, it starts, shuts itself down and starts again as it should do, everything looks fine everything mounts and I can login.
The only app so far installed is Plex Media Server.

So far I have no idea the time that passes before the machine freezes.
I havn't been able to see anything in any logs telling me what is up.
Did some googling and C-state was mentioned, so I turned that off and set the boot options to Normal Boot.
Turned off any overclocking. Still no luck.

So now I turn to you guys - what do I need to do?

---

### Post by QIII on 2018-04-09
Hello!

Windows users often share your pain, so the Linux community is not alone.

When was your board manufactured and what is the installed BIOS?  Have you updated it to the most recent?

---

### Post by mattiash on 2018-04-09
Yes I have updated to the latest, that I did before I installed anything.

---

### Post by mattiash on 2018-04-10
It was no software error... it was hardware. An easy sort of error too. The PCI card with 2 extra SATA connection was broken.

---

