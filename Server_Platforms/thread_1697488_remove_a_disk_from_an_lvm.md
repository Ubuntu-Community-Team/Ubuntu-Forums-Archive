---
title: "remove a disk from an lvm?"
date: 2011-02-28
forum: Server Platforms
---

### Post by SchnowdaPowda on 2011-02-28
ok on my file server i am trying to replace a small 30gb disk with a larger one i just purchased. i need to find a way to backup the data on it to another part of the lvm and then remove it hopefully with the backup and the rest of my data intact. possible?

---

### Post by dtfinch on 2011-02-28
If you add the new disk to the lvm group, you can run pvmove against the old disk/partition, and it'll move all the data to the new disk.

If your old disk is also your boot disk, you'll have to do a bit more, like installing grub to the new disk, and if there's a non-LVM boot partition, it needs to be copied exactly, like with dd, so that the uuid is the same for grub and such.

---

### Post by SchnowdaPowda on 2011-03-01
so the fourth drive was just put in so it should be empty. pvmove returns an error about insufficient free space. 

```
j@serve:~$ sudo pvmove /dev/sdb1 /dev/sdc1
  Insufficient free space: 447 extents needed, but only 9 available
  Unable to allocate mirror extents for pvmove0.
  Failed to convert pvmove LV to mirrored
```

and i tried vgreduce for the hell of it and i got this with the volume mounted and not mounted

```

j@serve:~$ sudo vgreduce data /dev/sdb1
[sudo] password for j:
  Physical volume "/dev/sdb1" still in use

```

---

### Post by dtfinch on 2011-03-01
What does pvdisplay say?

---

### Post by SchnowdaPowda on 2011-03-01
sorry i fell asleep for awhile.. its around 3am here. this is the output you requested thanks for the help.

```
j@serve:~$ sudo lvdisplay
[sudo] password for j: 
  --- Logical volume ---
  LV Name                /dev/data/1
  VG Name                data
  LV UUID                W6nhtL-0hZc-fndk-CTya-fjxl-odX8-PXSoOE
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                462.00 GB
  Current LE             7392
  Segments               4
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   

```

---

### Post by SchnowdaPowda on 2011-03-01
sorry you meant this fyi /dev/sdi is a usb external so n/a 

```
 j@serve:~$ sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/sda2
  VG Name               data
  PV Size               169.50 GB / not usable 1.46 MB
  Allocatable           yes (but full)
  PE Size (KByte)       65536
  Total PE              2712
  Free PE               0
  Allocated PE          2712
  PV UUID               70E87u-DQ0X-E1f3-bPWL-DtWa-KG3g-z1bhH2
   
  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               data
  PV Size               27.95 GB / not usable 15.59 MB
  Allocatable           yes (but full)
  PE Size (KByte)       65536
  Total PE              447
  Free PE               0
  Allocated PE          447
  PV UUID               3Djg2c-VxEU-s6IJ-yxe4-8DmE-nv6A-wkR54R
   
  --- Physical volume ---
  PV Name               /dev/sdd1
  VG Name               data
  PV Size               111.81 GB / not usable 62.47 MB
  Allocatable           yes (but full)
  PE Size (KByte)       65536
  Total PE              1788
  Free PE               0
  Allocated PE          1788
  PV UUID               EAZwyQ-3byR-GKlZ-xwhU-Mopg-np2e-jO9Axd
   
  --- Physical volume ---
  PV Name               /dev/sdc1
  VG Name               data
  PV Size               153.38 GB / not usable 9.15 MB
  Allocatable           yes 
  PE Size (KByte)       65536
  Total PE              2454
  Free PE               9
  Allocated PE          2445
  PV UUID               WOBxH2-JKcp-RSAi-o6Q5-kUTB-iXy3-TX2F2d
   
  "/dev/sdi1" is a new physical volume of "465.76 GB"
  --- NEW Physical volume ---
  PV Name               /dev/sdi1
  VG Name               
  PV Size               465.76 GB
  Allocatable           NO
  PE Size (KByte)       0
  Total PE              0
  Free PE               0
  Allocated PE          0
  PV UUID               nlGYer-rECX-xXgq-ZsGw-Fqjg-9cul-6Hpu1h
```

---

### Post by dtfinch on 2011-03-01
If you've already extended your logical volume onto the new disk then there's no free space to move it off the old disk.

You'd have to shrink your logical volume (after unmounting and shrinking your filesystem if you grew that already) back down to make enough room on the new disk. And this would be a good time to backup important files first if you haven't yet.
[http://blog.shadypixel.com/how-to-shrink-an-lvm-volume-safely/](http://blog.shadypixel.com/how-to-shrink-an-lvm-volume-safely/)

---

### Post by SchnowdaPowda on 2011-03-01
ok so i got this nasty error message 
```
j@serve:/$ sudo e2fsck -f /dev/data/1
e2fsck 1.41.9 (22-Aug-2009)
The filesystem size (according to the superblock) is 121241600 blocks
The physical size of the device is 121110528 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes

```
do you think i should just back up and start over?  i think it might be a little easier at this point.

---

### Post by dtfinch on 2011-03-02
So your original logical volume is exactly 462gb, but your filesystem is exactly 462.5gb, with the last 512mb cut off. Was it always on LVM or did you move it to LVM from elsewhere? It could have been truncated for a while, and you just never had any files placed there, or the errors went unnoticed.

You do have 9 extents (576mb) free on sdc1 if you want to try to extend the logical volume by 512mb ("lvextend -L+512M /dev/data/1 /dev/sdc1" I think) to match the filesystem and then retry the fsck (making sure the volume isn't mounted).

And making a backup if you haven't already is a good idea of course.

Edit: Also, earlier I assumed that sdc was your new disk intended to replace sdb, and that you might have accidentally extended the logical volume when you added it, but now I think I was mistaken and maybe you haven't plugged in the new disk yet. Are you trying to remove sdb first so that you have a free 4th port to plug the new drive into?

Edit 2: You really should consider switching to a redundant raid at some point. Right now if one disk died the whole volume would be lost, and 1tb drives are pretty cheap.

---

