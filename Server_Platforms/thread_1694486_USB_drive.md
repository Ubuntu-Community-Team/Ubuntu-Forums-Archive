---
title: "USB drive"
date: 2011-02-24
forum: Server Platforms
---

### Post by brand1068 on 2011-02-24
Hiya, Be Gentle with me...
 
I'm trying to copy a file from our newly setup Unbuntu server....
 
When I put the USB stick into the server I get the following output from the sudo fdisk -l
 
Disk /dev/sdb: 4005 MB, 4005527552 bytes
32 heads, 63 sectors/track, 3880 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f314df5
Device Boot Start End Blocks Id System
/dev/sdb1 1 3880 3911008+ b W95 FAT32
 
But if I cd /dev/sdb1 I get -BASH not a directory
 
Tried a few searches but nothing came up..
 
Cheers in advance.
 
Chris

---

### Post by howefield on 2011-02-24
Try looking in /media for your USB drive.

---

### Post by brand1068 on 2011-02-24
Nope, Nothing in media.
 
though that drive does disapear / reappear if I remove the USB stick.
 
Chris

---

### Post by dtfinch on 2011-02-24
Maybe try (as root):
mkdir /media/usbdrive
mount -t vfat /dev/sdb1 /media/usbdrive
cd /media/usbdrive

---

### Post by brand1068 on 2011-02-25
Thats a winner :)
 
Thanks Mate.
 
Chris

---

