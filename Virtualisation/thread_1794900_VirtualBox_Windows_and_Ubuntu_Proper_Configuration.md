---
title: "VirtualBox Windows and Ubuntu: Proper Configuration?"
date: 2011-07-01
forum: Virtualisation
---

### Post by slowtrain on 2011-07-01
I'm about to get a new i7-2600 machine at work and am trying to figure out how best to arrange my OS's and hard disk partitions.  Am thinking about putting Windows (already on the system) and Ubuntu on separate partitions but for now mostly running Ubuntu (from the disk partition) via VirtualBox in Windows.  Would love to get people's views on whether this is a good approach.

All the new hardware is likely not to play nice with a pure Ubuntu OS--am guessing that sleep, hibernate and so forth would crash the machine, and the new graphics card and other components may not work.  Will of course check with a flash boot disk.  It's also good to have Windows around for some purposes.

So, I suspect I will need to run Windows to be able to fully use the machine's hardware.  With time Ubuntu may be able to handle the machine's hardware and so I'd like to be able to switch to pure Ubuntu.

So some things I'm wondering:  Does anyone else have an arrangement like this?  Does it work & are there any drawbacks?  Anyone know whether mapping (Oracle) VirtualBox to the Ubuntu disk partition rather than a virtual hard disk will cause problems when I upgrade VirtualBox?  Any advice on what software to use to set up something like this?  The machine will come with Windows.  I'll need to repartition the disk.  Guess I could use gparted from a live flash drive, but last time I used gparted, it created an overlap between partitions which apparently could be a serious problem.  And, anywhere I can find out how to set up a dual-boot windows / ubuntu machine?  I wonder whether grub2 could be used.  As for mapping the Ubuntu partition to VBox, I've seen some instructions here (hope they are good ones!):  [http://www.sysprobs.com/access-physical-disk-virtualbox-desktop-virtualization-software](http://www.sysprobs.com/access-physical-disk-virtualbox-desktop-virtualization-software)

---

