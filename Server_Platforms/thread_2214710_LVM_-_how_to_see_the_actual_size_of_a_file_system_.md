---
title: "LVM - how to see the actual size of a file system within an lv"
date: 2014-04-02
forum: Server Platforms
---

### Post by frankerooney on 2014-04-02
Hi All,
  Very quick question - how do I see the size of the filesystem within a logical volume (lvm2) without mounting it? I can obviously mount /dev/vgname/lvname and look at the output of df -h, but I'd like something I can see offline..
fdisk doesn't like the filesystem, it complains about it and can't see any details.
Thanks
Andy

---

### Post by frostschutz on 2014-04-02
Well, only the filesystem itself knows, so you have to use some tool that is aware of that specific filesystem's internals (like tune2fs, fsck, ...) and see if any of those tell you about its size.

There is no generic solution.

---

### Post by bab1 on 2014-04-02
> **frankerooney said:**
> Hi All,
  Very quick question - how do I see the size of the filesystem within a logical volume (lvm2) without mounting it? I can obviously mount /dev/vgname/lvname and look at the output of df -h, but I'd like something I can see offline..
fdisk doesn't like the filesystem, it complains about it and can't see any details.
Thanks
Andy
```
sudo parted -l 
```  That's an 'ell' not a one.

---

### Post by frankerooney on 2014-04-03
Thanks for the replies. I'll mess with tune2fs, fsck etc. Interestingly parted also gives the lv size :

df -h

..
/dev/mapper/vols-share1                    772M  936K  719M   1% /media/test
..

(800MB ext4 partition)

parted -l

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vols-share1: 1074MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1074MB  1074MB  ext4

(~ 1GB lv)

wonder if gparted shows the space as unallocated..? - I'll have to have a play with a desktop edition, on server OS atm.

Thanks
Andy

---

