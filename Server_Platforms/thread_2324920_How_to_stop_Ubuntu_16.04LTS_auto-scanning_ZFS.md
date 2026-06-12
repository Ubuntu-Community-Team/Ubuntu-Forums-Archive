---
title: "How to stop Ubuntu 16.04LTS auto-scanning ZFS ?"
date: 2016-05-17
forum: Server Platforms
---

### Post by bob_jones2 on 2016-05-17
```
 $ cat /etc/lsb-release
    DISTRIB_ID=Ubuntu
    DISTRIB_RELEASE=16.04
    DISTRIB_CODENAME=xenial
    DISTRIB_DESCRIPTION="Ubuntu 16.04 LTS"
    $ uname -a
    Linux foobar 4.4.0-22-generic #39-Ubuntu SMP Thu May 5 16:53:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
    $ sudo dpkg -s zfsutils-linux
    Package: zfsutils-linux
    Status: install ok installed
    Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
    Architecture: amd64
    Source: zfs-linux
    Version: 0.6.5.6-0ubuntu8
```

    I have a zpool created as follows (just showing process one disk here to keep the story short !!) :

    ```
 gdisk /dev/sdg (then o and w - new empty GPT and write)
    zpool create foobar /dev/sde /dev/sdf /dev/sdg
    
```
    Anway, Ubuntu worked its magic and that all works great and I've got a working /foobar mountpoint. I have rebooted the system a few times subsequently and everything continues working great.

    Ubuntu sets up the partitions itself, so its automated end-result looks like:

    ```
 gdisk -l /dev/sdg
    Number Start (sector) End (sector) Size Code Name
    1 2048 32487423 15.5 GiB BF01 zfs
    9 32487424 32503807 8.0 MiB BF07
    
```
    Except one thing !

    Ubuntu still goes hunting around /dev/sdg for filesystems despite it knowing about zfs and the zfs mount being perfectly functional ! This is what my dmesg looks like :
    ```

    [39183.326519] EXT4-fs (sdg9): VFS: Can't find ext4 filesystem
    [39183.328795] EXT4-fs (sdg9): VFS: Can't find ext4 filesystem
    [39183.331125] EXT4-fs (sdg9): VFS: Can't find ext4 filesystem
    [39183.333482] FAT-fs (sdg9): bogus number of reserved sectors
    [39183.334162] FAT-fs (sdg9): Can't find a valid FAT filesystem
    [39183.340737] XFS (sdg9): Invalid superblock magic number
    [39183.344135] FAT-fs (sdg9): bogus number of reserved sectors
    [39183.344803] FAT-fs (sdg9): Can't find a valid FAT filesystem
    [39183.349688] VFS: Can't find a Minix filesystem V1 | V2 | V3 on device sdg9.
    [39183.351369] hfsplus: unable to find HFS+ superblock
    [39183.352916] qnx4: no qnx4 filesystem (no root dir).
    [39183.355158] ufs: You didn't specify the type of your ufs filesystem

    mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextste p|nextstep-cd|openstep ...

    >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
    [39183.359668] ufs: ufs_fill_super(): bad magic number
    [39183.362430] hfs: can't find a HFS filesystem on dev sdg9
```


    What is the "official" correct way to stop Ubuntu doing this ?.

---

### Post by repvik2 on 2016-05-19
> **bob_jones2 said:**
> .
I feel like referencing this particular XKCD: [https://xkcd.com/979/](https://xkcd.com/979/)

I'm seeing the same messages in my dmesg. What was your solution?

---

### Post by bob_jones2 on 2016-05-30
repvik2,

Nobody ever bothered to reply to my original post, so I don't know.  I've just filtered it out on my centralised logging and moved on with my life. :D

---

### Post by lisati on 2016-06-01
> **bob_jones2 said:**
> repvik2,

Nobody ever bothered to reply to my original post, so I don't know.  I've just filtered it out on my centralised logging and moved on with my life. :D

You might have noticed that the post you "deleted" has been restored. Rather than editing a post to make it go away, please use the "Report Post" button in future to ask the forum staff to take a look and, if needed, move the post out of public view.

---

