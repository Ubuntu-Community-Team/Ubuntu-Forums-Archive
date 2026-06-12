---
title: "Installation of Ubuntu 9.04 on IBM HS22"
date: 2011-01-27
forum: Server Platforms
---

### Post by harsha.angadi on 2011-01-27
HI All,

I have successfully installed Ubuntu 9.04 on my IBM HS22 blade server.It is having 2CPU's making it to 16core but its showing only 8core.Its using single processor.Please help me to fix this issue so that my ubuntu installtion is capable of using both the CPU's.

I am searching for 686-smp kernel image to install so that it will enable to use dual processor but unable to search it.

Please help me in this regard.

Thanking in Advance

---

### Post by datamove on 2011-01-27
The issue might be that 9.04 is not supporting the latest Xeon chipsets which you probably have. TRy the following: obtain a 10.4 live CD or/and 10.10 live CD and boot the to see if all the cores are recognized.
Another idea, are you sure of 8 cores per socket? May be you have to turn hyperthreading in the bios to get that?

---

### Post by harsha.angadi on 2011-01-27
> **datamove said:**
> The issue might be that 9.04 is not supporting the latest Xeon chipsets which you probably have. TRy the following: obtain a 10.4 live CD or/and 10.10 live CD and boot the to see if all the cores are recognized.
Another idea, are you sure of 8 cores per socket? May be you have to turn hyperthreading in the bios to get that?

Till now what I  have searched it says that Ubuntu 10.04/10.10 dont support SMP.Any ways I will check the way you suggested.Yes, hyperthreading is Enabled in BIOS.Yes, its 8 Cores.

I m trying to Implement SMP support for Ubuntu 9.04 and I am not sticking to this particular distro any distro is fine.

Thanking you.

---

### Post by datamove on 2011-01-27
SMP is since long supported in stock kernels, so no problems here. I run standard ubuntu 10.10 server on  a 2 x 12 core Opteron HW and see them all. Really, try a newer distro that might support particular new chipsets

---

