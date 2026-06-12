---
title: "Is it possible to remove a failed disk from mdadm RAID 5/6 before adding new one?"
date: 2020-12-01
forum: Server Platforms
---

### Post by hikariws on 2020-12-01
I'm reading a tutorial on [https://www.tecmint.com/grow-raid-array-in-linux/](https://www.tecmint.com/grow-raid-array-in-linux/) teaching how to add and remove disks from a mdadm array.

But that brought me a question. When a disk on a RAID 5 or 6 fails and we need to replace it, do we need to first add the new one, before removing the failty? Is it possible to remove it first, to then add the new?

I ask that because I'm planning to build a PC with 6 HDs in RAID, which will fill all its SATA ports. If I can't first remove the failed disk to then add the new one, then I'll need to leave a SATA port free for that, which means I'll be limited to a 5 HDs RAID.

---

### Post by TheFu on 2020-12-02
Running ubuntu off a mdadm array is non-trivial. Having data on RAID-whatever **is** trivial. You'll probably need 1 OS drive and 5 Data disks. An OS can be setup in a mirror, using LVM and 2 drives.  The mirror would be added via lvm commands after the install is finished.

Replacing a failed disk for a RAID setup is the expected method.

RAID is never a backup.  Backups are 1000x more important than RAID. RAID solves 2 issues, HA and perhaps improved performance. Backups solve 1001, at least, including failed RAIDs. Don't confuse RAID with volume management which can bring all sorts of capabilities. Those are separate or at least they can be.

If you really care about data integrity, use ZFS for the data, not mdadm.  ZFS for the OS isn't production-ready on ubuntu, though people do use it.

---

### Post by darkod on 2020-12-02
You can (and should) remove the faulty, both in the mdadm array and the server, before adding the new one.

---

### Post by volkswagner on 2020-12-06
+1 for “can and should”. 

To bit a bit of a sickler, RAID can solve more than two problems and not all servers have adequate RAM for a ZFS pool. 

With your arrangement the six sata ports limits you from having a hot spare which may not be a big deal if you have easy access to the physical server. 

You may want to tell us why you want RAID if you’d like more comprehensive replies.  For example are you interested in just fault tolerance? Are you more interested in performance or simply want to be able to combine disks to easily create mount points that span multiple disks?

---

### Post by LHammonds on 2020-12-07
My experience has only been with hardware RAID so I cannot comment to mdadm best practice.

If this was hardware RAID, I would +1 for removing the "failed" drive first.  If a drive failed in RAID 5, the two drives beside it are reconstructing and presenting the data where the failed was located.  How you do it depends on the hardware.  For example, on well-designed and high-end systems, you might only need to identify the failed drive (so you pull the right one!), pull it and insert the replacement drive and it will handle rebuilding it for you (unless you had a hotspare and it did it for you already....which means you are replacing the failed drive to become the new hotspare).  Other systems are not so automated and their standard procedure is that you flag the failed drive for removal BEFORE ejecting it and then manually tell it to rebuild AFTER you insert the replacement drive.  You just need to know what the best practice is for your hardware/software.

LHammonds

---

### Post by SeijiSensei on 2020-12-07
I'm with TheFu. Don't put the boot drive in a RAID. It doesn't need to be that large either. Have any older drives lying around? 80 GB would be plenty. Make it the first drive in the list via the BIOS, then RAID the other five.

Here are the steps to remove a faulty drive with mdadm: [https://www.thegeekdiary.com/replacing-a-failed-mirror-disk-in-a-software-raid-array-mdadm/](https://www.thegeekdiary.com/replacing-a-failed-mirror-disk-in-a-software-raid-array-mdadm/)

---

