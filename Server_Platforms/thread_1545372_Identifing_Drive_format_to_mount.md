---
title: "Identifing Drive format to mount"
date: 2010-08-03
forum: Server Platforms
---

### Post by ptmuldoon on 2010-08-03
Still a newbie, so please be gentle :)

I've installed Ubuntu Server, and Webmin following this [guide](http://www.smallnetbuilder.com/nas/nas-howto/30573-build-your-own-atom-based-nas-part-2), and all is well so far...

I've mounted some drives with some pre-existing data on them, and can view the data on those drives.

But I have one drive that I can't seem to mount, and I'm pretty sure there's data on it.   But I can't seem to find how to identify what format the data is in, ie.. ntfs, ext2, ext 3, etc.

Its likely pretty simple, but how can you identify the drive format before you attempt to mount it?

Thanks
PT

---

### Post by Vegan on 2010-08-03
generally disks are 

/dev/sda
/dev/sdb 


etc

so when you mount, you can use the auto detect

---

### Post by ptmuldoon on 2010-08-03
I think thats part of my problem.  Trying to mount the drive tells me "you must specify the file system"

I mounted all the others, knowing they were in ext2 format.  Its just this last drive I'm having issues with.

---

