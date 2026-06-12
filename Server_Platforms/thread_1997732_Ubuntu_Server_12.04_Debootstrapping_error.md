---
title: "Ubuntu Server 12.04 Debootstrapping error"
date: 2012-06-05
forum: Server Platforms
---

### Post by wboyd on 2012-06-05
I am in the process of trying to install Ubuntu Server 12.04 on a Dell Powervault 770n.  I get to "Installing base system", but the install craps out with "Warning Debootstrapping error" - I continue through, but it keeps going back to the install options and restarts the process all over again to the same result.

I have tried using several different cd's for the install, fresh download and a different cd rom drive (which is a pain because the old machine does boot via USB)

I tried disconnecting the network and configuring it manually (later).  I have checked and re-seated cables and memory, etc.

Could it be an issue that I am overlooking on the ISCSI array?  the machine has a total of 8 drives - 2 for the OS (18 GIG each) and 6 for storage - has Adaptec controllers and PERC array manager.  

RAID levels are RAID 0 (Disk Striping), RAID 1 (Disk Mirroring), RAID 5 (Disk Striping with Parity), 
RAID 1+0 (Striped mirrors – Direct attach JBOD only), RAID 5+0 (Direct attach JBOD only)

I feel like I have tried everything and exhausted all my resources...

Can anyone offer some words of wisdom?

Thanks,
Wayne

---

### Post by wboyd on 2012-06-06
Bump!!!

---

