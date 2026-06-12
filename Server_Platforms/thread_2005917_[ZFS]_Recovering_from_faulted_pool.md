---
title: "[ZFS] Recovering from faulted pool"
date: 2012-06-18
forum: Server Platforms
---

### Post by Asche42 on 2012-06-18
Hello,

I have got a pool of two mirrored 2 To HDD.
As the free space on them was decreasing quite fast, I added two 3 To HDD to make a RAID 10 with ZFS.

But, after the boot, the pool was faulted because HDD path changed. Currently, the 3-To-disks are /dev/sdb and /dev/sdc; and the 2-To-disks are /dev/sdd and /dev/sde.

I tried to recreate the pool and destroyed the old one. When creating the new pool, the new mirror was totally empty.
I tried
```
# zpool import -Ff zpool0
```but the data was restored at April 29th's state…

I destroyed, another time, the pool and now I cannot get it (April 29th's state) back, it does not appear in
```
# zpool import -D
```I do not know how to get the whole data back, especially the one after April 29th. Any help would be appreciated. :)

Thanks,
Asche42.

---

