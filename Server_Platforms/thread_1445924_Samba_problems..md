---
title: "Samba problems."
date: 2010-04-03
forum: Server Platforms
---

### Post by twin-08 on 2010-04-03
Hey guys, I had a few problems with samba to config it to a second hard drive which was on a raid card, as my primary drive is an ide drive.

I installed a gui and for the path to the second hard drive last night which all worked fine, I tried to remove the gui which failed so I went to my self lets just format and set it up again.

After doing that and getting webmin installed, I went to config samba like what I done before, went to the media folder and there was no second hard driver there, this is the problem that I am having with this as it was working last night.

Anyways heres the fdisk info just incase you need it.

```
Disk /dev/sda: 40.0 GB, 40037760000 bytes
255 heads, 63 sectors/track, 4867 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8cfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4836    38845138+  8e  Linux LVM
/dev/sda2            4837        4867      249007+   5  Extended
/dev/sda5            4837        4867      248976   83  Linux

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
16 heads, 63 sectors/track, 1240341 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x79789ada

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               3     1240339   625129472    7  HPFS/NTFS
twin@linux-server:~$

```

---

### Post by ubername on 2010-04-03
You don't mention the rest of the network you will be using to access the samba shares you are struggling to create. Can you provide a bit more info please?

---

### Post by twin-08 on 2010-04-03
> **ubername said:**
> You don't mention the rest of the network you will be using to access the samba shares you are struggling to create. Can you provide a bit more info please?

I will be having a share on the second hard drive for a windows network of two computers. The share will only be used as a file storage for backups and hosting movies/music.

I had it working last night, now today after I formated it to keep the gui off it has seemed to mess up again.

Thanks, Twin

---

### Post by Vegan on 2010-04-03
That CHS report is sure out of date. my disks are LBA and they respond to LBA requests fine.

---

### Post by twin-08 on 2010-04-03
Im, sorry but I don't understand what you mean.

---

