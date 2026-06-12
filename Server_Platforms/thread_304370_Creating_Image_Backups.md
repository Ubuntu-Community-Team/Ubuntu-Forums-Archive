---
title: "Creating Image Backups"
date: 2006-11-21
forum: Server Platforms
---

### Post by DannyG on 2006-11-21
Hi,

I currenlty run Ubuntu Dapper 6.06.1 on my Laptop, and I rent a VPS with Ubuntu Dapper 6.06 Server Installation.

I was wondering if its at all possible to create an exact image of my VPS onto my Laptop for backup purposes? I have plenty of space on my Laptop and download speeds and bandwidth are not a problem.

So does anyone know how to go about doing this? Is it just of using the "Connect to Server..." feature in "Places" and copying and pasting the entire thing accross?

Thanks,
Daniel.

---

### Post by marianom on 2006-11-21
Can PartImage help on this? [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by DannyG on 2006-11-22
Does that application make an image of the entire partition, or just data on the partition? For example, if I have a 10GB Partition, but theres only 3GB of data, will make an image 10GB in size, or 3GB in size?

Thanks,
Daniel.

---

### Post by MJN on 2006-11-22
Just the data...
 
Note however that come restore time you'd need to put it back into a 10GB partition even though you (and it) know there's only 3GB of data. This is likely not an issue most of the time, but it could be if you were restoring with different partition sizing (even if theoretically the partitions are still big enough).
 
Mathew

---

### Post by breezyfox on 2006-11-22
HI
You can also try the following:
There is a utility and it just like GHOST.
It is called image for linux (IFL) and is available from
[http://www.terabyteinc.com/imagel.html](http://www.terabyteinc.com/imagel.html).

 It works perfectly and copies data and recognises all fat,fat32 and ntfs and ext file systems.

bz

---

