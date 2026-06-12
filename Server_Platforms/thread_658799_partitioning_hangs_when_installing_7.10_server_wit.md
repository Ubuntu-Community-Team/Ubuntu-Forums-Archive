---
title: "partitioning hangs when installing 7.10 server with 3Ware SATA RAID"
date: 2008-01-05
forum: Server Platforms
---

### Post by gradedcheese on 2008-01-05
I'm trying to install Ubuntu 7.10 server on a new Asus box.  It has a 3Ware SATA controller installed that provides real hardware RAID, and I have two 500GB disks set up in a RAID-1 (mirroring) via the card's BIOS.  

My problem is that, in the installer, the partitioning step hangs at 33% when trying to make the / partition.  The installer does see one 500GB volume, like I expect.

I tried the following:

1) disabled ACPI in the BIOS.  This really messes things up in that it makes the motherboard's network interfaces not work in the installer.  I'm doing PXE boot (which works) but the installer can't get a DHCP address, and configuring them manually doesn't work.  Then I can't proceed to install.

2) enabled ACPI in the BIOS, but ran the Ubuntu installer with "install acpi=off", this seems to do the same thing as before (ie: I get to formatting partitions and hang at 33%)

In case it's useful, the motherboard is an Asus P5M2-M/RS100-E4, it has two Broadcom NICs and an onboard soft SATA RAID that I'm not using at all.  The controller is a 3Ware 9650SE.  This motherboard uses an Intel CPU, and I'm installing the 32-bit version of Ubuntu rather than 64-bit.

Does anyone have suggestions on what to try next?  Thanks!

---

### Post by gradedcheese on 2008-01-06
Hmm... no one has run in to this?  7.10, 3Ware 9650SE controller?  Anyone? :)  

google searches aren't turning up much, aside from the 9650SE being supported in 2.6.22 mainline, so I'm guessing this is some sort of issue with my motherboard but I'm not quite sure where to look aside from the usual suspect (ACPI).

---

### Post by gradedcheese on 2008-01-06
I dropped to the shell in the installer and found that the correct 3w-9xxx module for my controller is loaded, so really this should be working.  My next experiment is to not use the installer's partitioning step by doing it manually via fdisk and mkfs.ext3

EDIT: ah, mkfs.ext3 on my 500GB disk works from the shell, it just takes a really long time.  It looks like the installer doesn't 'hang', it just really takes this long to format the disk, the progress bar just doesn't get updated.  I can still switch to another console and see that a mkfs.ext3 process is running, so I suspect the installer is doing the right thing and that I was just overreacting.

EDIT: yep, that was it.  Wow, I sure feel stupid.  :( "33%" is the progress shown the whole time, meanwhile mkfs.ext3 is working correctly, as are all the other steps.  Wait long enough, and the installation proceeds normally.  I guess there's some problem with the progress bar.  Ah well.

---

