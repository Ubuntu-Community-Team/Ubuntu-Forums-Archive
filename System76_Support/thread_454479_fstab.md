---
title: "fstab"
date: 2007-05-25
forum: System76 Support
---

### Post by perce on 2007-05-25
I noticed that root and home are on the same partition, and I would like to separate them. The problem is that fstab uses the UUID convention, and someone in the forum said that switching to the device convention confuses automounter. If I split hda1 in two partitions, how can I discover the UUID of the new one? Also the file /proc/swaps is empty. Does this means that swap is not activate by default? notice that there is a swap entry in fstab.

---

### Post by psusi on 2007-05-25
What does your fstab currently say?  The existing UUID will not change if you shrink the partition, and there is no reason not to refer to the new partition by name instead of UUID, but if you want to, you can look up the UUID of the new partition by running:

sudo /lib/udev/vol_id -u /dev/hda1

Replace hda1 with the correct name of the partition in question.

---

