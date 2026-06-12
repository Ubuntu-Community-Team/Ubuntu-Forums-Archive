---
title: "Is there a max limit on filling up a non-root partition?"
date: 2011-05-18
forum: Server Platforms
---

### Post by Avicus on 2011-05-18
Hi, I have a number of servers I manage, and one of them is archiving old data that is never modified on a separate partition. This partition is at 100% capacity. A friend of mine says this is an unsafe way to keep this partition, even tho I don't plan to add any more data to it or change anything within. I know I can archive the data to dvd, but I'd like to keep the data online for my users.

What are your opinions on this? Can I keep this archive partition at 100% capacity? Or do I risk some sort of data corruption? Should I mount this partition as read-only to help prevent any corruption?

Thanks for any input!

---

### Post by Avicus on 2011-05-18
This partition is running LVM, so it would be trivial to add more space, but I'd prefer not to. If I must, what would the minimum free space I'd need to keep the partition at?

---

### Post by dtfinch on 2011-05-18
I'm not aware of any problems with having a full non-root partition mounted if you're not writing to it.

If this is an ext2/3/4 partition, you can usually decrease the reserved % to increase free space a little. Using "tune2fs -m1" on the device would reduce it to 1%, increasing free space by 4% of the total size, assuming the current reservation is the default 5%.

---

### Post by Avicus on 2011-05-18
Thanks for the info... so, assuming this 5% exists, does the 5% get reported in the total harddrive space available when running 'df' for instance? Or is it an invisible amount hidden from system processes? As in, when the partition is reported to be at 100% capacity, is there a secret 5% of total hidden from view?

---

### Post by dtfinch on 2011-05-18
Example on a vm:```
# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              7208664   3407060   3435424  50% /
...
# tune2fs -m1 /dev/sda1
tune2fs 1.41.14 (22-Dec-2010)
Setting reserved blocks percentage to 1% (18309 blocks)
# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              7208664   3407060   3728368  48% /
...
```
You can see that used+available blocks is about 5% less than the total in the first df, and 1% less in the second.

---

