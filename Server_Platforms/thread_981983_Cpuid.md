---
title: "Cpuid"
date: 2008-11-14
forum: Server Platforms
---

### Post by Vegan on 2008-11-14
As I have mentioned my Linux machine is a genuine IBM 300 GL that has been my web server for eons. The CPU uses 17.5W so its very cheap to run.

Curiously the BIOS does not recognize the CPUID properly making Linux misidentify the device. No big problem, the CPU seems to be asserting its ability well.

Serving deflated documents is very responsive, and the machine seems to be faster than the Windows box with a Dual Core AMD processor.

With 768 MB of RAM there machine has lots of room for caches and I note phpBB especially likes to cache documents. If I change the ads, I have to purge the cache.

I probably can find a different CPU, there are lots of them around. The thing is the machine is fine as is.

There is a 137 GB disk limit, but Linux should be able to use NFS/SAMBA for connecting to another disk/server easy enough. Of course I can mount a disk somewhere too.

Can Linux get around the 137 GB limits?

---

### Post by Titan8990 on 2008-11-14
What filesystem are you using that is limiting you to 137GB? EXT2 and EXT3 both can have up to 32TB volumes...

---

### Post by cariboo on 2008-11-14
Yes, unless things have changed quite a bit in later kernels, I regularily used hard drives whose capacity exceed the limits of the bios. I still have a dual cpu 223Mhz mother board that could only see hard drives of less than 8Gb capacity. The last time it was running it had 3 40Gb drives that worked with zero problems.

Jim

---

### Post by Vegan on 2008-11-21
The BIOS when I put a disk > 137 GB reports 137 GB of space. With Windows installed, it will recognize the remaining space and let you make an extended partition.

Linux is minuscule compared to Windows and was wondering if I could use a minuscule boot partition and the rest for Linux.

The old IBM is a Pentium III, click on the IBM and it is linked to the manual.

:guitar:

---

