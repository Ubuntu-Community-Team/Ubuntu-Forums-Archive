---
title: "Predetermined State Computing"
date: 2021-08-09
forum: Security
---

### Post by shawn2021w on 2021-08-09
I've had this idea of making computing faster or what a friend called a version of Turing computing for a modern day computer. 

Mainly, the idea is based on utilizing the ECC-RAM utilized nowadays in servers to be able to predetermine the state of a computer through directly interacting with the system OS itself. The computations would be carried out by the CPU and then a bootable OS would work from the ECC-RAM. The CPU would then upload values into the OS based in the ECC-RAM directly and would enable a very secure Linux OS environment. 

One application stands out, called TimeShift is of utility to this idea in Debian Linux.

Altering that program would enable imputing predetermined values from the CPU into the OS through the ECC-RAM, or even with a little work it could be possible to directly boot an OS into the RAM and then alter it with TimeShift inside the ECC or non-ECC-RAM. 

It's a simple patentable idea for enhancing security of an OS or speeding up computations significantly. Let me know what anyone thinks or where this should be posted on the internet? Thanks.

---

### Post by CharlesA on 2021-08-12
That's called booting the OS to a ramdisk. However, you still need store the files someone for them to be loaded into memory, maybe booting via pxe or something.

---

