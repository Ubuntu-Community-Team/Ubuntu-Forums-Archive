---
title: "Corrupted LVM with 1 RAID 6 member"
date: 2012-06-26
forum: Server Platforms
---

### Post by Einsteiniac on 2012-06-26
Alright very long story so I hope you have patience.

I setup this RAID 6 array initially using open filer.  They seem to make everything a LVM.  So long story short I have a RAID 6 array of 10 disks that is a member of my 1 LVM.

I realized Openfiler sucks and erased it and went Ubuntu.

The other day the server crashed and now when it boots I have to skip my media raid mount point to get Ubuntu to start.  Once started mdadm reports that the /dev/md0 is good and ready to rock.  However the xfs partition is on the LVM.  So when I type:

mount /dev/media/media /media/RAID

When I type that I get NOTHING.  Just brings the cursor to the line below then freezes.  Top shows the command but no activity to speak of.

If I type:

xfs_check /dev/media/media

or 

xfs_repair /dev/media/media

I get the same as the mount command above just goes to the next line then nothing.

If I try:

xfs_check /dev/mapper/media-media

or 

xfs_repair /dev/mapper/media-media

I get the same results as well.

I would LOVE to get this back and running as I have about 15TB of stuff on there.

I tried to boot off of Slax to repair but realized my RAID card needs drivers to mount the drives to even see if it sees the LVM.

ANY insights or points in a direction would be VERY much appreciated.  I figure I will try for a day or two then I just need to blow it out and start over which I don't wanna do but the server needs to come back.

Mark

---

### Post by steeldriver on 2012-06-27
Ubuntu version?  I have xfs on top of lvm2 on top of raid1 on an 11.10 box here so I may be able to help

IIRC you mount these things via /dev/mapper/logical-volume-name or the equivalent UUID - in my experience the mapper is pretty resilient and finds the lvm even if the underlying raid volume re-assembles with a completely different designator (e.g. /dev/md127 instead of /dev/md0)

I'd start by looking at the whole lvm stack i.e. pvdisplay / vgdisplay / lvdisplay

---

### Post by darkod on 2012-06-27
Once you boot, can you see the Physical Volume and the Volume Group with:
```
sudo pvscan
sudo vgscan
```

It should show the physical volume for the LVM and the volume group.

---

### Post by Einsteiniac on 2012-06-28
> **darkod said:**
> Once you boot, can you see the Physical Volume and the Volume Group with:
```
sudo pvscan
sudo vgscan
```

It should show the physical volume for the LVM and the volume group.

Steel Driver and Darkod thanks for the replies and sorry it has taken so long to get back.

I am running 11.04

when running pvscan and vgscan I get this.

```
root@storage:~# pvscan
  PV /dev/md0   VG media   lvm2 [13.88 TiB / 6.00 GiB free]
  Total: 1 [13.88 TiB] / in use: 1 [13.88 TiB] / in no VG: 0 [0   ]
root@storage:~# vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "media" using metadata type lvm2

```

Also I have tried to mount with.

mount /dev/mapper/media-media /media/RAID 

with the same results.

Everything sees the LVM and the RAID just fine I just can't mount or do any File systems checks because it essentially crashes.  Do you know where the logs for something like this would be stored so I could maybe see whats happening?

Mark

---

### Post by darkod on 2012-06-28
Did you try activating the volume group?
sudo vgchange -a y

Only then the devices like /dev/VGname/LVname become available.

The filesystem check is done on unmounted anyway, and I haven't used xfs_check, but I guess it would be like:
sudo xfs_check /dev/VGname/LVname

And mounting:
sudo mount /dev/VGname/LVname /mount-point

Make sure the mount point exists because if you are doing this from live mode it might not.

---

### Post by Einsteiniac on 2012-06-28
> **darkod said:**
> Did you try activating the volume group?
sudo vgchange -a y

Only then the devices like /dev/VGname/LVname become available.

The filesystem check is done on unmounted anyway, and I haven't used xfs_check, but I guess it would be like:
sudo xfs_check /dev/VGname/LVname

And mounting:
sudo mount /dev/VGname/LVname /mount-point

Make sure the mount point exists because if you are doing this from live mode it might not.

Sorry yes I have done the vgchange command and just tried it again for giggles.  The mount point is there and root owns it and has all permissions.  

Its as if something is failing but nothing is reporting what exactly is failing.

Mark

---

