---
title: "sfill crash"
date: 2013-01-16
forum: Security
---

### Post by scenkner on 2013-01-16
Please forgive me if this is not the correct forum for this question. It is the most appropriate forum I could find.  So, I try to wipe free space on a drive using sfill, part of the secure-delete package.  I use a command like this:
```
sudo sfill -v /media/a_user/some_disk
```
Everything seems to go well for a few hours.  Every so often it outputs an asterisk I assume indicating a completed pass.  The problem occured @ Wiping inodes.  Here is the output:
```
Using /dev/urandom for random input.
Wipe mode is secure (38 special passes)
Wiping now ...
Creating /media/a_user/some_disk/oooooooo.ooo ... ************************************** Wiping inodes ...sfill: malloc.c:2451: sYSMALLOc: Assertion `(old_top == (((mbinptr) (((char *) &((av)->bins[((1) - 1) * 2])) - __builtin_offsetof (struct malloc_chunk, fd)))) && old_size == 0) || ((unsigned long) (old_size) >= (unsigned long)((((__builtin_offsetof (struct malloc_chunk, fd_nextsize))+((2 * (sizeof(size_t))) - 1)) & ~((2 * (sizeof(size_t))) - 1))) && ((old_top)->size & 0x1) && ((unsigned long)old_end & pagemask) == 0)' failed.
```
Any ideas what would cause this crash?  This left hundreds of files on the disk with randomly generated names like ahlvbhsjfl.vhd.  Thanks for any help you can offer! 
Oh BTW, Ubuntu 12.10 x64 3.5.0-22-generic

---

