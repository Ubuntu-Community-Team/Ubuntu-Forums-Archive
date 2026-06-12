---
title: "Ubuntu Server 10.04 /boot to big"
date: 2010-11-18
forum: Server Platforms
---

### Post by pras on 2010-11-18
Hi all,

I have an Ubuntu  10.04 server and I keep getting a message that my /boot is 99% used. 
I removed all the old kernels in the past (when I get a message that my system uses 100% of the /boot).

How can I clear up my /boot because the Size is 227.73 MB with Free 2.28 MB

Do I have to check something else?

Thank you!

Christos  :p

---

### Post by CharlesA on 2010-11-18
You can just remove the old kernels with apt-get or by just deleting them from /boot.

Just make sure you don't delete the kernel you are using.

---

### Post by pras on 2010-11-18
> **CharlesA said:**
> You can just remove the old kernels with apt-get or by just deleting them from /boot.

Just make sure you don't delete the kernel you are using.

Hi CharlesA,

Thank you for your prompt answer!

I already delete the old kernel....
The Size is 227.73 MB with Free 2.28 MB (99% full) only with latest kernel!

Any other suggestion?

Thank you

Christos

---

### Post by CharlesA on 2010-11-18
Can you run this and post the output:

```
ls -l /boot
```

---

### Post by pras on 2010-11-18
The output is

```
total 15510
drwxr-xr-x 2 root root    1024 2010-10-30 13:33 2010-10-30-10-img
-rw-r--r-- 1 root root  655316 2010-10-17 03:03 abi-2.6.32-25-generic-pae
-rw-r--r-- 1 root root  116502 2010-10-17 03:03 config-2.6.32-25-generic-pae
drwxr-xr-x 3 root root    4096 2010-11-18 21:15 grub
-rw-r--r-- 1 root root 8961725 2010-11-18 21:15 initrd.img-2.6.32-25-generic-pae
drwxr-xr-x 2 root root   12288 2010-10-09 13:42 lost+found
-rw-r--r-- 1 root root  160280 2010-03-23 11:37 memtest86+.bin
-rw-r--r-- 1 root root 1730990 2010-10-17 03:03 System.map-2.6.32-25-generic-pae
-rw-r--r-- 1 root root    1200 2010-10-17 03:05 vmcoreinfo-2.6.32-25-generic-pae
-rw-r--r-- 1 root root 4167200 2010-10-17 03:03 vmlinuz-2.6.32-25-generic-pae

```

---

### Post by CharlesA on 2010-11-18
That looks normal. The largest file looks to be around 8MB.

Is /boot on a seperate partition?

Run this:

```
du -h
```
```
mount
```

---

### Post by pras on 2010-11-18
The /boot is not on a separate partition.

If the biggest file is about 8MB.... where goes all the other 220MB?

Do you want me to post any other output of a command?

---

### Post by CharlesA on 2010-11-18
Please post the output of "mount" and we'll go from there. :)

---

### Post by pras on 2010-11-18
here it is

```
/dev/mapper/Ogts-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
/dev/sda1 on /boot type ext2 (rw)
```

---

### Post by CharlesA on 2010-11-18
It looks like /boot is on another drive/partition.

Can you post the output of this:

```
sudo fdisk -l
```

---

### Post by pras on 2010-11-18
Here is the output

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000500b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       60802   488135681    5  Extended
/dev/sda5              32       60802   488135680   8e  Linux LVM

```

---

### Post by CharlesA on 2010-11-18
How is your machine set up? Encrypted LVM?

It looks like /boot is on it's own partition, but I don't know why it would be set up like that outside of the above scenario.

---

### Post by pras on 2010-11-19
Hi CharlesA,

No my machine is not set up as encrypted LVM.

---

### Post by CharlesA on 2010-11-19
can you post the output this please:

```
df -h
```

---

