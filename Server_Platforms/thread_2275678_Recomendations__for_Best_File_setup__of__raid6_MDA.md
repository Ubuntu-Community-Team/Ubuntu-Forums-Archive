---
title: "Recomendations  for Best File setup  of  raid6 MDADM over 20TB"
date: 2015-04-27
forum: Server Platforms
---

### Post by oehq on 2015-04-27
I am needing to replace a 12TB raid6 with a 20TB using MDADM.
I understand that I should not use ext4 file systems due to its limit of 16TB.
I am looking for a setup that will allow expansion in the future without having to re-create the raid.

Any suggestions for building raids larger than 16TB are very welcome? 

Thanks for a great forum

---

### Post by darkod on 2015-04-28
Is it necessary to be mdadm? If you want to, you can consider using ZFS on ubuntu. Using raidz2 is equivalent to raid6, plus it has some improvements I believe. Of course, the OS will not be on the raidz2, you will need separate small raid for the OS only.
Expansion is very easy with zfs and virtually limitless (if I'm not mistaken the name zfs comes from Zetta Byte, so start counting the zeroes.... :) )

In this kind of setup the raidz2 will only be the foundation for the data storage. The OS is still standard ubuntu and you can do any config the same...

---

### Post by MAFoElffen on 2015-04-29
The 16TB limitation is not on the container. (Misunderstood by Darko.) So the limitation on an mdadm RAID6 is 256 members in the Array... I like using ZFS (I also support and test Solaris)... but that would be another filessytem within another RAIDZ container... The maximum volume size for a ZFS volume is 2 to the power of 64 for a total of 18 exabits.

So the size limtations come into play when we start talking about the addresability of the filesystem within those containers.

The information was misunderstood (old information) by the OP... The old limit of ext4 and the present limit of 32bit ext4 is 16TB. The newer limit of 64bit ext4 is 50TB.

Here is from the RHEL docs for rhel7 and differing filesystems... (just for fyi):
Filesystem        RHEL 7
------------       --------
EXT2/3            16TB
EXT4                  50TB [1EB]
GFS                 n/a
GFS2               100TB [8EB]
XFS                 500TB [16EB]

So, there is some config excentricities when you create an ext4 filesystem for big data... but, you are going to run into those also with GFS2 and XFS. If planning to grow in the future (again), maybe a better choice may be GFS2 or XFS filesystems. Grub2 and Linux mount now handle both well.O nly caution I've heard on those is that with XFS, it handles inodes a bit differently, and some older applications have difficulties with that.

In extX filesystems, the inode limit is created when the filesystem is created. Btrfs and XFS use dynamic inodes to avoid inode limits. ZFS does not use inodes. Now we are full circle back to ZFS.

Grub2 for Linux, as in the form from Ubuntu, does not play well trying to read Native ZFS. There is a ppa for the "Native ZFS for Linux" team at [https://launchpad.net/~zfs-native/+archive/ubuntu/grub](https://launchpad.net/~zfs-native/+archive/ubuntu/grub). Not sure where they are with that at present...  I've used Linux mounted to ZFS pools, but honestly, my sys for that was on a more traditional Linux system /boot.

---

### Post by darkod on 2015-04-30
Yes, my slip up... Whether the container is zfs or mdadm wouldn't matter much, you still need to create a filesystem to use it.

Although according to the info posted ext4 on 64-bit ubuntu should support up to 50TB but I remember at least one other thread where the owner complained that using 64-bit ubuntu is limiting him to 16TB ext4 filesystem too. Not sure if that was clean install of the latest LTS, or upgrade from previous version, but being 64-bit should support larger ext4, no?

I haven't searched into details yet, the actual experiences with large ext4 on 64-bit ubuntu.

---

### Post by MAFoElffen on 2015-05-01
I think the toolset for that hit our repos with "updates" to 14.04 LTS. So the current updated toolset supports it. But as I remember, there is a particular option you have to include and do some things to support it:
Quoted from the directions/recipe I used:
> 
Before actually creating your filesystem, however, you are going to want to check and/or edit your /etc/mke2fs.conf file and to make sure that it enables the 64-bit feature flag automatically for a big disk. It should look something like this:
```

[fs_types]
    ext4 = {
        features = has_journal,extent,huge_file,flex_bg,uninit_bg,dir_nlink,extra_isize
        auto_64-bit_support = 1 # add this line
        inode_size = 256
    }

```
Finally, you are ready to create your volume! If you are having trouble with the standard tools, you can run this to manually specify your options:
```

# mke2fs -O 64bit,has_journal,extents,huge_file,flex_bg,uninit_bg,dir_nlink,extra_isize -i 4194304 /dev/vg0/lv_data

```
Now, you should be able to mount your volume and use it!
```

# mount /dev/vg0/lv_data /mnt
# cd /mnt

```

The  e2fsprogs toolset package needed to be greater or equal to version 1.42.7... Current in Trusty is 1.42.9, so you should now only have to give mke2fs the "64bit" option, without having to edit the config file for it beforehand.

---

