---
title: "Re-installing XP"
date: 2008-10-01
forum: Windows
---

### Post by civillian on 2008-10-01
I'm going to install XPsp3 again on my PC for gaming purposes. The issue is that I have an ubuntu only machine (not dualbooted with anything).

My original plan was to resize my partitions to allow some space for my xp C: drive, but I remembered that when I tried this before, XP complained that I had too many partitions for it to install. Now I can't remember what this number was. I had a feeling that it was 3 and so all I need to do is remove my swap, install XP again, restore the bootloader (from ubuntu live CD) and then remake my swap partition.

Can anyone shed any light on this?

---

### Post by ajgreeny on 2008-10-01
You can only have four primary partitions on a disk so you may need to make an extended partition and add new partitions to that.  The only problem I see is that windows does not like to be on an extended, logical partition, and you may have problems getting it to boot from one.  Perhaps you need to let us see your current partition layout with ```
sudo fdisk -l
```

---

### Post by smoker on 2008-10-01
if you have 3 partitions at the moment, and you want to make a fourth for windows then that should be no problem, as long as it is a primary partition, as ajgreeny stated, you can have 4 primary partitions. as long as you make the windows partition large enough, i don't see how it can complain! if you format it beforehand, ie, with gparted or partition magic, it may be easier.

---

### Post by civillian on 2008-10-01
I do only have three partitions at the moment (swap, / and /home) so if I just resize my /home partition (it's about 400GB) then format some ntfs space at the end (in terms of gparted layout) i should be ok?

---

### Post by smoker on 2008-10-02
> **C!V!NT said:**
> I do only have three partitions at the moment (swap, / and /home) so if I just resize my /home partition (it's about 400GB) then format some ntfs space at the end (in terms of gparted layout) i should be ok?

i would think that would be ok, though you may have to 'mark' the partition as an 'active' partition with your partitioner for windows to see it (could be wrong about the active part, though, i haven't dual-booted this way for years!). but, as is wise with partitioning, back up essential data first.

---

