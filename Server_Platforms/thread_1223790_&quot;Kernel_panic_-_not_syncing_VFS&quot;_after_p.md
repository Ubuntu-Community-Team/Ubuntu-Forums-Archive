---
title: "&quot;Kernel panic - not syncing: VFS&quot; after pulling power cord"
date: 2009-07-26
forum: Server Platforms
---

### Post by chu_ben on 2009-07-26
I accidentally tripped on the power cord for my machine and now am unable to boot.  After selecting the image from the GRUB boot menu, I get the following message:

```
Starting up ...
[    6.120777] EXT3-fs: unable to read superblock
[    6.120856] EXT4-fs: unable to read superblock
[    6.121007] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(9,2)
```

Is there a way I can repair this problem?  I have RAID'd some of the partitions.  /boot with RAID1, swap with RAID1, and / with RAID5.  I am guessing the problem is a boot or GRUB problem but I am not sure since I am still learning.

Thanks in advance for any help!

---

### Post by cariboo on 2009-07-26
Boot from a live cd and run fsck on your / partition.

---

