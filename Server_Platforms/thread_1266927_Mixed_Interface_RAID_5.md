---
title: "Mixed Interface RAID 5"
date: 2009-09-15
forum: Server Platforms
---

### Post by eniacpx on 2009-09-15
I have 2 320GB ATA100 drives in my server, they are currently not part of a RAID configuration. I would like to set up a software RAID 5 with a third drive. My question is this, does the third drive have to be ATA100 as well? Or can I put a SATA drive in there?

It is getting increasingly hard to find 320 ATA100 drives, and I would like to slowly convert all my storage to SATA, so I thought I would start with this drive. I would also like to be able to add additional SATA drives to this in the future.

Thanks!

---

### Post by grantemsley on 2009-09-15
With software raid you can mix IDE, SATA, and even USB/firewire drives without any problems.

The performance may suffer a little, since the array's speed will be limited by the slowest drive, but it will work just fine.

---

