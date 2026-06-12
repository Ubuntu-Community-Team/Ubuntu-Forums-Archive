---
title: "How Many CPU's with 8.04 TLS ?"
date: 2008-07-03
forum: Server Platforms
---

### Post by oakey_99 on 2008-07-03
How many CPU's does 8.04 support ??

---

### Post by promodus on 2008-07-03
```
 cat /boot/config-2.6.24-19-generic | grep  NR_CPUS
```

change config-2.6.24-19-generic to fit your current running kernel.

Even despite what Ubuntu supports, it's easy enough to recompile the kernel. 

I believe the short answer you're looking for is **8.**
Which typically this would be dual quads.

For 4way configurations you need AMD Opteron 8 series, and MP Capable XEONs.

It is theoretically possible to modify the kernel to work in a NUMA based architecture with high-speed interconnects to create a somewhat virtual SMP environment without special Opterons or XEONs, at that point you'd definitely need a custom kernel. (vSMP)

---

