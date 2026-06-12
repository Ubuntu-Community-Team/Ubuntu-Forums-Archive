---
title: "Getting PCI controller card to work?"
date: 2006-11-04
forum: Server Platforms
---

### Post by shultzjr on 2006-11-04
I have a SuperMicro P5DBE with two P2-400 cpus and 256M of ram.  I has one 3.2G Samsung ide hd connected to the first ide cable.  It has a cdrom connected to the second ide cable and it is set to master.  It also has has one PCI IDE RAID card stuck into the fourth pci slot (left to right looking from the front).  The hardware boot routine sees it and assigns irq 10 to it.  It has two 250G seaget hd's connected to it that I would like to share on my network.  I installed U610.server.i386 on the computer which went ok.  After I log in and get the command line I can type lspci and get:

00:12.0 RAID bus controller: Silicon Image, Inc., PCI0680 Ultra ATA-133 Host Controller (rev. 02)

When I look in the /dev directory there is no hde file that would allow cfdisk or a partitioner to work on the array.
What do I need to do to get this card/hd's to work in Linux so I can partition and put a file system on it?

thanks,
charles.....

---

