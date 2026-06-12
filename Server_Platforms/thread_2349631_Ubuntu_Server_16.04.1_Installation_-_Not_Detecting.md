---
title: "Ubuntu Server 16.04.1 Installation - Not Detecting USB SSD"
date: 2017-01-16
forum: Server Platforms
---

### Post by davzd on 2017-01-16
Hi there. I'm trying to do a straight install of Ubuntu Server 16.04.1. However, the installation program doesn't seem to recognize the drive on which I want to install, which happens to be an SSD in a USB dock.

I had been running Ubuntu Server 16.04.1 from that SSD for some time. However, I did that by cloning an existing SATA drive that was connected directly to a SATA port on the motherboard. In any event, something blew up with that installation and I decided after quite a bit of effort just to give up and to try reinstalling it from scratch. But the installer doesn't show me the drive as an option.

The somewhat odd part about all of this is that when I boot up a Ubuntu 16.04.1 Desktop live USB, it sees the SSD just fine. Same when I boot to a boot-repair live USB. Both times, it shows up and I can read and write to it. However, it's nowhere to be found when I try to install Ubuntu Server. I've already tried going into the shell during the install process - fdisk -l doesn't show the SSD.

I suppose I could perhaps just install Desktop instead, but the box is a server, so I'd prefer to install Server. Just thought I'd take the liberty of asking here in case I'm perhaps missing something obvious.

---

### Post by TheFu on 2017-01-17
ubuntu server doesn't install all the drivers normally used by desktops.  There is a package with those. Sorry, I don't remember the name of that package.

Also, many disks are GPT, so fdisk doesn't work correctly. Use parted/gparted instead.  Also, when partitioning , parted/gparted will automatically align the sectors correctly.

---

### Post by efflandt on 2017-01-17
What sort of dock is the SSD in and does it provide power (of required voltage) to the drive?

I have an external dual drive dock that can connect with eSATA or USB (2.0 I think, but that is all my PC has). Its PSU only provides 12v and 5v. When I put mSATA SSD card in a 2.5" SATA adapter (which also has a miniB USB port on it) I cannot even see it in the dock from the dock connected with USB (in which case the dock is seen in lsusb, but nothing drive in dmesg) or if the mSATA adapter is connected with its own miniUSB with a cable with dual USB plugs for more power. That is probably because the mSATA is 3.3v 1.7a max and maybe the older dock does not have a 3.3v regulator.

When I put a regular SSD that uses 5v 1a max in the dock, for some reason I get drive errors when connected by eSATA, but it works fine without any issues connected with USB. Large or laptop Mechanical drives work fine with the eSATA connection.

See if anything shows up about the dock in **lsusb** and anything about the drive in **dmesg**.

You also say that you cloned the drive. Maybe it is an issue of 2 partitions with same UUID. See what **sudo blkid** lists when it is connected.

---

### Post by davzd on 2017-01-18
Ah, thank you very much TheFu. I did a bit of googling and I suspect it's the linux-image-extras package. Will give it a try to see if it work.

Also appreciate the suggestion regarding parted. In this case, I know the disk is not GPT but will keep it in mind.

---

### Post by davzd on 2017-01-18
Thank you efflandt - I appreciate the info. That being said, I don't believe the dock type or power is an issue, insofar as it had been running previously, and booting to other Live USBs allowed me to see the drive.

---

### Post by TheFu on 2017-01-18
Partition alignment applies to all disks - MBR and GPT. Performance could be worse by 20-30% if misaligned. If they have 4K sectors, it is easiest just to use parted/gparted for all partitioning rather than do the math correctly to get the alignments all correct. [https://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

---

### Post by slickymaster on 2017-01-18
Thread moved to **Server Platforms** which is probably a better fit.

---

### Post by davzd on 2017-01-18
Thanks again TheFu - most appreciated and interesting info - I was not aware of that. That being said, for this particular exercise, I hope to use the existing partitions and if at all possible preserve as much of the existing info on them as possible. Really the only thing that I think is broken is something in the boot process, but since my efforts in recovering from that have been for naught, I'm resorting to reinstalling.

---

