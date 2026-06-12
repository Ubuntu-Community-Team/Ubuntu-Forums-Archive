---
title: "Abysmal performance of md raid6 direct or sync IO"
date: 2011-10-28
forum: Server Platforms
---

### Post by Xianath on 2011-10-28
Hi all,

I have a home server with an md raid6 array with LVM on top. I built it as far back as 8.04 and have had no problems until I upgraded to 11.04. The upgrade itself took well over 12 hours, almost all of it spent in dpkg extracting packages. I googled around and found out that dpkg has been changed to default to synchronous I/O. I tried the --force-unsafe-io option but it didn't help at all. I then ran some benchmarks and the results are quite abysmal:

Write performance, normal: 450MB/sec
Write performance, direct IO: 39MB/sec
Write performance, sync IO: 22MB/sec

The array itself is set up from 12 identical Samsung SpinPoint F1 1TB drives, with a 256k chunk. The test was a simple dd using 2560k size blocks and writing to an XFS filesystem on top of LVM. As far as I can tell, the XFS format and mount parameters are OK (swidth etc) as well as block device parameters in sysfs (optimal_io_size, alighment etc.)

I do expect *some* performance drop from bypassing the stripe cache but an order of magnitude seems excessive. Is this normal? Any hints as to where to look for clues?

Thanks,
Peter

---

### Post by rubylaser on 2011-10-28
That is definitely slower than it should be.  Unfortunately, I don't run anything but the LTS releases on my servers, so I can't compare apples to apples with yours.  Prior to my recent hard drive upgrade, I had 11 disks in an mdadm RAID6 array, without LVM on top of it.  I would get slightly higher read numbers, and around 260 MB/s write.  This was on mdadm 3.1.4, so it should be the same version you're running on 11.04.

A few questions... Have you done anything to tune mdadm in terms of stripe_cache_size, readahead, etc?  Anything strange in the logs?  What does this yield for read / write speed?  Have you checked the load on the system and made sure that something isn't using up all of the resources?

```
dd if=/dev/zero of=/array_mount/point bs=1M count=10000
dd if=/array_mount/point of=/dev/null bs=1M
```

---

### Post by Xianath on 2011-10-28
The array has certainly been tuned up in terms of stripe_cache_size, read_ahead_kb and other params, it's even worse without it. Read (direct) and write (cached) speeds of a 25GB file are around 350-400MB/sec average (peaking to 450MB for the first 4GB of the file, but that's expected given the amount of RAM in the system).

What I notice during O_DIRECT and O_SYNC writes is a rather large ratio of read IOPs that shouldn't be there if writes indeed happen in stripe sized blocks. I really can't explain this behavior except by some misalignment between XFS, LVM and md, though there really shouldn't be one and newer kernels account for that anyway. My current theory is that for some reason when a single request to the LVM (or md) device that is flagged as either O_SYNC or O_DIRECT is broken down into 12 individual requests, those are serialized by the kernel instead of executing in parallel, which would make more sense for a compound block device. I have no idea how to prove or reject this, though. Any hints?

---

