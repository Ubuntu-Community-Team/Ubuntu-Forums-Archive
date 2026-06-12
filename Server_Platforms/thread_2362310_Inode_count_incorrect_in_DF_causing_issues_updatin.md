---
title: "Inode count incorrect in DF causing issues updating"
date: 2017-05-26
forum: Server Platforms
---

### Post by johnathan3 on 2017-05-26
Inode count incorrect in DF causing issues updating

```
#uname -a
Linux MediaVault 4.4.0-77-generic #98-Ubuntu SMP Wed Apr 26 08:34:02 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```
```
# df -ia
Filesystem      Inodes   IUsed  IFree     IUse%     Mounted on
sysfs                0          0      0          -              /sys
proc                 0       0      0     -                     /proc
udev            452078     561 451517       1%            /dev
devpts               0       0      0     -                   /dev/pts
tmpfs           457078     788 456290       1%            /run
/dev/sda1      1048576 1048110    466     100%          /
tmpfs           457078       2 457076        1%              /dev/shm
tmpfs           457078      16 457062        1%             /sys/fs/cgroup
cgroup               0       0      0     -                    /sys/fs/cgroup/systemd
tmpfs           457078       4 457074         1%            /run/user/0

```
```
# tune2fs -l /dev/sda1
tune2fs 1.42.13 (17-May-2015)
Filesystem volume name:   <none>
Last mounted on:          /
Filesystem UUID:          abe26068-8778-48e7-a706-d24b95a9088f
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              1048576
Block count:              4194048
Reserved block count:     209702
Free blocks:              2562200
Free inodes:              533
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1023
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Mon May  1 00:04:17 2017
Last mount time:          Fri May 26 12:58:36 2017
Last write time:          Fri May 26 12:58:35 2017
Mount count:              27
Maximum mount count:      -1
Last checked:             Mon May  1 00:04:17 2017
Check interval:           0 (<none>)
Lifetime writes:          17 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
First orphan inode:       524750
Default directory hash:   half_md4
Directory Hash Seed:      1a4933a6-3532-4f98-83d3-11ccae61843d
Journal backup:           inode blocks

```
```
#for ii in $(find -maxdepth 1 -type d); do echo -e "${ii}\t$(find "${ii}" -type l -o -type d -o -type f | wc -l)"; done | sort -n -k 2 | column -t
./lost+found  1
./snap        1
./srv         1
./lib64       2
./NAS         2
./media       4
./mnt         4
./tmp         7
./scripts     20
./home        53
./opt         158
./bin         173
./sbin        232
./boot        298
./dev         326
./root        444
./run         767
./etc         4572
./var         10415
./lib         13562
./sys         24854
./proc        50970
./usr         113858
.             220730

```


```
#for i in *; do echo -e "$(find $i | wc -l)\t$i"; done | sort -n
1       initrd.img
1       initrd.img.old
1       lost+found
1       snap
1       srv
1       vmlinuz
1       vmlinuz.old
1       webmin-setup.out
2       lib64
2       NAS
4       media
4       mnt
7       tmp
20      scripts
53      home
158     opt
173     bin
232     sbin
298     boot
444     root
564     dev
791     run
4572    etc
10515   var
13562   lib
24854   sys
51331   proc
113858  usr
```



NCDU also reports Items 219566
Where are these inodes being used?

---

### Post by TheFu on 2017-05-26
You ran out of inodes.  
```
Free inodes:              533
```
Modifying the number can only happen at file system creation.
You can add more storage and mount it somewhere useful, if you like.

I've had to do this when my / ran out of i-nodes, just like yours.
```
$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/vda1        7389384 3990480   3023608  57% /
/dev/vda2        2325684 1099088   1108384  50% /var/www

$ df -i
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
/dev/vda1      464000 345322 118678   75% /
/dev/vda2      154128  58873  95255   39% /var/www

```
I removed the pseudo-file systems, since they don't count.
/var/www/ has a bunch (thousands?) of tiny files for a few different webapps.  

i-nodes are used for any temporary needs too, so the 533 available can be sucked up quickly.

---

### Post by johnathan3 on 2017-05-26
I get that.
But according to NCDU and the number of files I have. there should only be about 220,000 inodes used out of over 1,000,000

How do i find were that extra 800k is being used?

---

### Post by TheFu on 2017-05-26
Never heard of ncdu before.  The manpage for it says it doesn't deal with hardlinks consistently. Could that be the issue?

---

