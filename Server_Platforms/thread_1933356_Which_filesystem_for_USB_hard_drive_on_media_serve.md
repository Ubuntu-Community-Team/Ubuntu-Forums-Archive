---
title: "Which filesystem for USB hard drive on media server?"
date: 2012-02-29
forum: Server Platforms
---

### Post by neufena on 2012-02-29
Hi,

I use an old netbook (with a broken lcd) as a small home server.  It only really serves 3 functions:

Sharing a USB Hard drive with Samba
Running Twonkyserver for media playback on my Xbox 360
Sharing my printer and scanner.

The USB hard drive is one I've had for a long time, is formatted with FAT32 (from before it's use with the server) and is almost full.  The time has come to buy a much bigger one (2TB) and since I'm getting to start this drive from scratch my attention has turned to filesystems.  My choice seems to come down to these 4, any advice or suggestions as to which would be best for my purpose?

Ext4
BtrFS
XFS
ZFS

Thanks,

---

### Post by rubylaser on 2012-02-29
Of the one's you listed, I'd use them in this order:
1. Ext4 - On something that size with no redundancy.  It's proven, portable and works very well.  
2.  ZFS - This is fantastic too and with a native port, it works great in Linux.
3. XFS - I've had nothing but problems with this filesystem over time (file corruption).  Personally, I never use this anymore.
4. BtrFS - This has some great features (COW, snapshots, etc), but still isn't ready for production (filesystem corruption and no fsck).  So, at this point, I wouldn't even consider using it.

---

### Post by neufena on 2012-02-29
I'll go with Ext4 then, just wondered if there was a better choice out there.

---

### Post by rubylaser on 2012-02-29
Good choice :)  There's a good reason that it's the default filesystem.

---

