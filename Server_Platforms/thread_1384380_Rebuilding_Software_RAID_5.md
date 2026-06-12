---
title: "Rebuilding Software RAID 5"
date: 2010-01-18
forum: Server Platforms
---

### Post by CREEPING DEATH on 2010-01-18
I set up a machine for a customer with software RAID 5, his insistence, I'd much prefer a proper RAID controller.
Anyway, 1 of the 4 drives is throwing SMART errors on smartmontools and needs to be replaced.
How do I do it?  I already have another of the same drive (WD Caviar Green 2TB) but I'm not sure it's "identical".  Help please!

CD

---

### Post by pirateghost on 2010-01-18
replace the failing drive with the replacement, format it as linux raid, and add it to your raid array, let the rebuilding begin

---

### Post by CREEPING DEATH on 2010-01-18
> **pirateghost said:**
> replace the failing drive with the replacement, format it as linux raid, and add it to your raid array, let the rebuilding begin

That's it?  No rebuilding commands or anything?  I can format and flag it as RAID on my tech box so no problems there.

CD

---

### Post by pirateghost on 2010-01-18
i use webmin on my servers, so when i need to rebuild an array, its just a matter of adding that new partition to the array.  it rebuilds itself when it sees the new drive

---

### Post by Fire_Chief on 2010-01-18
From the Software-RAID howto pages regarding reconstruction:
>     * Power down the system
    * Replace the failed disk
    * Power up the system once again.
    * Use raidhotadd /dev/mdX /dev/sdX to re-insert the disk in the array
    * Have coffee while you watch the automatic reconstruction running


Cheers!

---

