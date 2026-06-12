---
title: "Trying to format external 1TB drive, df reports only 204M space? eh?"
date: 2009-04-25
forum: Server Platforms
---

### Post by submute on 2009-04-25
What I'm doing..

```
root@felix:~# sudo mkfs.ext3 /dev/sde1
mke2fs 1.41.3 (12-Oct-2008)
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
51200 inodes, 204800 blocks
10240 blocks (5.00%) reserved for the super user
First data block=1
Maximum filesystem blocks=67371008
25 block groups
8192 blocks per group, 8192 fragments per group
2048 inodes per group
Superblock backups stored on blocks: 
	8193, 24577, 40961, 57345, 73729

Writing inode tables: done                            
Creating journal (4096 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 28 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

```

Then...

```
sudo umount /mnt/dongle
```

/mnt/dongle is in fstab via:

```
/dev/sde1       /mnt/dongle     ext3
```

Then df -h says:

```
/dev/sde1             194M  5.6M  179M   4% /mnt/dongle
```

What gives? What am I doing wrong? This is a 1TB drive connected via USB...

Thanks!

---

### Post by Zeosa on 2009-04-25
What is the output of 'fdisk -l /dev/sde' ?

---

### Post by submute on 2009-04-26
Thanks- I ended up getting. The disk prior had configured two partitions (sde1 and 2), the latter being the bigger one. I just ran fdisk and made one partition on the disk, formatted it w/ ext3, and all is well.

---

