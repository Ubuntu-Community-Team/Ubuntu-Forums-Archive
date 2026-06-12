---
title: "Superblock set into the future"
date: 2016-08-01
forum: Ubuntu Development Version
---

### Post by VMC on 2016-08-01
After installing xubuntu, I get a message: "Superblock set into the future"

I don't want UTC time, but LOCAL TIME instead. In the past issuing "timedatectl set-local-rtc 1" fix it. Not any more. It still works in Xenial.

timedatectl set-local-rtc 1 is for LOCAL TIME
timedatectl set-local-rtc 0 is for UTC time

Here's some info for my system:
 ```
$ date && sudo hwclock --debug && sudo dumpe2fs /dev/sda7 | head -50
Sun Jul 31 21:31:05 PDT 2016
[sudo] password for vmc: 
hwclock from util-linux 2.28
Using the /dev interface to the clock.
Last drift adjustment done at 0 seconds after 1969
Last calibration done at 0 seconds after 1969
Hardware clock is on local time
Assuming hardware clock is kept in local time.
Waiting for clock tick...
...got clock tick
Time read from Hardware Clock: 2016/07/31 21:31:07
Hw clock time : 2016/07/31 21:31:07 = 1470025867 seconds since 1969
Time since last adjustment is 1470025867 seconds
Calculated Hardware Clock drift is 0.000000 seconds
2016-07-31 21:31:06.842675-8:00
dumpe2fs 1.43.1 (08-Jun-2016)
Filesystem volume name:   <none>
Last mounted on:          /
Filesystem UUID:          d873f8c6-2230-44e6-b865-a0b1c1ef4259
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent 64bit flex_bg sparse_super large_file huge_file dir_nlink extra_isize metadata_csum
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              4521984
Block count:              18067138
Reserved block count:     903356
Free blocks:              16903579
Free inodes:              4365297
First block:              0
Block size:               4096
Fragment size:            4096
Group descriptor size:    64
Reserved GDT blocks:      1024
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sun Jul 31 21:10:29 2016
Last mount time:          Sun Jul 31 21:30:24 2016
Last write time:          Sun Jul 31 14:30:21 2016
Mount count:              4
Maximum mount count:      -1
Last checked:             Sun Jul 31 21:10:31 2016
Check interval:           0 (<none>)
Lifetime writes:          5471 MB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     32
Desired extra isize:      32
Journal inode:            8
First orphan inode:       2883686
Default directory hash:   half_md4
Directory Hash Seed:      d2a27026-ca68-4971-aa6d-964039f8b68b
Journal backup:           inode blocks
Checksum type:            crc32c
Checksum:                 0x3597c54e
Journal features:         journal_incompat_revoke journal_64bit journal_checksum_v3
Journal size:             128M
Journal length:           32768

```

Notice the time difference of Filesystem created:Sun Jul 31 21:10:29 2016, Last mount time:Sun Jul 31 21:30:24 2016 and Last write time: Sun Jul 31 14:30:21 2016
The last write is in the past.

I will re-check tomorrow to see if the error continues.

---

### Post by VMC on 2016-08-02
I decided to change Windows 10 registry to use UTC instead:
```
reg add "HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TimeZoneInformation" /v RealTimeIsUniversal /d 1 /t REG_DWORD /f
```

That makes life much simpler. I've been fighting this for a long time.

Another point is e2fsprogs has been updated for Yakkety. My Xenial can no longer *fsck* on Yakkety's EXT4 filesystem.

edit: I installed *e2fsprogs* 1.43 on Xenial. Now I can successfully test Yakkety installs.

---

