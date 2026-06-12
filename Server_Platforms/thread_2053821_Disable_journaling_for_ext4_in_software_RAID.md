---
title: "Disable journaling for ext4 in software RAID"
date: 2012-09-06
forum: Server Platforms
---

### Post by al_mic on 2012-09-06
Hello,

I have two disks with three partitions each in a software raid array. (raid 1)
The filesystem on each partition is ext4, but I want to disable the journaling.

After reading a bit on the net, I found that one way to do it is to use this command:
# tune2fs -O ^has_journal /dev/mdX

or maybe, like this:
# tune2fs -O ^has_journal /dev/sdaX
# tune2fs -O ^has_journal /dev/sabX

I have not tried it. Instead I've tried adding a mount option in the fstab: noload
This option supposed to disable the journaling for an ext4 fs.

I'm not sure if it worked because:
- after rebooting the system I get these messages from dmesg:
EXT4-fs (md0): mounted filesystem without journal
EXT4-fs (md1): mounted filesystem without journal
which sound good, but I also get this one:
EXT4-fs (md3): mounted filesystem with ordered data mode

- also, checking the devices with tune2fs shows this for each of them:
# tune2fs -l /dev/md0|grep features
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super huge_file uninit_bg dir_nlink extra_isize

The presence of has_journal flag should mean that journaling is still on? Even if dmesg said different?
And second, do you know why dmesg shows something else for md3?
Could that be cause by the size of the partition? md3 is a bit larger than the other two.

Thank you.

---

