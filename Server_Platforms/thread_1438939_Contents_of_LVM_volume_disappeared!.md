---
title: "Contents of LVM volume disappeared!"
date: 2010-03-25
forum: Server Platforms
---

### Post by eomvjv on 2010-03-25
I have an LVM group containing three 500GB drives in my NAS/home server. Last week, the contents of this group(ext4) disappeared with no apparent explanation.

I've been looking around for solutions, and here's what I've tried:
[LIST]Restoring the LVM configuration using vgcfgrestore with the most recent file from /etc/lvm/backup/. This restored just a few of the folders.
[/LIST]
[LIST]
Run fsck on the group. Lots of errors, all fixed, but nothing more appears.
[/LIST]
[LIST]
Run badblocks on each of the disks, no errors found. 
[/LIST]

It seems there is nothing wrong with the drives physically, or with the software configuration, so where have the files gone? Any suggestions?

Even if I can't restore the full volume, it would really help if I could just grab what I can from the drives, any ideas on how to do this?

Thanks very much!

---

### Post by KB1JWQ on 2010-03-25
fscking this was probably a mistake.

Does lvs / pvs show any of the logical volumes that went messing?

---

### Post by eomvjv on 2010-03-25
All volumes are and were always present, that's what makes this all so confusing!

```
pvscan:
  PV /dev/sdb1   VG fileserver   lvm2 [465.76 GB / 0    free]
  PV /dev/sda1   VG fileserver   lvm2 [465.76 GB / 0    free]
  PV /dev/sdd1   VG fileserver   lvm2 [465.76 GB / 0    free]
  Total: 3 [1.36 TB] / in use: 3 [1.36 TB] / in no VG: 0 [0   ]

lvscan:
  ACTIVE            '/dev/fileserver/share' [1.36 TB] inherit
```

There were a few hundred gigs of space free on the volume though, should it show as 0 free? Is this a clue as to what might've gone wrong?

Thanks for your reply!

---

