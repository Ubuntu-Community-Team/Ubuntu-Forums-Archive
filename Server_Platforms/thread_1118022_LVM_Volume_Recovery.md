---
title: "LVM Volume Recovery"
date: 2009-04-06
forum: Server Platforms
---

### Post by ProfDecoy on 2009-04-06
Greetings,
I've recently gotten myself into a bit of a pickle.  Recently I had to rebuild a server that had a 3.5TB Hardware RAID Array attached to it.  The array was set up with LVM on RHEL 4 or 5 (don't remember which), long before I was associated with the server in question.

Unfortunately, before the rebuild, I was unable to log in locally to the server to properly export the LVM volume, and the server was never properly backed up (the array was backed up occasionally, but the /etc/lvm files never were backed up).  When I tried brining the LVM volume back into the new server (fresh install of 8.04.2), it wasn't seeing any of the volume information for LVM, and in my attempts to get the physical and logical volumes recognized, I managed to erase the LVM metadata on the array.  The LVM only had a single EXT3 partition in it for the entire size of the array, which I have questioned why it was setup with LVM if it was only going to have a single partition. 

Anyway, right now I am trying to recover the EXT3 partition and the data within the LVM.  I have looked at the array with X-Ways Forensics/WinHEX and the raw data is still there, but it doesn't see the EXT3 partition, just the LVM partition.  So I'm unable to use it to extract the individual files.

I figure that if I can identify the start of the EXT3 partition I can use dmsetup to create a logical device to mount and copy the data off the array.  However, I have been unable to identify the sector were the EXT3 partition starts within LVM, and I'm not all that familiar with LVM and EXT3 to be able to identify the start sector from looking a hex dump of the array.

Does anyone have any suggestions that'd help me accomplish this miracle I'm attempting to pull off?

Thank you.

---

