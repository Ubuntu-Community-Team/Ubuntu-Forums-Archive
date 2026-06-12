---
title: "Crossplatform File systems"
date: 2012-01-30
forum: Server Platforms
---

### Post by maverick918 on 2012-01-30
Hello,

I have a department at my work that uses all Mac OS X machines. I've been tasked with migrating all they're existing data from an HFS+ file system to a new server. 

I know about the data fork and resource fork and have the file transfer down to preserve them but I need to know what file system Ubuntu 11.10 should use to preserve the names of the files and folders (alot of weird naming conventions)

Ext4 did not work dude to the limitations of naming conventions.
Ext3 will not work either.

HFS+ is a no go because the Volumes have to be bigger than 2 TB. 

I'm at a loss. I had it setup with ZFS but then I read that ZFS is just a glorified LVM manager with software RAID. 

Please help me settle on a file system that will hold these files and not mess with the naming conventions. Has anyone done this? Let me know if you need more info.

---

### Post by sandyd on 2012-01-30
> **maverick918 said:**
> Hello,

I have a department at my work that uses all Mac OS X machines. I've been tasked with migrating all they're existing data from an HFS+ file system to a new server. 

I know about the data fork and resource fork and have the file transfer down to preserve them but I need to know what file system Ubuntu 11.10 should use to preserve the names of the files and folders (alot of weird naming conventions)

Ext4 did not work dude to the limitations of naming conventions.
Ext3 will not work either.

HFS+ is a no go because the Volumes have to be bigger than 2 TB. 

I'm at a loss. I had it setup with ZFS but then I read that ZFS is just a glorified LVM manager with software RAID. 

Please help me settle on a file system that will hold these files and not mess with the naming conventions. Has anyone done this? Let me know if you need more info.
XFS. Its a little non-accepting of hardware problems though.
You could try JFS as well.

---

### Post by rubylaser on 2012-01-30
We have 2 fileservers for our Macs here at work and they're both Solaris 11 boxes using ZFS + napp-it web interface.  They both have worked very well.  Personally, I've had nothing but problems with XFS (corruption, etc).  We went with ZFS because we needed volumes larger than 16TB and that ruled out EXT3/4 right away and because of past XFS problems we avoid that like the plague.

ZFS is a very slick filesystem and I'm not sure how being an LVM + software RAID as you described it is a drawback.  It's easy to migrate (not controller dependent) and supports copy-on-write (atomic writes, no RAID5 write hole).

---

