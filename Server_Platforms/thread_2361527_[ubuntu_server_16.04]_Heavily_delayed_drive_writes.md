---
title: "[ubuntu server 16.04] Heavily delayed drive writes/caching to reduce SSD writes"
date: 2017-05-17
forum: Server Platforms
---

### Post by jrmymllr on 2017-05-17
I'm running Server 16.04 on a computer with a small SSD (32GB) that contains the OS and all other application software.  The primary purpose of this machine is a security camera recorder, and the recorded video is written to a separate drive, also an SSD but much larger than 32GB.

The security camera program seems to write a lot of temporary files to both drives according to fatrace.  These files exist for maybe a few minutes, then are deleted and written again as a different filename to the larger SSD.  

What I'd like to do is heavily cache and delay writes so these temporary files are never actually written to either drive.  I set these values in sysctl.conf:

vm.dirty_ratio = 50
vm.dirty_background_ratio = 40
vm.dirty_writeback_centisecs = 500
vm.dirty_expire_centisecs = 180000

and set commit=600 in fstab for the OS drive, which is EXT4.  I'm still seeing 250-500MB/day written to the OS drive according to smartctl and [COLOR=#242729][FONT=Arial]/sys/fs/ext4/$DEVICE/lifetime_write_kbytes

The system has 8GB RAM, no swap, and services running on it are using under 1GB, so there's plenty of free RAM.

[/FONT][/COLOR]Is there anything else I'm missing?  Should the configuration options I mentioned allow files that are written then deleted a minute or two later never hit the drive?  I haven't found anything else in my research, but thought maybe someone has some experience with this.

---

### Post by howefield on 2017-05-17
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

