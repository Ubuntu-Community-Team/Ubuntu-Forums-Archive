---
title: "Intel S1200BTL (ESRT2 Raid) &amp; Ubuntu Server questions"
date: 2012-01-21
forum: Server Platforms
---

### Post by arpisk on 2012-01-21
We bought an entry-level server motherboard for our company.
The type of motherboard is S1200BTL,with 4GB RAM, two SSD (Intel SSD 320 - 80GB) and two HDD (WD Black 1TB). My plan is to make a file server of it (Samba). We have 30 Windows and Linux clients.

I would like to resolve as follows:
- 2 SSD - Raid Array1 60GB (20% freely outside the partition) for System
- 2 HDD - Raid Array2 1TB for data

Questions:
- which server version to install, 10.04LTS or 11.10?
  Unfortunately We should wait until April to 12.04LTS version.
- Intel issued ESRT2-Raid drivers for Suse and RedHat, how do I install it? I found a description to Ubuntu: [http://users.emt.ee/aigark/wp/?p=47]("http://users.emt.ee/aigark/wp/?p=47")
- is possible using TRIM function with RAID?
- do I put the swap space outside of SSD?
- what a size of partitions advisable to be create?

Thanks for help!

---

### Post by arpisk on 2012-01-22
At least could someone to give information about these:
- is possible using TRIM function with RAID?
- do I put the swap space outside of SSD?

---

