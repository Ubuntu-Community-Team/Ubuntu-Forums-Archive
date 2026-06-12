---
title: "Partition problem - RAID5"
date: 2008-04-03
forum: Server Platforms
---

### Post by sevenmichael on 2008-04-03
Hi,

We have a new server, with RAID5 array for storage (6TB total - 4.5TB usable). I installed Ubuntu 7.10 server on a separate HDD (outside of the RAID array).

The OS runs fine and recognizes the RAID5 array and shows the correct size.

Here is the problem: when I try to create a partition with parted, and even though I select the full 4.5TB - it creates a partition of 550GB only... 

Is there any limitation on the partition sizes in Ubuntu ?

Thanks,

Michael

---

### Post by GigaVolt on 2008-04-03
google -> hint 1: EFI
google -> hint 2: parted

---

