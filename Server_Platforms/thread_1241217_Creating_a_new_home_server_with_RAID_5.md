---
title: "Creating a new home server with RAID 5"
date: 2009-08-15
forum: Server Platforms
---

### Post by Triptoph on 2009-08-15
So I've got one SDD with Linux loaded on it, and I have 5 1.5TB drives that are not yet connected to the motherboard.  I intend to hook these up in a RAID 5 software array, and use the box as a home file server.

I would love to have the ability to have some specific directories accessible to only some on the network, where they would need to log in somehow, and some folders available to everyone on the local network.  What would be the best way to set that up?

Also, with respect to setting up RAID 5: I've got Linux on a 30GB SSD, so it will be separate from the RAID array.  Can I set this up, and then re-install any flavour of linux on the OS disk without affecting the RAID array?  So long as I set it up properly?

Last question: When one of the RAID disks dies, how would I know about it?  Is there some nice monitoring software out there I could use that could monitor the RAID's current health?  How would I know which drive died so I know which to replace?  

The other computers on the network are connected via a Linksys router ( which happens to be running another flavour of linux! ) connected to computers running XP, Mac OS X, and Vista... just to make things more interesting :p

Appreciate any suggestions / comments!! Part of this is for the learning experience, but I also want to use this server as a place to back up all other systems.

---

### Post by twidget on 2009-09-04
::bump:: for the login stuff try samba. there are tons of how tos out there.

---

