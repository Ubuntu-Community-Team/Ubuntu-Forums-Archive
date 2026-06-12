---
title: "How much disk space should this take"
date: 2010-06-21
forum: The Cafe
---

### Post by PurposeOfReason on 2010-06-21
All four of my sata ports are going to a RAID5 setup, but all I need is XBMC and rtorrent. I have a 2GB and 4GB flash drive I was going to install Ubuntu on, I'd prefer to use the 2GB, should be enough right?

---

### Post by cariboo on 2010-06-21
IF you are going to make the install persistent 2Gb should work, but 4Gb is always better. :)

---

### Post by PurposeOfReason on 2010-06-21
> **cariboo907 said:**
> IF you are going to make the install persistent 2Gb should work, but 4Gb is always better. :)
Minimal says it only needs 1GB, "lite" takes 2GB, figure I'm hitting in between. :)

---

### Post by PurposeOfReason on 2010-06-21
For the record, it too 1.3Gb. Not too bad, all works fine except xbmc is far too slow. Is there a way to create an iso out of my install then boot that with toram in grub? I have 4GB of RAM in the box, I doubt it'd be a hassle.

Currently reading this.
[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

EDIT - A way to just run /usr/bin/xbmc from ram would be just as welcome.

EDIT2 - Easily the worst way to do this, but I'm currently mounting a /temp tmpfs partition and I copy all of /usr (as it has /usr/lib and /usr/bin which both read a lot) to /temp. Then I mount /usr as a tmpfs and copy from /temp to the now empty /usr. It works, it is fast, but it isn't keeping ownership and permissions. :/ I'll do it again with cp -rp which should work. Not worried about reading in music/video as those are on a plenty fast raid5.

---

