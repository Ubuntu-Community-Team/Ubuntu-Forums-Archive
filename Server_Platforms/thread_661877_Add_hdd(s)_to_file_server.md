---
title: "Add hdd(s) to file server"
date: 2008-01-08
forum: Server Platforms
---

### Post by lucas4ce on 2008-01-08
I've got an old P2 computer that was being used as a file server using Freenas, but I've just set it up with Ubuntu 7.10 desktop to be used as a file/web server.

So far I've just set up samba so that two windows machines in the house can see their own idividual home directory to use as they wish (extra storage, backup copies etc).

At the moment the Ubuntu computer only has one 40gig hard drive, and already only has 6gig of space left.

What I would like to do is add storage space.  I've seen a SATA PCI card that I could install giving me access to 4 SATA hdd's when I get them, but to begin with probably just one.  I mention the PCI card because the computer only has IDE connections, and not many of them;)

How do I add this(these) hard drive(s) to the server in a way that will simply increase the storage space, so for example:

**Existing Setup**
Server home directory viewed from windows machine shows:
Size = 40GB
Free space = 6G

**New Setup** (with say 250GB SATA drive added via PCI card)
Server home directory viewed from windows machine shows:
Size = 290GB
Free space = 256GB

I know the numbers above will differ slightly becaucse of a small % of free space kept on the drives, but hopefully you get my drift.

I'm also intersted in RAID, to protect the stored information.  Some of teh information will at some point be streamed to an xbox360 so speed of transfer may become important too.

Any help would be great!!!

---

### Post by maybeway36 on 2008-01-08
You'd probably have to stripe the drives, and I don't really know how. Alternatively, you could use two shares.

---

### Post by fozy on 2008-01-08
Well, to set up a RAID you would need to have the drives on hand; 2 minimum for a RAID 1 and 3 minimum for a RAID 5.  And all the drive should be around the same size.  You might want to look into a LVM which will allow you to have multiple hard drives appear as one and allow you to add new ones to expand when desired.

---

### Post by koenn on 2008-01-08
The easiest way is to mount the drives each to its own (sub)directory, which would give something like this (using home directory as example, but it could be any directory)

eg:
/home  --> your current home 
/home/music  -> extra drive 1
/home/misc  ->  extra drive 2
/home/pics  ->   extra drive 3
and so on

there's a recipe like that here : [http://users.telenet.be/mydotcom/howto/linux/disks1.htm](http://users.telenet.be/mydotcom/howto/linux/disks1.htm)

other than that, you can use LVM to span multiple disks, or something with raid.

---

