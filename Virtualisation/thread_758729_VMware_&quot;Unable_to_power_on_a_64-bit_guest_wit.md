---
title: "VMware: &quot;Unable to power on a 64-bit guest with paravirtualization enabled.&quot;"
date: 2008-04-18
forum: Virtualisation
---

### Post by DarkFox.DK on 2008-04-18
I get this error in VMware Server 2 beta when i enable paravirtualization for the guest OS, which is Ubuntu Gutsy server ed. 64-Bit

The host OS is the same.

Have i missed something about 64 bit and paravirtualization or is this something that shouldn't happen and can be fixed?

---

### Post by tribaal on 2008-04-25
I'm having the same problem with a 64bits server guest (8.04).

I couldn't seem to find any place on the web that deals with 64 bits Ubuntu guests... And a quick "grep VMI /boot/config-2.6.24-16-generic" shows no VMI installed for my kernel (a 64bits one)... How comes? 

It is compiled in 32b kernels... Is it on purpose or should I raise a bug?
Thanks a lot!

- Trib'

---

### Post by marcpem on 2008-12-27
Has someone found a solution to this problem ?

I installed the 64-bit version of Ubuntu 8.04.1 server edition on VMware ESXi Udate 3 (which is officially supported). Everything works perfectly, the vmware tools install in no time. But as soon as I turn Paravirtualization on I get this error:

“This kernel requires an x86-64 CPU, but only detected an i686 CPU.”

I did turn on VT on the bios of the host machine. 
Can anybody help ?

---

### Post by JBDynamics on 2009-08-13
I have 3 questions about VMWare and paravirtualization; plus I have listed my setup and specifications for install.

I am attempting an install on VMWare Workstation 6.5.2, trying to install Kubuntu 9.04 (Jaunty) 64-bit Desktop edition on a Intel Extreme 2 Quad with 16GB DDR2-1066. (#1) Does anyone know if x86_64 2.6.28 kernels support paravirtualization?

I have virtualization and XD enabled. I tried to install it yesterday and it stopped at the end of the disk creation, but I should have made a system restart before the install. 

I was attempting a creation of a full 200GB virtual disk (On my secondary 1TB RAID-1 SATA 3GB/s using SCSI SAS) and allocating 4GB RAM. I looked at the VMI Performance scores (they were from a 2.6.20-16 (NO PV) and 2.6.20rc6 (PV) kernel) and there wasn't a significant difference in performance. 

(#2) Should I attempt the install with paravirtualization enabled on VMWare Workstation with 2 processors, or would I be better off not running kernel paravirtualization and buying VMWare Server and running 4 cores? (#3) Which would be better performance for both the host and guest OS's, assuming paravirtualization works on the 6.5.2 Workstation edition of VMWare for Kubuntu 9.04.

If I don't hear back from anyone soon, I will attempt the install with paravirtualization and an incrementing 250GB Max V.Disk.

---

