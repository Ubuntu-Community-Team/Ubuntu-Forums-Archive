---
title: "Cannot paste or move items on FAT partiton"
date: 2012-03-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by x-shaney-x on 2012-03-18
I have a FAT32 partition which I use for shared storage between OS's.
The partition is auto-mounted via an fstab entry which was created during installation. 

In 12.04, I am unable to cut/copy and paste or move any items anywhere on the partition, either within the partition or from other partitions.

Strangely, I AM able to create files and folders and delete items from the partition.

If I boot into 11.10, which has an identical fstab entry, I am able to copy/paste/move files on that partition normally.
```
# /mnt/Data was on /dev/sda3 during installation
UUID=9996-53A4  /mnt/Data       vfat    utf8,umask=007,gid=46 0       1
```

```
drwxrwx--- 5 root plugdev 16384 Mar 18 08:01 Backup
drwxrwx--- 9 root plugdev 16384 Mar 16 11:35 Multimedia
drwxrwx--- 7 root plugdev 16384 Mar  7 19:11 Shared
drwxrwx--- 2 root plugdev 16384 Mar 15 10:33 temp
```

---

### Post by WasMeHere on 2012-03-18
Hi x-shaney-x,

Please post the output of ```
ls -l
``` and
```
cat /etc/mtab
``` for both 12.04 and 11.10! Maybe it will be different although the fstab entries are the same.

Have fun finding out
Olle

---

### Post by x-shaney-x on 2012-03-18
The ls -l entries for both 11.10 and 12.04 are identical, as listed in my last post.

mtab 11.10: ```
$ cat /etc/mtab
/dev/sda7 / ext4 rw,errors=remount-ro,user_xattr,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda3 /mnt/Data vfat rw,utf8,umask=007,gid=46 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/shane/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=shane 0 0
```

mtab 12.04: ```
$ cat /etc/mtab
/dev/sda8 / ext4 rw,errors=remount-ro,user_xattr 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda3 /mnt/Data vfat rw,utf8,umask=007,gid=46 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/shane/.cache/gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=shane 0 0
gvfs-fuse-daemon /root/.cache/gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0
```

---

### Post by WasMeHere on 2012-03-18
From mtab it points to /dev/sda:
```
/dev/sda3 /mnt/Data vfat rw,utf8,umask=007,gid=46 0 0
```
and it looks exactly the same in both cases while the root file system entries look slightly different
```
< /dev/sda7 / ext4 rw,errors=remount-ro,user_xattr,commit=0 0 0
---
> /dev/sda8 / ext4 rw,errors=remount-ro,user_xattr 0 0
```
I don't know why it doesn't work, maybe someone else reading this can tell. Or maybe you have found a bug in 12.04.

Does it work, if you exclude the drive from fstab and mount it manually with the file browser?

---

### Post by x-shaney-x on 2012-03-18
Strangely enough, I can now move files and paste etc.

I haven't changed anything, all that I can think of is when it was mounted in 11.10 (which I haven't used very recently) to check things there, it fixed whatever was wrong.

---

### Post by WasMeHere on 2012-03-18
> **x-shaney-x said:**
> Strangely enough, I can now move files and paste etc.

I haven't changed anything, all that I can think of is when it was mounted in 11.10 (which I haven't used very recently) to check things there, it fixed whatever was wrong.
Yes, that might be the case, or maybe there was an update of 12.04, that fixed it. Anyway, post again if your problem comes back!

---

### Post by VMC on 2012-03-18
Good topic. I have a slightly different situation. 

I have NTFS partition that I can easily move between 4 OS's.

That mtab is:

```
/dev/sda2 /media/NTFS fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0

```
I also have a ext4 partition that I can move files to and from, but not on its root. that mtab is:

```
/dev/sda9 /media/SAVE ext4 rw,nosuid,nodev,uhelper=udisks 0 0
```

I cannot use the Backup program on the ext4 but can on the ntfs partition.

The ntfs partition lies outside on a primary partition, while the ext4 is inside on an extended partition. That might be my issue.

I've tried on Mint, Fedora and any Ubuntu OS. All have the same problem.

Regarding FAT file system. I've never had issue with copying and/or pasting.

---

