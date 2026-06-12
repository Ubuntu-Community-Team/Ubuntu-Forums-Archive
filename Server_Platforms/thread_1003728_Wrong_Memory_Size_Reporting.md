---
title: "Wrong Memory Size Reporting"
date: 2008-12-06
forum: Server Platforms
---

### Post by OfMacandMen on 2008-12-06
I have a Ubuntu 8.10 loaded on an Intel Board with 4Gb (4 x 1). When I check the System Monitor or 'free -m" it only reports 2.5GB. The BIOS verifies 4GB on boot. 

??

---

### Post by Maverick321 on 2008-12-06
If your only running 32-bit it is normal for the operating system to not see the entire 4gb of RAM.  You can only have 4 GB of address space to work with and devices such as keyboard/mouse all the way to your video ram needs a address for it to communicate with the system.  If you want to use all 4GB you will have to run a 64-bit operating system.

---

### Post by OfMacandMen on 2008-12-06
As per [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

A 32-bit computer has a word size of 32 bits, this limits the memory theoretically to 4GB. This barrier has been extended through the use of 'Physical Address Extension' (or PAE) which increases the limit to 64GB although the memory access above 4GB will be slightly slower.

A a 64-bit computer will be able to address up to 16.8 million TB (16 exabytes) although constraints are in place that limit this to around 1TB.

---

