---
title: "LVM Disk Failure"
date: 2009-02-13
forum: Server Platforms
---

### Post by wh1terabb1t on 2009-02-13
Hello,

I currently have an Ubuntu 8.10 server with a 5 disk LVM setup.  Recently one of the disks failed that contains a LVM partition. However, this particular drive does not seem fully dead since I recovered one of the other partition from it yesterday. None the less, I still cannot distribute the drives LVM contents to the rest of the VG. When I run "pvmove /dev/sde2" I receive the following error:

```

File descriptor 3 left open
File descriptor 4 left open
File descriptor 6 left open
File descriptor 7 left open
  Insufficient free space: 6985 extents needed, but only 42 available
  Unable to allocate temporary LV for pvmove.

```

Oddly enough, the LVM has 215 gigs free and this drive can only contain a max of 30 gigs of LVM space.  Also, the VG fails to mount stating resulting in: "wrong fs type, bad option, bad superblock, or other error."  Does anyone have any solutions aside from putting in another hard drive (the box is a bit out of reach physically)?

I appreciate any feedback in advance,
Andrew

---

