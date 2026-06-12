---
title: "Run tune2fs to modify FS, after a year from the disk's creation"
date: 2017-04-04
forum: Server Platforms
---

### Post by nihvel on 2017-04-04
Hello all,
last year I setup a few _Ubuntu 14_ server and on some of them I applied the _ext4 FileSystem_, this is how I mounted the disk on fstab:
```
/dev/sdb1 /data ext4 noatime,nodiratime,data=writeback,barrier=0,nobh,errors=continue 0 1
```

_**I totally forgot to run tune2fs.**_
After a year, I realized I haven't when during a scheduled maintenance, I saw from the ESXi console that the server wasn't booting because as "error" about the disk and its mount point /data.

The choice was between I-ignore, M-manually recover and S-skip check.

To have the system booted, I "Ignored" the error and could ssh on this server to check its drive's filesystem:

```
root@serverwithdamageddisk:/var/log# tune2fs -l /dev/sdb1
tune2fs 1.42.9 (4-Feb-2014)
Filesystem volume name:   <none>
Last mounted on:          /data
Filesystem UUID:          9a3d8917-99ff-4dc8-82be-e2999b33a502
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      **has_journal** ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file dir_nlink extra_isize metadata_csum
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              6553600
Block count:              26214144
Reserved block count:     1310707
Free blocks:              25075500
Free inodes:              6543833
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1017
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Mon Sep 12 18:06:00 2016
Last mount time:          Mon Apr  3 17:43:00 2017
Last write time:          Mon Apr  3 17:43:00 2017
Mount count:              4
Maximum mount count:      -1
Last checked:             Mon Sep 12 18:06:00 2016
Check interval:           0 (<none>)
Lifetime writes:          17 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     32
Desired extra isize:      32
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      6f903de6-c9b1-461e-82cb-b61797403cd8
Journal backup:           inode blocks
Checksum:                 0x126c00a7
```

As you can see, in the **Filesystem features:** appears "only" **has_journal **and _**journal_data_writeback **_is not set.

_**My question is:**_
Can I run the following code "on the fly" and hope the disk won't get corrupted/damaged/exploded/ or worst that the file inside would *disappear* ?
```
tune2fs -o journal_data_writeback /dev/sdb1
e2fsck -f /dev/sdb1

```

I did a search on the forum and read almost all of the 8 pages with keyword "tune2fs", unfortunately people were not so dumb as I was when I set up the system, therefore I haven't seen my question or similar in the search result.

Please help me (:

---

### Post by howefield on 2017-04-04
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by nihvel on 2017-04-04
**UPDATE:**

I am trying to reproduce the error by creating a virtual machine with ubuntu 14, /dev/sdb/ added when the system was built already but improperly configured both on fstab and disk FS. Exactly like in the production environment.

I am running, since this morning, various scripts I created to create many random file of 10MB each for the whole disk size (10GB), then SHRED them and this on a loop, which is running now for hours.
See screenshot.

I am trying to "destroy" the virtual disk and replicate the error.
[http://imgur.com/a/OqnL8](http://imgur.com/a/OqnL8)
[IMG]http://imgur.com/a/OqnL8[/IMG]

---

### Post by ajgreeny on 2017-04-04
I am not certain exactly what you are trying to achieve, but you speak as though it is a requirement to run tune2fs always after installation of an OS or after setting up/creating a filesystem on a partition, which I do not think is the case. Tell us more about your reasons for wanting to run tune2fs, and if this relates to the chosen mount options for the partition, can you perhaps change those more easily using fstab.

You can use tune2fs on a partition that is mounted for many, if not all activities; I'm not sure if it must be unmounted for anything, but if so, I'm unaware of it and have never needed those actions.

However, you can not use e2fsck on a mounted partition, or if you did, it is very dangerous, so if by "on the fly" you mean when the partition is mounted and/or in use, your command **e2fsck -f /dev/sdb1** is most likely a non-starter.

---

### Post by nihvel on 2017-04-04
Hi thanks for reply!

One of the server in production, when my maintenance finischd and it was time to start it, during its boot it shown an error about the mount point /data (my bad I did not take a screenshot). 
This disk, sdb, is mounted with that line in fstab and what I read (and knew already) was that using this fstab's string when the disk was not "tuned", may lead to errors on the disk.

I believe I reached this point, where my disk is corrupted. Else, during the boot it should not have shown me the disk error.

My question is, if i can run the ```
tune2fs -o journal_data_writeback /dev/sdb1
```  now, obviously after have the disk unmounted. 

The complete steps would be:

```
umount /dev/sdb1
tune2fs -m 0 /dev/sdb1
tune2fs -o journal_data_writeback /dev/sdb1
e2fsck -f /dev/sdb1
mount -a

```


In that virtual machine I created, I tested these passages as if I were doing them on the real server. The result was ok, meant that it worked and no errors appeared.


Else, the road to edit fstab and remount the drive with  ```
/dev/sdb1 /data ext4 defaults 0 1
``` would work ok for me, I don't really need journaling.

My worry is that the server is in production and I wish to fix it with the safest method available.

I am not familiar with tune2fs itself, I do not know if this command needs to be ran just after the server/disk is created or I can use it whenever I want

---

### Post by ajgreeny on 2017-04-04
That is one of the uses of tune2fs that I have never used so am not sure about, but reading man tune2fs in terminal does not indicate any likely problems running the command.

---

### Post by nihvel on 2017-04-04
I read the manual too, wanted to know more about this tool and I do not read anywhere it needs to be ran after the disk creation or that there are issued in running it or anything..
Actually, I am quite comfortable in doing another maintenance for this reason, but you know... better safe than sorry.

I think I will create a new virtual disk, rsync all, proceed with tune2fs and hope. 
We'll see.. for now I thank you for your support! hope to be back with good news.

---

