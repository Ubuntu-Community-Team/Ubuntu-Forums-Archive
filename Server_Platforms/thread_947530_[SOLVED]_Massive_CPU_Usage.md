---
title: "[SOLVED] Massive CPU Usage"
date: 2008-10-14
forum: Server Platforms
---

### Post by ocr14a on 2008-10-14
Hi Guys. 
I have a problem (I think). 
I've noticed that since installing a copy of Ubuntu Server (the latest available: 8.04) in a new VM, it's using the CPU like it's going out of style. 

I will list the details here and upload some screenshots. 
What do you think?

steven

**_Core hardware_**
Brand/Model of Server: Dell PowerEdge 2900
HD: 800 GB RAID 5
RAM: 8 GB (I know, I want more, but...)
CPU: 2 quad core 64bit Xeons @ 1.6 GHz

**_Core Virtualization system_**
VMware's ESX Server version 3.5

**_the VM_**
RAM: 512 MB
CPU: 1
NIC: E1000
SCSI cntrlr: LSI (best match for the actual hardware)
HD: 4 GB

**_the OS_** 
(installed via ISO attached as CD-ROM drive within ESX configs) 
Ubuntu 8.04 LTS Server Edition - Supported to 2013
64bit AMD and Intel computers

**_other installed software_**
ebox (as per Ubuntu documentation)
nothing else yet

---

### Post by ocr14a on 2009-01-05
Well, as I suspected, it was soemthing related to needing updates. 
I finally got the latest round of Dell server firmware and bios updates and ESX updates done and the Ubuntu server VM works fine now.

---

