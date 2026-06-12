---
title: "Problem with Extended Attributes limix in Linux+XFS when backing up HFS+"
date: 2014-01-31
forum: Server Platforms
---

### Post by Sun_Blood on 2014-01-31
If I understands it correctly XFS don't have a limit to the  size of extended attributes(EA) but Linux kernel impose a limit at 64k? What I am trying to do is build a backup server that our Apple computers  will use together with rsync to backup files to. The problem that I  face is that Apple HFS+ don't have a limit to EA so it has files with  more then 64k of EA in it.

  The Linux Kernel has a limit imposed to it in include/linux/limits.h
  ```
#define XATTR_SIZE_MAX 65536    /* size of an extended attribute value (64k) */ 
#define XATTR_LIST_MAX 65536    /* size of extended attribute namelist (64k) */
  
```
Changing this values feels unsafe because they will be system wide and I use ext4 also in this server.
  Is the any possibility to combine Linux + XFS to make a backup that works with EA?
  Thanks.

---

