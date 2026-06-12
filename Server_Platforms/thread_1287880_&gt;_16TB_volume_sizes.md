---
title: "&gt; 16TB volume sizes"
date: 2009-10-10
forum: Server Platforms
---

### Post by wesg on 2009-10-10
I'm thinking of the future, so for the last few days I've been reading about large RAID setups that people have built. Sometime after I graduate university and have some money, I too want to build a 20 disk storage solution with one of those Norco cases. 

My question is about file systems and volume sizes. Say I eventually put 20 x 2 TB in the case as a RAID 6 array. Theoretically that gives me 20x2TB - 2x2TB = 36TB. Since ext3 doesn't work with volumes over 16 TB, I need a new file system. What options are available? Can I insert new drives into the array using only RAID 5?

---

### Post by Vegan on 2009-10-10
ext4 can cope, but some parts of Ubuntu are still behind on the curve.

I tried to mount an ext4 disk, no joy.

Maybe next version whenever it surfaces.

---

### Post by insane_alien on 2009-10-11
ext4 works fine on ubuntu.

XFS is another option, it can support up to 16EB

---

### Post by cariboo on 2009-10-11
+1 for XFS, I use it on my server, transfer speeds are just a little slower than ext4, but it is a great file system for **large** files.

---

### Post by Bachstelze on 2009-10-11
ZFS ftw.

---

### Post by wesg on 2009-10-11
> **Bachstelze said:**
> ZFS ftw.

How did you get ZFS onto Ubuntu?

---

### Post by Vegan on 2009-10-12
Not sure if Ubuntu has it, but the LUSTRE file system should scale to as big as you want over several servers.

---

### Post by BQAggie2006 on 2009-10-12
I've kind of been researching the same thing over the past few weeks and narrowed my options down to either ext4 or JFS.

---

### Post by dragos2 on 2009-10-12
JFS, XFS, ext4, ZFS (bsd's and solaris because of the license), btrfs, and cluster software like
GFS.

---

### Post by collinp on 2009-10-12
Another option, although fairly ineffective and inefficient, would be to split the > 16TB volume into several EXT3 filesystems.

---

### Post by khughitt on 2009-10-12
```
I've kind of been researching the same thing over the past few weeks and narrowed my options down to either ext4 or JFS.
```

I would stick to ext4. I ran JFS for about six months on a desktop machine and would run into very strange errors that were very likely to be caused by issues with JFS. Since then I've switched to ext4 and it's been working wonderfully.

---

### Post by hubie on 2009-10-13
> **pwnedd said:**
> 
I would stick to ext4. I ran JFS for about six months on a desktop machine and would run into very strange errors that were very likely to be caused by issues with JFS. Since then I've switched to ext4 and it's been working wonderfully.

Unfortunately ext4 doesn't yet do >16TB, at least according to this [Ext4 Howto article]("http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Creating_ext4_filesystems").

Anyone out there use beta or other versions of e2fsprogs or whatever to get support for >16TB volumes on ext4 (if so, how well does it work)?

---

