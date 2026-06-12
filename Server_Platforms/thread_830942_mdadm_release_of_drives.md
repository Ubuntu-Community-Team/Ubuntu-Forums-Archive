---
title: "mdadm release of drives"
date: 2008-06-16
forum: Server Platforms
---

### Post by fjgaude on 2008-06-16
After an array is created with mdadm what is the best way to release all drives of the array to be used for other purposes?

One purpose would be to use some of the drives in a new array. What does it take to remove all references to the old array's UUID and superblocks so that the new build occurs without incident?

---

### Post by dlazerka on 2008-06-16
To stop a RAID array use ```
mdadm --stop /dev/md0
``` where ```
/dev/md0
``` is your raid device.

To clear RAID-specific data from a partition, use ```
mdadm --zero-superblock /dev/sda1
``` where ```
/dev/sda1
``` is the partition you want to clean RAID metadata from.

---

### Post by fjgaude on 2008-06-16
Thanks... I take note.

umount the array, stop it, then zero the superblocks on each drive in the array. Then we can create another array using a different md number, md[nn]. Okay!

I wonder how you get the already used md number removed from the boot list that the kernel and md use to assemble the old array? Get rid of the old mdadm.conf for one thing, then what?

---

