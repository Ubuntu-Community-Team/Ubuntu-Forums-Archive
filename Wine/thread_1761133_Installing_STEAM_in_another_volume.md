---
title: "Installing STEAM in another volume"
date: 2011-05-17
forum: Wine
---

### Post by MGN001 on 2011-05-17
As a gamer, I absolutely LOVE Steam.  However, there's not enough room to install to wine's virtual C drive (well, I can't download games to it as well).  I want to install Steam in another, larger partition I've decided to dedicate to it.  Is there a way to install Steam to this partition?

---

### Post by bobwyajnr on 2011-05-19
> **MGN001 said:**
> As a gamer, I absolutely LOVE Steam.  However, there's not enough room to install to wine's virtual C drive (well, I can't download games to it as well).  I want to install Steam in another, larger partition I've decided to dedicate to it.  Is there a way to install Steam to this partition?

Yeh you can create a WINEPREFIX folder in the other partition and install Steam to that. Just make sure the WINEPREFIX folder on the other partition has R/W permissions for your user account (since WINE should never be run as root). Also the filesystem on the other partition needs to be native Linux (no NTFS for example that uses a userspace FUSE driver - that breaks stuff).

Personally I have my whole **/home** partition on a separate drive (from my **/** root partition). Makes upgrading your distro a bit easier! It's also give slightly faster (since the harddisk latency of each drive can overlap each other).:cool:

I would carefully read the [WINE FAQ]("http://wiki.winehq.org/FAQ") and [WINE users guide]("http://www.winehq.org/documentation") to get a good understanding of how WINEPREFIX's are used and what not to do!

It's generally considered a good idea to install different applications in different WINEPREFIX's. Say you have all you Steam games installed in a WINEPREFIX on machine A you can move that whole (intact) WINEPREFIX folder to machine B and get the games to run still (well apart from missing icons, desktop shortcuts, etc. which are often stored outside of the WINEPREFIX folder - in the usual Ubuntu places :o) )

Bob

---

