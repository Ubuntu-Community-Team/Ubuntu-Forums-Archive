---
title: "Slow Raid 5 Performance"
date: 2010-07-19
forum: Server Platforms
---

### Post by FeraTech on 2010-07-19
We are having a very serious issue.

We have 3 500gig sata drives in a software Raid5 configuration. However, the performance is VERY slow. With read times of over 40mbps from the array as soon as we get anything around 1000kbps activity over "iotop" the entire server becomes useless.

We have one directory with over 400 sub folders. Simply listing the contents takes 3 minutes.

I tried copying the directory structure to my laptop and it even runs faster on it than on my server!

Specs:
ISPconfig 3 on Ubuntu 10.4
AMD Quad Core 2.2mhz
8gig Ram
3 Sata300 500gig WD drives in software raid 5

Drive Partitions:
1gig boot in Raid1
10gig swap in Raid 1
489gig root in Raid 5

---

