---
title: "Booting from a Hardware RAID 5 System?"
date: 2010-01-26
forum: Server Platforms
---

### Post by statikeffeck on 2010-01-26
(Posting because I could not find much information about booting up on a RAID system with a custom driver)

I have a RocketRAID 2640X4 PCI Express card with three 750GB Sata drives connected in a RAID 5 setup.

I have a 250GB SATA drive connected to the mainboard SATA, on which I installed Ubuntu Desktop 9.10. I did this because I didn't want to deal with trying to install to the RAID array from scratch, so I can work on getting the driver working on a full operating system. 

I compiled & installed the manufacturer's driver from source, used insmod to insert the module, and the RAID array shows up as a nice 1500 GB of usable space. I can create partitions and copy data to/from.

I'd like to copy my old server programs & data (a Fedora system) directly to the RAID array and directly boot off of it.

However, now I'm thinking this is not a good way of migrating a system especially since the old system is 32-bit and the new one is 64-bit. But I just don't know enough about inserting a kernel module into a dormant system to do this anyway.

So, Question 1 is: whats the best way to configure the kernel, such as loading required modules, on a system that isn't booted? 

Assume that I have a fully updated & working system on a single SATA drive, and I just purchased a RAID card for which I would like to use as my full system, and boot from.

---

