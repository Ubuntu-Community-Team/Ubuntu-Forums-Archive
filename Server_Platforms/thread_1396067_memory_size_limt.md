---
title: "memory size limt"
date: 2010-02-01
forum: Server Platforms
---

### Post by dd1313 on 2010-02-01
Hi GUys

What is the maximum memory Ubuntu 8.04 server can see.

Thanks
Dev

---

### Post by kiranmurari on 2010-02-02
Hi,

32-bit system has an address space of 0-(2^32 - 1) so it can support upto 4GB. If you have a 32-bit system, then 4GB of RAM is supported.

The Linux kernel includes full PAE support starting with version 2.6, enabling access of up to 64 GB of memory on 32-bit machines. A PAE-enabled Linux-kernel requires that the CPU also support PAE.
   
The maximum memory space for 64-bit system is 256TB (2^48 bits). Theoretically, 64-bit system support much higher RAM, 64 exabytes. But no chipset in the market actually decodes more than 48 bits of address
See: [http://en.wikipedia.org/wiki/X86-64#Virtual_address_space_details](http://en.wikipedia.org/wiki/X86-64#Virtual_address_space_details)
[URL="http://en.wikipedia.org/wiki/X86-64#Virtual_address_space_details"]
[/URL]

---

