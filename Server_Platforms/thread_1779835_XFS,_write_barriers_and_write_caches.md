---
title: "XFS, write barriers and write caches"
date: 2011-06-11
forum: Server Platforms
---

### Post by Rincage on 2011-06-11
Am running Ubuntu 10.04 with an mdadm RAID5 array spread across x4 2TB SATA hard drives. The filesystem used is XFS. 

I'm reading comments about write caches (built in to each disk) causing problems with data corruption if there is a power failure during a write. This makes sense, and my understanding is that XFS mitigates this to some extent by using write barriers to flush the cache periodically. But I also read that this doesn't always work on non-physical devices (like an md0 raid array) - see here

[http://madduck.net/blog/2006.08.11:xfs-zeroes/](http://madduck.net/blog/2006.08.11:xfs-zeroes/)

> XFS supports barriers as well, but unfortunately not yet on non-physical media, like RAID or dm-crypt. ext3 seems to work okay on both.

So my question ... is this still the case in 2011 and how do I find out if write barriers are working on my RAID array with XFS?

If I find out write barriers are not working, should I try and disable the write caches entirely?

Thanks

---

