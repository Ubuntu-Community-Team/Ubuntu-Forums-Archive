---
title: "Ubuntu sees only 1 cpu in 2 cpu dell server"
date: 2005-12-28
forum: Server Platforms
---

### Post by vinjvinj on 2005-12-28
I look under /proc/cpuinfo and see only 1 cpu. How can I have Ubuntu recognize the other cpu and the kernel support SMP?

Thanks,

VJ

---

### Post by kejar31 on 2005-12-28
just apt-get the smp kernel

---

### Post by psusi on 2005-12-28
Are you sure it has to actual CPUs?  I believe that Dell ships their desktop systems that support hyperthreading with it disabled in the bios.  

If it actually has two cpus, yea, install the smp kernel.

---

### Post by DevilsAdvocate on 2005-12-28
Even if your chip is one that has Hyperthreading, after you enable it in the BIOS, grab the SMP kernel.  It will recognize HT as 2 CPU's as well as actually haveing a dual core or 2 CPUs.

---

