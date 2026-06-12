---
title: "Linux swap partition not on VDI image."
date: 2016-05-30
forum: Virtualisation
---

### Post by dajjyhuaca on 2016-05-30
I converted my Linux OS (Ubuntu 15.10) on SSD to a virtualbox vdi. Only when I started to boot from it (and it seemed to boot just fine) did I remember that the swap partition for my OS was on a separate physical disk! It doesn't finish booting and it drops to a root shell under the image, but it says read-only when I try to edit something say in nano.  What to do?

Your answer/help should go under number 2.

1. Do I need to rectify the situation on the physical disk then reimage?
2. Is there a way to avoid scenario #1?

Thanks a mil!

---

### Post by houstonbofh on 2016-05-30
1. No.  You can just fix it.
2. Yes.  Fix it one of two ways.  One involves a Linux boot cd.

You can fix it in virtual box by adding an additional virtual disk and formatting it swap.  If it is in the "same place" your image should see it and boot.

Or, you boot a livecd and edit the fstab to change the mount location where you have a swap partition or disk, or remove swap entirely.

---

### Post by MAFoElffen on 2016-06-01
Mostly true: Follow "adding or changing swap" instructions as if you would for a physical machine and adapt it to your VM image of one of the image partitions. Your still have to mod the fstab to the specific /dev/DiskID/PartID or the partition's FS UUID...

---

