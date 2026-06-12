---
title: "I need your help to find the right virtualization solution"
date: 2008-03-06
forum: Virtualisation
---

### Post by the8thstar on 2008-03-06
Hello,

Ever since I've used Ubuntu I've considered several options when it comes to partitioning and toying with different OSes.

I currently dual-boot Vista and U7.10 and have Nexenta Core as a VDI with VirtualBox (doesn't work beyond console though). Since I'm x86, I can't have more than 4 partitions at the same time on my HDD.

I wanted your enlightened opinion on several possibilities I could use on my PC. I own a HP Pavilion dv2000 with a Intel Single Core Solo running at 1.87GHz, 2048Mb of RAM, 74Gb of HDD and a 945GM Intel Express Graphics chipset 128-256Mb. I can dedicate 1024Mb of RAM to the VM and up to 20Gb for one or 10Gb for each if 2VM are installed.

In the attached image, I have laid the options I'm considering. Could you give me your feedback as to which seems to be the most coherent? I mostly use my PC as a 'common mortal' user: I do a bit of Office work, play a few games, use the Internet, archive my music and pictures. Nothing fancy like being a developer, a network security manager or an IT Guru!

Thanks for your feedback!

---

### Post by fjgaude on 2008-03-06
I'm at a loss, what is Nexenta Core?

---

### Post by the8thstar on 2008-03-06
Nexenta is part of the OpenSolaris port to x86 systems. To make it very simple, it's the look-and-feel of Ubuntu, but it's based on Solaris. It's still SunOS UNIX.

---

### Post by lswest on 2008-03-06
and uh, about not being able to have more than 4 partitions on a disk at a time, you can, you just need to take a chunk of it, make it into an extended partition, then make what you need in there such as >  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15040   120801248+   7  HPFS/NTFS
/dev/sda2           18491       19457     7759872    7  HPFS/NTFS
/dev/sda3           15041       18490    27712125    5  Extended
/dev/sda5           15041       15301     2096451   82  Linux swap / Solaris
/dev/sda6           15302       18490    25615611   83  Linux
 (sda3=extended partition, then 5 and 6 are within that partition), so, for example, you could take your ubuntu stuffs and put it into an extended partition (then it's only seen as 2 main partitions out of the 4 you can have), which does mean you'd lose all your information, but that can't be helped, or you can just move ubuntu and the swap, then mount your home again, which frees up an extra partitioning option

otherwise, i'd probably go with the full Ubuntu and 2 virtual machines, or add a virtual machine onto a windows/Ubuntu dual boot (i run Vista and ubuntu as a dual-boot, and have 3 other VMs running in windows for when i test stuff :P)

---

### Post by fjgaude on 2008-03-06
Thanks for the info on Nextenta. Might look into that, if it is free.

Here's mine on one drive:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11495    92333556   83  Linux
/dev/sda2           11496       11988     3960022+  82  Linux swap / Solaris
/dev/sda3           11989       24858   103378275   83  Linux
/dev/sda4           24859       38913   112896787+   5  Extended
/dev/sda5           24859       38336   108262003+  83  Linux
/dev/sda6           38337       38913     4634721   82  Linux swap / Solaris

Using only one Extended partion I remember having nine total partitons on one drive. So as has been said, really, there's no limit to the partitions you can have on one drive: up to four Primaries, or, three Primaries with one Extended and from there add as many Extendeds you wish.

I boot into Ubuntu, and have one to three virtual partitions using VMware server, the free one from their site, vmware, com,  for WinXP and other Linux OSs, as needed for testing. I triple boot Ubuntu versions, 32-, 64-bit Hardy, Gutsy.

---

