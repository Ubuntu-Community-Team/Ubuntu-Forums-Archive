---
title: "Boot error with external journal!"
date: 2010-08-28
forum: Server Platforms
---

### Post by galactus51 on 2010-08-28
Hello, I will try to be clear, sorry about my english.

My system has 5 hard drives. On my hard drive where the system is, I have an ext4 partition with external journal. The system is on /dev/sda1 and the external journal on /dev/sdb1!
So far so good. The problem is that when adding a new hard drive, the system gives the following errors:

Fatal error on ramswap and on initramfs!

I do use two kernels! The official Ubuntu 10.04 64bits 2.6.32-24-generic and an experimental kernel - Omnislash  2.6.34. With the experimental kernel the error occurs when I put a new hard drive on SATA2 port or a disk on the USB port!

With the Ubuntu kernel the error occurs when the disk is on the USB port! No error occurs when I use the SATA2 port!

What could be happening? I have not altered the boot order of the  disks! The system installs and runs normally with external journal with both kernels! The error only occurs when adding a new hard disc!

My motherboard is an Intel DP55KG Extreme with a Core i7!

Any suggestions?

One more thing, my friend with a different Motherboard (gigabyte) have the same erros, but in the two cases I have listed above! With Sata2 port and USB port with Ubuntu kernel!

---

