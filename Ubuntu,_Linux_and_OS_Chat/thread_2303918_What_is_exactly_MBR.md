---
title: "What is exactly MBR?"
date: 2015-11-22
forum: Ubuntu, Linux and OS Chat
---

### Post by Xayide on 2015-11-22
Hello everyone. First of all I don't know if this post should be into General Help but I don't know which thread fits it the most. 
And excuse my english too, it's not my native.

The question is: what is exactly MBR? I've read that it's a way of building partitions, and that there are two primary ways: MBR and GPT. I know GPT is newer and that's all I know about this. But I have also read that when booting a Linux machine, after the POST is executed (executed? loaded?), the Boot Sector is searched and it contains a program called MBR (LILO) that executes automatically. If your partitions are using GPT, the Boot Sector contains the GPT program or is this MBR a different MBR than the partitioning thingy? 

Thank you in advance!

---

### Post by grahammechanical on 2015-11-22
MBR = Master Boot Record.

GPT = GUID Partition Table

GUID = Globally Unique Indentifier

GPT is part of the UEFI (Unified Extensible Firmware Interface) boot system. MBR partitioning is part of the BIOS (Basic Input Output System) boot system. Although it is possible for BIOS machines to use GPT partitioning.

POST = Power On Self Test.

After POST the motherboard will follow the settings in the BIOS/UEFI as to where to look for an Operating System. If it finds a boot loader in the boot sector (MBR) of the disk it will load the boot loader.

The MBR not only contains code that runs as a boot loader but information about the partitioning system. UEFI & GPT systems do things a bit differently. Which is the point where I say - Wikipedia and good night.

Regards.

---

### Post by Bucky Ball on 2015-11-22
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by oldfred on 2015-11-22
Even gpt has a protective MBR, just so older partition tools like older versions of fdisk see one large gpt partition and not a blank disk. 

 MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)
      
 [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

