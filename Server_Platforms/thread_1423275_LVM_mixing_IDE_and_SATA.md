---
title: "LVM mixing IDE and SATA"
date: 2010-03-06
forum: Server Platforms
---

### Post by leegold on 2010-03-06
Is LVM sensitive to mixing different drives w/different specs? If I mix IDE and SATA drives are there issues?

Thanks

---

### Post by richardjh on 2010-03-06
You can combine any block devices using LVM.
You could combine an external USB drive an internal hard disk and a floppy disk using LVM if you wanted to. 

The slowest device will be a bottleneck for the performance.

I don't think there is any reason not to use LVM across a SATA and IDE drive.

---

