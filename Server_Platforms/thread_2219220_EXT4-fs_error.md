---
title: "EXT4-fs error"
date: 2014-04-23
forum: Server Platforms
---

### Post by larzeb on 2014-04-23
/var/log/syslog contains the following error:

> [59261.914182] EXT4-fs error (device md0): ext4_iget:3737: inode #301662691: comm py     thon3: bad extra_isize (62208 != 256)

EXT4-fs (sdf1): re-mounted. Opts: errors=remount-ro
EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: errors=remount-ro



This is not the first time I've experienced problems with these RAID disks. I just rebuilt this array two weeks ago. Obviously I need to replace hardware. 

Why didn't mdadm degrade the array? Why was my only warning my inability to save data to the array?

Any suggestions on how I might recover? I do have a backup of the data.

---

### Post by CharlesA on 2014-04-24
Have you already run fsck on the array? That would be a good place to start.

It's likely the file system inconsistency isn't enough to cause problems, but a fsck should fix it right up.

---

