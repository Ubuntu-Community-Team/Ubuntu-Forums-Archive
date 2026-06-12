---
title: "Restore to Raid 1"
date: 2009-07-01
forum: Server Platforms
---

### Post by MarioFromBelgium on 2009-07-01
Hi,

I have successfully setup Ubuntu 8.01 Desktop with RAID1.(software raid from UBUNTUs alternative install)

I'm planning backup to tape with TAR.
Will I be able to restore my system in case both HDD refuse duty. 
In other words if I backup from / will my backup-file contain all necessary data to rebuild the RAID.
Or even more will a restore refuse duty just because it has the RAID config?

Somewhere I have read that building a RAID config from within an installed UBUNTU is a hassle. This would mean that I would have to re-install Ubuntu with RAID 1 and than restore the necessary apps/configs/data... nice theory but...is this feasible?

Thx,
Mario

---

### Post by ian dobson on 2009-07-01
Hi,

You could use dd to read directly from your md array to a tar archive then dd it back.

dd if=/dev/md0 of=/dev/tar_device
dd of=/dev/md0 if=/dev/tar_device

The md0 raid device must exist before you can restore to it.

Regards
Ian Dobson

---

### Post by MarioFromBelgium on 2009-07-02
so what you say is

1° put two new HDD in
2° put life cd in and make partitions with RAID device(s)
3° don't install ubuntu but restore data from tar

is that the way to do it?

---

### Post by ian dobson on 2009-07-03
Hi,

Yes, that about it.

Note: I've only used dd to copy entire drives and it's always worked for me. As a raid array is just another block device under linux I can't see why it shouldn't work.

I reccomend you test it before you really need it :lolflag:

Regards
Ian Dobson

---

### Post by MarioFromBelgium on 2009-07-03
If I find time I'll test it.

---

