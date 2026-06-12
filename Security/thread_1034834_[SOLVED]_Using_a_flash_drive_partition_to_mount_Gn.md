---
title: "[SOLVED] Using a flash drive partition to mount GnuPG keys"
date: 2009-01-09
forum: Security
---

### Post by argie on 2009-01-09
I wish to do the following:

1. Partition a USB flash stick into a tiny (say 32 MB) ext3 partition, and a larger FAT partition.
2. Set it up so that Ubuntu will automatically mount the small partition to /home/myname/.gnupg/
3. Use the FAT partition to transfer files.

Will partitioning the USB drive result in any problems when using it on Windows?

How do I set up fstab so that #2 can be done? I understand you can do something like this with UUIDs but I have no clue how exactly they work.

Is this whole thing even possible?

---

### Post by argie on 2009-01-11
Here's a suggestion:

1. Use fdisk to partition, gparted doesn't seem to know how to do it.
```

sudo fdisk /dev/sdb
```
An important note at this stage: If you want Windows XP to be able to read your FAT partition, put it first. So when you're done /dev/sdb1 will be a big partition and /dev/sdb2 will be a small partition.
2. Use gparted to format the created partitions, this part is straightforward. But since I wanted a large partition to share files I made the large (1.7 GB) /dev/sdb1 partition a FAT16 partition, and the small (128 MB) /dev/sdb2 partition an ext2 partition. So that's what I did.
3. Use vol_id to find out the partition volume IDs:
```

sudo vol_id /dev/sdb2 | grep ID_FS_UUID

```
4. Edit /etc/fstab to always mount this filesystem at your .gnupg key location. So put the following at the bottom
```
# Keys
UUID=35b210fb-a068-409d-bfba-bbf365a674cd	/home/cow/.gnupg	ext3	rw,noauto,async,user	0	0

```
rw means read-write. noauto means it won't mount automatically at boot. async is good for flash drives. user means you don't have to be root to be able to use it. It also means that anyone can mount it, I think.

You are now done. As a bonus, use e2label to set the filesystem label:
```

sudo e2label /dev/sdb2 "keys"

```

If you want to set your FAT filesystem label too, use mlabel like so:
```

sudo mlabel -i /dev/sdb1 ::"CHOW"

```

You can use vol_id to check the partition labels.

Hope that helps.

---

### Post by argie on 2009-01-11
Oh thank you, that works just fine.

---

### Post by xpd259 on 2009-06-22
lol you didn't just have a convo with your self did you?
:D

---

### Post by Agent ME on 2009-06-22
Interesting informative post, but I found it a lot easier to simply symlink ~/.gnupg to a directory under /media/my-flashdrive-name.

Also a tip if you're using your keyring on a filesystem like FAT which doesn't support locking: add "lock-never" to the file "~/.gnupg/options" to get rid of the warning message about it.

---

