---
title: "mdadm RAID5 vs. 4x4 LVM Striped in worse case scenarios?"
date: 2011-03-12
forum: Server Platforms
---

### Post by AllGamer on 2011-03-12
I'm trying to find out which one is safer when it comes down to recovery process in case of a drive failure 

A RAID5 created in mdadm
or
a Stripe RAID created on pure LVM

the RAID is purely for data storage for a SAMBA server, the OS will reside on its own drive.

Ideally the RAID physical hard drives should be re-build on another machine in case of catastrophic server failure (mother board problem, or any other random problems as an example)

I can't decide which of the 2 software RAID method is more convenient and safest, don't care about performance, it'll be a dedicated server for mass storage, it's going to mirror other 3 file servers on fakeRAIDs (dmraid), it's simply a redundant backup for the backups

The important goal here is portability.

from what've read it appears that LVM might be more portable?

but according to some dated (2009) info the mdadm seems to be a bit buggy when it comes to rebuilding the array, yet LVM doesn't appear that safe either

which one would you pick for ease to rebuild on catastrophic failures?

---

### Post by rubylaser on 2011-03-12
This is a no brainer for me, I'd go with mdadm in RAID5 (I'd use RAID6).  LVM in a stripe has no redundancy (it's basically RAID0).  If you lose 1 disk in your stripe set, you lose your stripe completely.  It is in no way redundant. mdadm in RAID5, can lose 1 drive before losing parity.  If the reliability of your data is paramount, I'd still use either RAID10 or RAID6 with mdadm.  Since disk failures occur a lot more often than motherboard failures, I'd be concerned about focusing on the redundancy of my disks.

But, in the case of a mobo failure, mdadm is easily transferrable to a new machine (you can even mount your array with the livecd if you apt-get install mdadm), and is very easy to replace failed drives.    Hope that helps.

---

### Post by AllGamer on 2011-03-12
thanks, yes that makes sense, i was testing out the LVM strip vs. mirror modes, and they are award to say the least

mdadm works much more like a "real" physical RAID setup than LVM

---

