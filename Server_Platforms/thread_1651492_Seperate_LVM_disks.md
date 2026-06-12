---
title: "Seperate LVM disks"
date: 2010-12-23
forum: Server Platforms
---

### Post by ene_dene on 2010-12-23
Hello, I have two partitions from 2 hardisks that I put to one with lvm2.
```
sudo pvdisplay
[sudo] password for me: 
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               lvm
  PV Size               465.76 GiB / not usable 1.47 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              119234
  Free PE               0
  Allocated PE          119234
  PV UUID               uIDOQk-LVoy-G6No-UIXp-647q-hfQK-UydeBN
   
  --- Physical volume ---
  PV Name               /dev/sdb5
  VG Name               lvm
  PV Size               465.78 GiB / not usable 1.03 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              119240
  Free PE               0
  Allocated PE          119240
  PV UUID               eMSj3X-uqgL-2PLX-fYhX-3zTU-pNey-X7oWUH

```

One of the disks has starting dying so I want to separate them. How do I do that?

---

### Post by craigp84 on 2010-12-23
```
$ pvmove /dev/dead_disk /dev/happy_disk
$ pvremove /dev/dead_disk
```

---

### Post by dtfinch on 2010-12-23
First you need to free up about 500gb of space. You can shrink your filesystem, then shrink the logical volume (but slightly larger than the filesystem), small enough to fit on one drive, like described [here](http://blog.shadypixel.com/how-to-shrink-an-lvm-volume-safely/). Or you can add a third disk of equal or bigger size (like pvcreate /dev/sdc1 (or whatever the new partition is, then vgextend nameofvolumegroup /dev/sdc1).

Next you would do "pvmove /dev/sdb5" (if sdb5 is on the dying disk), which would tell lvm to try to move all extents on that disk to the other disks, which may take a long time, though I've never done it before. Then "vgreduce nameofvolumegroup /dev/sdb5" to take the drive out of the volume group.

---

### Post by psusi on 2010-12-23
Yes, pvmove will get everything off of the dieing disk, but you need space to move it to, which you don't seem to have.

---

### Post by ene_dene on 2010-12-23
> **psusi said:**
> Yes, pvmove will get everything off of the dieing disk, but you need space to move it to, which you don't seem to have.

The problem is that the drives are Truecrypted so it looks like they are full. I don't care about the data, because this is my backup disk, the original data is safe, but I need to get it running soon because I'm in danger if my main disk dies too.

I can't even delete data, something is wrong with that disk.
I get this error:
```
my@comp:/media$ sudo pvremove -ff /dev/sda5
  /dev/sda5: read failed after 0 of 2048 at 0: Input/output error
  No physical volume label read from /dev/sda5
  Can't open /dev/sda5 exclusively - not removing. Mounted filesystem?
my@comp:/media$ sudo pvremove /dev/sda5
  /dev/sda5: read failed after 0 of 2048 at 0: Input/output error
  No physical volume label read from /dev/sda5
  Physical Volume /dev/sda5 not found
```
Disks are not mounted.
Is there some primitive way I could get it done, by deleting partitions somehow, of formating? Data is safe.

---

### Post by psusi on 2010-12-23
It looks like the data on that drive is gone.

---

### Post by ene_dene on 2010-12-23
> **psusi said:**
> It looks like the data on that drive is gone.

Yes it's probably gone, I just want to separate the disks so I can use the other disk that is OK.

---

### Post by psusi on 2010-12-23
> **ene_dene said:**
> Yes it's probably gone, I just want to separate the disks so I can use the other disk that is OK.

vgreduce --removemissing --force should do the trick.

---

### Post by ene_dene on 2010-12-23
> **psusi said:**
> vgreduce --removemissing --force should do the trick.
This is what I get:
```
sudo vgreduce --removemissing --force lvm
  Volume group "lvm" is already consistent
```
pvscan still gives:
```
sudo pvscan
  PV /dev/sda5   VG lvm   lvm2 [465.76 GiB / 0    free]
  PV /dev/sdb5   VG lvm   lvm2 [465.78 GiB / 0    free]
  Total: 2 [931.54 GiB] / in use: 2 [931.54 GiB] / in no VG: 0 [0   ]

```
Also this gives:
```
sudo vgreduce -a --force lvm
  Physical volume "/dev/sda5" still in use
  Physical volume "/dev/sdb5" still in use
```
But the disk is not mounted. Could it be that it has something to do with truecrypt? I haven't mounted the disk anyway.
Here are the devices that have something to do with this lvm disks:
/dev/mapper/lvm-lvmdisk
/dev/lvm/lvmdisk

---

