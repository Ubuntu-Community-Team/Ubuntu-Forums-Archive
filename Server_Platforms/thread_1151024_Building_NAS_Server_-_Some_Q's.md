---
title: "Building NAS Server - Some Q's"
date: 2009-05-06
forum: Server Platforms
---

### Post by spelunker on 2009-05-06
I'm interested in building a NAS server because a) we need a big hunk of storage space and b) I'm really interested in how its done.
I have a few questions regarding hardware selection and actually setting up the machine. Be gentle as I'm relatively inexperienced but willing to learn.

First, I want to build a machine where I can have 8TB of space, with RAID 5 or 6 protection. So this means I need 9 or 10, 1 TB drives. Where would I find a box that could hold so many drives and do I need to look for any special hardware? Would it be better to set up a hardware or software raid?

Second, I want to offer this up as a NFS mount for my server. Currently, we have 1 server and a NAS server (SNAP server) with a few 100 GB of space. This is all ext3. Does it make a difference if I make this new build ext4 to take advantage of the features? We'll want to backup the snap server onto this new server along with other data files, but will there be any issue with copying the data from the snap server (ext3) to the new build (maybe ext4)? I'm a little unsure of how this works.

Any guidance that can be offered up is greatly appreciated.

One other thing, I've looked at FreeNAS but want to stay with ubuntu as I'm more familiar with it.

---

### Post by andrewc6l on 2009-05-06
I had trouble finding servers that had enough drive bays. I eventually ended up going to NewEgg and just doing the "Advanced Search" under computer cases. I'd recommend you go for external 5.25" bays, and then get mobile racks (removable drive enclosures) for the hard drives - when a RAID drive dies, you don't want to have to bring the server down. Get one or two extra drive bays (and drives) so you don't have to build the OS on RAID - that will make your life easier.

As for hardware or software: I ended up getting a RocketRAID card - but I don't recommend them, since their Linux integration is pretty poor. It's also just "software RAID on the card" and not real hardware RAID. If I had it to do over, I'd go with either a really good ($$$) RAID card, or if Ubuntu supports software RAID and hot-swapping of SATA drives, I'd be inclined to do that.

When you build the NAS, you can use either ext3 or ext4. If you decide to do software RAID, I'd suggest ext3 - just because it's been tested longer.

Finally, don't forget backup. I built my RAID array with 4 250G drives, which backs up nicely onto a 750G drive - but 8TB is likely to cause you trouble :-)

---

### Post by windependence on 2009-05-07
There are many cases that will support 13 or more drives. If you want, I can probably supply you if you can't get them where you are. I have quite a bit of experience with this and I would use a real hardware card if you can. Adaptec makes a few good ones even though they aren't so great at sharing their code, the cards work great with Linux and BSD. 

Personally, I use FreeNAS for this type of thing because it's easy to install and even easier to administer. It also will serve up NFS, SAMBA, iSCSI and others without a problem. You can even set up software RAID right in the FreeNAS software. I have one set up in RAID 5 and it has been up for over a year. You can even monitor the drive temps and other things through the web interface.

-Tim

---

