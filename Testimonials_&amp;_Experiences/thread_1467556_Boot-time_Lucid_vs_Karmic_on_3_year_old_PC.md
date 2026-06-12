---
title: "Boot-time: Lucid vs Karmic on 3 year old PC"
date: 2010-04-30
forum: Testimonials &amp; Experiences
---

### Post by DawieS on 2010-04-30
I have just measured boot-times on both Karmic and Lucid, since I have both installed. Times are measured from pressing 'Enter' at the Grub menu, until completely booted into the desktop (I don't have a login screen, since I am the only user on my PC).

I am using a 3 year old Gigabyte S-series Dual-Channel DDR2 Motherboard with AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ and 3 GB RAM.

Ubuntu Version ____ Karmic________ Lucid

Boot-time_(sec)____ 28____________ 15

Version___________ 32bit__________ 64bit

Kernel____________ 2.6.31-21______                2.6.32-21

Disks_____________ Internal________ External
                                 _________________ Seagate 320GB__     Seagate 1TB
_________________ Sata2__________                        Sata2
_________________ 7200 rpm_______               7200 rpm     

File system________ ext3___________                          ext4

As can be seen from the table, the boot-time with Lucid has nearly decreased by 50%. Disk reading speeds are similar, and both installations are on the first partitions (most outer edge of disks). Part of the improvement can be attributed to ext4 being faster than ext3.

It would be interesting to see the boot-time for Lucid using a Solid State Disk!:smile::smile:

---

### Post by bhaverkamp on 2010-04-30
I think this all attributeable to the lucid boot speedup and nothing due to ext4. I have been using ext4 in karmic as well and see similar or better speedups. I don't think ext4 effect boot times at all. Most of the speedup optimizations have to due with disk writing. Booting is mostly reading.

---

