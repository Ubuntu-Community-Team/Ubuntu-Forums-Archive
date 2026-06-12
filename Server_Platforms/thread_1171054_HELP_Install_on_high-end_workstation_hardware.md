---
title: "HELP: Install on high-end workstation hardware"
date: 2009-05-27
forum: Server Platforms
---

### Post by jps0 on 2009-05-27
Re-Posted, with permission, from a different sub-forum...

I am currently building a high-end workstation for a client who originally spec'ed Win XP 64-bit, but now also wants to dual-boot with Ubuntu or Kubuntu 64-bit as well. I am a few years removed from regular linux support, so I wanted to see if there would be any "GOTCHAs" I should watch out for with the following hardware:

MOTHERBOARD: Supermicro X8DAi
CPU(s): 2 x Xeon 5540 (2.53GHz)
RAM: 48GB (12 x 4GB) Crucial DDR3 ECC/Registered
VIDEO: Basic nVidia GeForce 9400 GT
RAID Controller: Areca ARC-1680IX-12 (4GB)
BOOT ARRAY: 2 x [Fujitsu MBA3073RC 73.5GB SAS HDDs ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822116057")(RAID 1)
SCRATCH ARRAY: 2 x [Fujitsu MBA3300 MBA3147RC 147GB]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822116058") SAS HDDs (RAID 0)
STORAGE ARRAY: 4 x WD RE3 WD1002FBYS 1TB SATA HDDs (RAID 10)

I am intending to do a basic desktop install of the 64-bit version of Ubuntu or Kubuntu. is desktop what I should go with or would it be better to go server and then add on the bits I need. The workstation is a pure number cruncher - it will not be a true 'server'.

Thanks in advance for your help...

---

### Post by netztier on 2009-05-27
> **jps0 said:**
> 
I am intending to do a basic desktop install of the 64-bit version of Ubuntu or Kubuntu. is desktop what I should go with 

yes

> **jps0 said:**
> 
or would it be better to go server and then add on the bits I need. 


no.

The main difference between server and client is in the kernel's tuning parameters, and the second difference is the set of software packages that come with the default install. If you choose to add an Apache webserver, you get the very same piece of software, regardless if you add it to a Server or a Desktop default installation.

The though nut might be the RAID controller, though. A quick google search shows that support seems to be available.

One dualbooting gotcha is always: choice of file system on the scratch/storage array. Linux *can* read and write NTFS, but it's not it's "native" file system - there's always the chance of slight incompatibilites and interoperability issues. FAT32/vfat is probably not the filesystem of choice for such large filesystems anyway. You'll have to think of something or make the system's owner aware of these issues.

regards

Marc

---

### Post by jps0 on 2009-05-27
> **netztier said:**
> yes



no.

The main difference between server and client is in the kernel's tuning parameters, and the second difference is the set of software packages that come with the default install. If you choose to add an Apache webserver, you get the very same piece of software, regardless if you add it to a Server or a Desktop default installation.

The though nut might be the RAID controller, though. A quick google search shows that support seems to be available.

One dualbooting gotcha is always: choice of file system on the scratch/storage array. Linux *can* read and write NTFS, but it's not it's "native" file system - there's always the chance of slight incompatibilites and interoperability issues. FAT32/vfat is probably not the filesystem of choice for such large filesystems anyway. You'll have to think of something or make the system's owner aware of these issues.

regards

Marc

Thanks for the feedback and tips.  Filesystem compatibility I am aware of and if the end-users do opt to user Linux the majority of the time, I will likely throw a dedicated hard disk in for Linux usage that is separate from the RAID 10 subarray.

---

