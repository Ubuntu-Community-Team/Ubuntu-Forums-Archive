---
title: "large memory supported by default kernel of 6.06"
date: 2006-08-30
forum: Server Platforms
---

### Post by zealubuntu on 2006-08-30
We recently purchased a PowerEdge6800 with 32GB RAM. The processor of the machine is the Intel Dual-Core XEON 3.00GHZ. We installed the ubuntu 6.06 server version for x86 on the machine. 

The kernel version is 2.6.15-26-server #1 SMP 

I checked the /proc/meminfo, the memory is recognized as 32GB. However, normally the 32-bit system can only supports up to 4GB address space. In our case, does the default ubuntu 6.06 kernel has the large memory support enabled? If so, does that mean the OS can actually handle the 32GB RAM? Is that possible for user application to also address more than 4GB memory?

Thanks.

---

### Post by leexgx on 2006-08-30
user applications norm can only adresss 4gb max if 32bit

64bit programs have no limit (maybe 2TB of ram i think?)

---

### Post by Woei on 2006-08-30
> **zealubuntu said:**
> We recently purchased a PowerEdge6800 with 32GB RAM. The processor of the machine is the Intel Dual-Core XEON 3.00GHZ. We installed the ubuntu 6.06 server version for x86 on the machine. 

The kernel version is 2.6.15-26-server #1 SMP 

I checked the /proc/meminfo, the memory is recognized as 32GB. However, normally the 32-bit system can only supports up to 4GB address space. In our case, does the default ubuntu 6.06 kernel has the large memory support enabled? If so, does that mean the OS can actually handle the 32GB RAM? Is that possible for user application to also address more than 4GB memory?


The feature that's enabled is called PAE, Physical Address Extension. It allows for a 32-bit CPU to address up to 64Gb of RAM, and has been a standard feature since at least the Intel Pentium II. It usually incurs a slight performance hit due to the use of so called 'bounce buffers' which are necessary to let older devices like 32-bit PCI cards and ($deity forbid) 16 bit ISA devices to still make use of the available memory. An AMD64 has an advantage here, since it has hardware support to do this copying through a so called IOMMU device. Intel CPU's do not have this, as the IOMMU was not in the specification AMD originally released to the public to solicit feedback, and Intel implemented the older spec. Moreover, since the Xeon does not have an integrated memory controller, the IOMMU would have had to be implemented on the chipset. So with an AMD64, you will not incur a measurable hit on I/O bandwith if you're using older PCI devices (NIC, IDE, USB2) that can't address all available memory.

User applications still cannot address more than 4Gb of RAM each, and due to bounce buffers, it's usually a bit less even. Go with a full 64-bit version of Ubuntu if you have processes that require more than 4Gb of memory.

---

