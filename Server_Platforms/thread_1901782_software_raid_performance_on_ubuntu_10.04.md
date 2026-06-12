---
title: "software raid performance on ubuntu 10.04"
date: 2011-12-29
forum: Server Platforms
---

### Post by dsi_me on 2011-12-29
Dear all,

Has anybody evaluated the extra CPU and RAM usage required on a ubuntu server if software raid is enabled? Basically i want to understand how much processing power I will loose per server if we use software raid instead of hardware raid.

---

### Post by rubylaser on 2011-12-29
mdadm will have very little impact in terms of CPU / RAM use except when it's doing a re-sync.  Modern CPU's have no problem handling parity calculations for a RAID array.  

The main difference you'll see vs. a hardware array is the lack of write cache, so it's writes are not typically as fast as a hardware controller. Even on an older AMD 240e processor with 2GB of RAM, I could still easily saturate a gigabit connection with my ( 8 ) disk RAID6 array.

Hardware RAID is typically faster, but you are locked into that hardware, and the cost for entry is obviously much higher than the free price of mdadm.

---

### Post by SeijiSensei on 2011-12-29
> **rubylaser said:**
> The main difference you'll see vs. a hardware array is the lack of write cache, so it's writes are not typically as fast as a hardware controller. Even on an older AMD 240e processor with 2GB, I could still easily saturate a gigabit connection with my ( 8 ) RAID6 array.

I agree with rubylaser that you'll see little if any degradation of performance with software RAID.  I haven't had the same problem with writes as he describes, but I'm generally running two-drive RAID1 systems where the penalty would be much smaller than on an eight-drive RAID 6.

---

### Post by rubylaser on 2011-12-29
Yes, and RAID0/1 in software should in theory be just as fast as a hardware controller, because there are no parity calculations involved.

---

### Post by jchung on 2011-12-29
To give you an idea... I have a file server at home where I have two mdadm arrays created. One is ~ 6TB (8 drive RAID 6 array) and the other is ~ 9TB (4 drive RAID 5 array).

I use a Intel(R) Celeron(R) CPU G530 @ 2.40GHz dual core processor & 4GB RAM.

I have no problems getting ~ 600MB/s reads and ~ 450MB/s writes to the 6TB array.


Joo

---

### Post by rsvancara on 2012-01-01
Plus you will benefit from not being locked into a proprietary RAID controller scheme.  For example, if your hardware RAID controller dies five years from now, good luck finding a replacement.

---

### Post by nirvanaraj on 2012-03-15
Successfully done Software RAID 1 (Mirroring) and also checked with each hard disk removed.

My system specs:

Intel Pentium 4
RAM : 2 GB
2,160 GB IDE Seagate Hard Drives used 

Suggestions to those who are trying RAID 1 for the first time:

1. If u have **SATA** drives, make sure you are connecting them to SATA ports in Motherboard and not **E-SATA**.
2. Please do not do any modifications in the **BIOS**, because there are some options for **RAID** in BIOS.
3. Read only the below link or any link which is from Ubuntu forum sites and not any other crap website.
    [https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)
4.After reading the step by step installation guide from the above link, be very careful when you get the     
    partitions step and please re-refer each step and do your installation.
5.Always first create **swap** partition and then **root** partition, respectively do for raid devices.
6.Do not forget to give **mount point** and **partition** for RAID devices.
7.When your making any changes and you have "Done setting" option, please enter that or else your changes will not get saved.
8.DO THE WHOLE PROCESS VERY VERY SLOWLY, DONT BE IN A HURRY.
9.After the whole installation is done, restart the pc and it will take some time to boot(depending on your hardware).
10.If your getting server login, then your installation is proper but still you need to check whether raid works or not.
11.Now, after logging in type the following command
# cat /proc/mdstat

if your getting 2 raid devices then your mirroring is complete and perfectly done.
12.Still if you want to check manually then, create a folder in any directory
13.Now remove one hard disk, and boot, you will find the folder.
14.Repeat the step with another hard drive and if you still find the folder, then your verification is complete.

---

