---
title: "Low Priority Problem init ureadahead terminated"
date: 2010-06-30
forum: The Cafe
---

### Post by Mark_in_Hollywood on 2010-06-30
After changing kernels (an upgrade to: 2.6.34-020634-generic) I get an odd message at boot time, which reads:

init ureadahead main process 344 terminated with status 5

and then 6 lines which read:

[7.648790 sd 6:0:0:0: [sdb] Assuming drive cache: write through
[7.652409 sd 6:0:0:0: [sdb] Assuming drive cache: write through
[7.672040 sd 6:0:0:0: [sdc] Assuming drive cache: write through
[7.705041 sd 6:0:0:0: [sdc] Assuming drive cache: write through
[7.747033 sd 6:0:0:0: [sdc] Assuming drive cache: write through
[7.766418 sd 6:0:0:0: [sdc] Assuming drive cache: write through

I'm posting this here as I the OS and applications (Firefox, thunderbird, f-spot) all are working without problems. I'm not looking to "fix" this, only to know what it's about. Netsearching this returns nothing via Google with the exact same words. Similar words appear some from a French Ubuntu user.

---

### Post by TheLions on 2010-06-30
[http://lists.us.dell.com/fom-serve/cache/110.html](http://lists.us.dell.com/fom-serve/cache/110.html)

> The Linux block layer makes some assumptions about when writes are actually committed to disk. LSI RAID controller logical drives pretend to be SCSI disks, but the firmware and driver doesn't report whether the controller is in "write-through" mode or "write-back" mode. Without this information, the block layer assumes "write-through". This is safe, because the controller has a battery-backed cache.
LSI's engineers know that their driver should handle this better so you don't see this message. But it's not an error, and it doesn't affect the system. 
Matt_Domsch

---

