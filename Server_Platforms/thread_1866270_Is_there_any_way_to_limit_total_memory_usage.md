---
title: "Is there any way to limit total memory usage?"
date: 2011-10-21
forum: Server Platforms
---

### Post by chrisjsmith on 2011-10-21
I've got a beasty 16Gb x64 machine and I want to test our current software against 4Gb of memory instead, preferably without yanking 12Gb of RAM out of the box.

Is there anything I can supply the kernel with at boot that says "use only 4Gb of RAM"?

---

### Post by newbie-user on 2011-10-21
I don't know if you could actually do that inside the OS itself, but you can certainly do that using virtual machines in VirtualBox or VMware.

---

### Post by ian dobson on 2011-10-21
Hi,

I think there's a kernel command line parameter you can set to limit/reduce the maximum amount of memory that the kernel sees.

Have a look at the highmem= parameter or maybe 

max_addr= n

max_addr: Cause the kernel to ignore all physical memory greater than or equal to the physical address n

Regards
Ian Dobson

---

