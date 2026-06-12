---
title: "installation: partman can't mount raid6 on /"
date: 2020-04-16
forum: Server Platforms
---

### Post by honeycombs_big_yahyahyah on 2020-04-16
Hi all,

I've been pursuing this question on another [thread]("https://ubuntuforums.org/showthread.php?t=2440352"), and while I've gotten through a few issues there, I think the principal issue has now become buried.  I'm hoping a fresh thread can help resolve it.

I'm trying to install Server v18 on two existing md raid arrays via the alternative installer, as I have data on one of the arrays (14.04 previously installed, but dead due to raid crash).  Partman seems able to mount the raid1 to format and use as /boot.  It [errors out]("https://i.imgur.com/R4t8mw6.png"), however, when trying to mount my larger raid6 at /, without formatting (i.e. keeping the data on the drives).

The two md arrays are formatted as ext4, and the raid1 is detected as such by partman.  The raid6, however, is detected as ext2.  I don't know if this is the root of the problem.  I am able to escape out into shell and mount the array, see the files, etc.  /proc/mdstat does not indicate any problems, and e2fsck shows the partition as clean.  The live installer detects the raid6 as ext4, but I don't think I can use it to install without killing the data on the raid (though I'd be happy to be wrong about that).

Any suggestions as to how to solve this would be much appreciated.

Many thanks,
Allie

---

