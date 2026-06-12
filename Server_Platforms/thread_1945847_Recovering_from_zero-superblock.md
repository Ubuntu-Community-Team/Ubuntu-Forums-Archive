---
title: "Recovering from zero-superblock"
date: 2012-03-23
forum: Server Platforms
---

### Post by phyrexia on 2012-03-23
Hello everyone. 

I have made a particularly boneheaded mistake. 

I had a raid 1 array using two 2tb discs, which was built with mdadm.  Inadvertently, I have erased the raid array and performed a zero-superblock on the two drives.

This was not my intended goal...(I am about to turn this machine into a hackintosh and wanted to separate the array into two discrete discs before switching OSes)

I can run dumpe2fs with the following output.

```
root@crushinator:/# dumpe2fs /dev/sdb1 
dumpe2fs 1.41.14 (22-Dec-2010)
Filesystem volume name:   6YD0GEM6
Last mounted on:          <not available>
Filesystem UUID:          c501f304-cc90-4faf-8242-545ef9f25c82
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              122101760
Block count:              488378637
Reserved block count:     24418931
Free blocks:              480665218
Free inodes:              122101749
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      907
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Thu Jan  5 18:04:14 2012
Last mount time:          Thu Jan  5 18:05:06 2012
Last write time:          Thu Jan  5 18:16:38 2012
Mount count:              2
Maximum mount count:      34
Last checked:             Thu Jan  5 18:04:14 2012
Check interval:           15552000 (6 months)
Next check after:         Tue Jul  3 19:04:14 2012
Lifetime writes:          1940 MB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      f6dadfdf-b063-4ac5-92f1-2bc3db3a1baf
Journal backup:           inode blocks
dumpe2fs: A block group is missing an inode table while reading journal inode

```

So it appears data is still there.  

Is there a method that would allow me to recover these partitions?  I do not have a full understanding of mdadm (or, frankly, the way linux filesystems work) and this obviously has caused problems. ;)

Thanks

---

### Post by rubylaser on 2012-03-24
The easiest way to do this is to recreate the array.  Since those disks where in RAID1, even after zeroing the superblocks, you should still be able to mount and read the individual disks though.  Have you tried doing that? **<--- This should be your first step.**

Why in the world did you zero the superblocks on both disks though? :)  Something like this.
```
mdadm --create /dev/md0 --assume-clean --level=1 --verbose --raid-devices=2 /dev/sda1 /dev/sdb1
```

---

