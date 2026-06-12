---
title: "xfs_fsr - could not open: inode"
date: 2008-10-08
forum: Server Platforms
---

### Post by adechiaro on 2008-10-08
Hey all,

I have a server with a software RAID 5 array formatted with XFS.  Awhile ago I used xfs_fsr to degragment the array (rather large ~1 TB) which worked great.  Recently I started it up again, and it ran for a little bit then promptly exited.  Since xfs_db / frag still reported ~15% fragmentation I tried restarting it again but it just stopped right away.  Running with -d option reported a large amount of these messages:

could not open: inode 3087052599
could not open: inode 3221226241
could not open: inode 3221226240
could not open: inode 3221226295
could not open: inode 3221226260
could not open: inode 3221226275
could not open: inode 3221226290
could not open: inode 3221226293
could not open: inode 3221226294
...etc

Thinking it may be due to the filesystem in use, I tried remounting read-only and unmounting it totally but neither worked as I realized it had to be mounted rw to actually modify the filesystem.

A quick Google search revealed nothing regarding these messages, any ideas?  Thanks!

---

