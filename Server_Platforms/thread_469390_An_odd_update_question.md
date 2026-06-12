---
title: "An odd update question"
date: 2007-06-09
forum: Server Platforms
---

### Post by Dudsmacka2 on 2007-06-09
I'm the lead admin of a LAN-Party organization.  Recently we have started to build a server farm that we use for our events, which basically consists of a rack and 10 racked servers, ranging from high-end pentium w/ HT 4's, Pentium d's, and Core 2's.  Each server has mobile hard-drive removable trays.  The idea is rather than taking the server home to update game files we just pull out the hard drive.  We are considering of moving all our servers to ubuntu server edition from their various operating systems (some are running windows server - some are running cent os).

When we take the hard drive out and back for an update it is put into a machine having very little (if anything) with the machine it was pulled out of.  Would it be possible to update the operating system in this manner?

The rack is kept in storage in such a way that SSH is not a viable option.  The only time we really have access to the machine is during events.  The other option would be to dis-assemble the rack and transport them home.

---

### Post by Reugen on 2007-06-17
If the hardware on your machines at home is close enough to the server hardware you should be able to boot them, although you may want to use pre edgy because they started using uuid instead of filetree locations and if you switch compys wth the hard drive the uuid of the drive and partitions will be different.  You also could optionally just change the locations in  /etc/fstab and grub to filetree locations instead, and then use edgy or feisty.  As far as accesing the disk from another os i don't know of a way of updating the os without breaking things.

---

