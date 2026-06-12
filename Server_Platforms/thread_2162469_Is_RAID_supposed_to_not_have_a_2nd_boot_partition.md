---
title: "Is RAID supposed to not have a 2nd boot partition"
date: 2013-07-14
forum: Server Platforms
---

### Post by wlraider70 on 2013-07-14
I have 2 disks in a RAID 1 array.

I have 3 partitions on my primary disk; boot, / , and swap.
/dev/sdb has mirror copy of the / partition. Thats it

Should there be more, is that my misunderstanding? I have the redundancy of the data, but I can't boot that second disk so its far less useful to me than I originally thought.


How can I get 2 identical disks?

---

### Post by sandyd on 2013-07-14
> **wlraider70 said:**
> I have 2 disks in a RAID 1 array.

I have 3 partitions on my primary disk; boot, / , and swap.
/dev/sdb has mirror copy of the / partition. Thats it

Should there be more, is that my misunderstanding? I have the redundancy of the data, but I can't boot that second disk so its far less useful to me than I originally thought.


How can I get 2 identical disks?

If thats software RAID, then its normal
You will need to have LVM setup on top of the RAID in order to have more than one partition on the RAID.

---

### Post by wlraider70 on 2013-07-14
The unit has a cheap (might be a stretch to call it) RAID controller. Its more of a PCI sata card that offers RAID controls. 
It is not the the mobo or OS raid.

Is it possible to setup LVM now after my system is configured and running?

---

### Post by sandyd on 2013-07-14
> **wlraider70 said:**
> The unit has a cheap (might be a stretch to call it) RAID controller. Its more of a PCI sata card that offers RAID controls. 
It is not the the mobo or OS raid.

Is it possible to setup LVM now after my system is configured and running?

are you using dmraid (fakeraid)?

You *can* migrate to LVM, though it really depends on how much work you are willing to do.

i.e. something like
1. Mirror Drive onto External
2. Create LVM Physical Volume/Volume Groups/Logical Volumes to represent root, swap, boot, etc
3. Put the root data back on.
4. Update FSTAB
5. Reinstall and update grub

There are tools such as "[blocks]("https://github.com/g2p/blocks")" which will convert to LVM, but once again, there is always the chance of data loss, corruption, etc, etc

---

