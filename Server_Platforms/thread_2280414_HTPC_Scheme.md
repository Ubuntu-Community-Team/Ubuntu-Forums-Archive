---
title: "HTPC Scheme"
date: 2015-05-30
forum: Server Platforms
---

### Post by Hugo_Lapointe_Di_G on 2015-05-30
Hi Everybody!

I need your help. Can configure my server like this? If not, I can I improve it?
[IMG]https://scontent-ord1-1.xx.fbcdn.net/hphotos-xat1/v/t1.0-9/10613023_10153425809375407_2708868395727778049_n.jpg?oh=b024f13bc0c9d4f4cf89bcad306f222a&oe=56099BAA[/IMG]

---

### Post by cariboo on 2015-05-30
That looks like an awful complicated setup. I'm not really sure why you feel you need raid as well as LVM. I'd say select one or the other, and spend your time and  money on a reliable backup solution, as neither raid nor LVM are a replacement for good backups.

---

### Post by TheFu on 2015-06-01
It isn't clear what you are really trying to do.

RAID5 without at least 3 physical disks is foolish.
RAID0 only makes sense for temporary storage - most companies will switch to SSD storage for high performance needs.

Also - it would help if you clarified - HW-RAID or SW-RAID? That changes what is possible/smart.

Logical volume groups are the 3rd level. Can't start there.
* physical disks are added to ...
* physical volumes (PV)
* volume groups (VGs) sit on PVs
* logical volumes (LVs) sit on VGs

HW-RAID fits between the physical disks and PVs. Don't go cheap with a RAID controller ($350+) to get a real HW RAID controller. Anything less expensive probably is "fake-RAID." I cannot think of any good reason to ever use fakeRAID.  SW-RAID can fit a few different places.

RAID is only for HA needs. An HTPC doesn't need RAID. Can you really not have it down for a day?  Corrupt files can be written to RAID very fast, so backups are still completely mandatory.

---

