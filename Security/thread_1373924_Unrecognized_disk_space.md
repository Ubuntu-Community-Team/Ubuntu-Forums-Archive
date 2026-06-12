---
title: "Unrecognized disk space"
date: 2010-01-06
forum: Security
---

### Post by dogdo on 2010-01-06
Hi 

Anyone know what this unrecognized disk space means?

---

### Post by mcduck on 2010-01-06
The partition is either unformatted, or formatted with some file system Linux isn't able to use.

Based on the rest of the info it sems to be a swap partition or a Solaris file system (which uses the same ID as Linux swap does).

---

### Post by dogdo on 2010-01-06
Hymmm i already have another swap partition for use with an encrypted private folder-so where did this other partition come from? i did install a new printer the other day and while there was no exact driver available i was able to get the printer working with a driver for a earlier model of the printer...

---

### Post by mcduck on 2010-01-06
Actually now that I look your screenshot again I doubt that its really another partition at all, just some bug in the disk manage app or your partition table.

It really can't be a real partition, your 9,3GB extended partition can't contain two partitions both 9,3GB large.. Besides, the actual swap partiton appears to be inside this unrecognized partition, which doesn't make any sense either.. 

Could you perhaps run "sudo fdisk -l" and post the output here for a better look at your disk layout? And perhaps add the contents of your /etc/fstab file as well...

---

