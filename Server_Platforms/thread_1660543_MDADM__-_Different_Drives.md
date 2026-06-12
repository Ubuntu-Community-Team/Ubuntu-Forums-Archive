---
title: "MDADM  - Different Drives"
date: 2011-01-05
forum: Server Platforms
---

### Post by JonnyRocket on 2011-01-05
I put together a file server about a year ago and you guys convinced me to use linux software RAID rather than an expensive hardware solution, and I have to say I've been completely impressed with it all year. So thank you all for that suggestion. I'm starting to run low on space so I'm looking to add a drive or two to the array.  I've read through the documentation and it seems simple enough to grow the array (and maybe convert it from 5 to 6).  My question is should I stick with the same drive manufacturer and model, or would it be ok to purchase different drives?  Are there any performance impacts I should be looking into? I'm just looking to save some cash on cheaper drives.

---

### Post by ian dobson on 2011-01-06
Hi,

It shouldn't be a problem using different drives. My backup array (3x2Tb drives) uses different models of drive (all are wd).

Being a backup array it only get hit once a day or so (during backup) but it's never missed a beat.

Note: mdadm will only use the size of the smallest drive in the array. So if you add a 2tb drive and your other drives are only 1tb then mdadm will only use 1tb of the new drive.
 
Regards
Ian Dobson

---

