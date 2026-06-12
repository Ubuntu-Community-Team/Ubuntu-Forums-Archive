---
title: "Ubuntu server 8.04 hard drive upgrade"
date: 2010-06-05
forum: Server Platforms
---

### Post by eatont9999 on 2010-06-05
Hello,

I am in need of help upgrading my server's drive to a larger one. I am running ubuntu server 8.04 on an Athlon 2000 with 2GB RAM. This server has multiple tasks and some are divided up on VMs via VMware 2. Originally the server had a single 80GB drive and every thing was setup on that drive. I added a 1TB software RAID for file storage, but the boot drive is 80% used. I have a 160GB drive I would like to use to replace the current 80GB drive. I used Ghost 11 to clone the old drive to the new one and setup the partitions to size. 

When I boot off the new drive, I get a grub "error 2." I am using grub 1.5. I have read some things online that say the uuid is wrong in grub and fstab. I am not sure how to go about fixing this so it boots. The articles I read were quite out of date and I don't want to screw this up. 

Because I know someone will ask, here is the following:

teaton@teserver2:~$ ls -al /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root 100 2010-06-05 14:32 .
drwxr-xr-x 5 root root 100 2010-06-05 10:32 ..
lrwxrwxrwx 1 root root   9 2010-06-05 14:32 13f5fe0d-dfd2-4cba-bae2-0877714e20df -> ../../md0
lrwxrwxrwx 1 root root  10 2010-06-05 10:32 e1418127-1643-4983-baf8-0969fef331a5 -> ../../sdc5
lrwxrwxrwx 1 root root  10 2010-06-05 10:32 f5f7510c-6c73-4c6b-8188-7e3b4c5b6895 -> ../../sdc1

^^New 160GB drive is NOT attached now, but when it is, the output above is the same.^^

teaton@teserver2:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=f5f7510c-6c73-4c6b-8188-7e3b4c5b6895 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=e1418127-1643-4983-baf8-0969fef331a5 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/md0        /mnt/md0        ext3     defaults,errors=remount-ro  0   1


Thanks all!

---

### Post by volkswagner on 2010-06-06
I would try using a live CD of your choice.

Boot the system with the 160GB drive connected.

After booting the live CD run:

Mount the 160GB drive somewhere such as /tmp.

Change to /tmp

```
cd /tmp
```

Backup your /etc/fstab

```
sudo cp etc/fstab etc/fstab.bak
```

Replace the uuid with /dev/xxxx from fstab file, it is commented out above the uuid.

ie:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb1
**/dev/sdb1 / ext3 relatime,errors=remount-ro 0 1**
# /dev/sdb5
UUID=e1418127-1643-4983-baf8-0969fef331a5 none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

/dev/md0 /mnt/md0 ext3 defaults,errors=remount-ro 0 1
```

Also make sure on the 160GB drive grub "knows" where root disk is.

```
cat boot/grub/device.map
```

Make sure (hd0) matches your 160GB drive (root device name not partition name, from fstab without the partition number, should be /dev/sdb).

If not backup and edit.

Please note the above commands I dropped the leading slash to make sure you edit inside /tmp where you mounted the 160GB drive, or you may be editing the virtual file system of the live CD.

Also make sure the 160GB disk is bootable.

```
sudo cfdisk /dev/sdb
```


Make sure the boot flag is set.

You should now be able to boot the 160GB disk, if not, you still may need to [reinstall grub]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by eatont9999 on 2010-06-06
Thanks, that seemed to work great. The only long-term concern I have is that when the system boots, it says that lines 5 and 7 are incorrect. Those lines are the ones we un-commented. Here is /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
 /dev/sdb1
#UUID=f5f7510c-6c73-4c6b-8188-7e3b4c5b6895 /               ext3    relatime,erro
 /dev/sdb5
#UUID=e1418127-1643-4983-baf8-0969fef331a5 none            swap    sw
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/md0        /mnt/md0        ext3     defaults,errors=remount-ro  0   1




The machine does boot and everything seems in order. Just wondering about those lines.

Thanks again!

---

### Post by volkswagner on 2010-06-06
> **eatont9999 said:**
> Thanks, that seemed to work great. The only long-term concern I have is that when the system boots, it says that lines 5 and 7 are incorrect. Those lines are the ones we un-commented. Here is /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
 /dev/sdb1
#UUID=f5f7510c-6c73-4c6b-8188-7e3b4c5b6895 /               ext3    relatime,erro
 /dev/sdb5
#UUID=e1418127-1643-4983-baf8-0969fef331a5 none            swap    sw
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/md0        /mnt/md0        ext3     defaults,errors=remount-ro  0   1




The machine does boot and everything seems in order. Just wondering about those lines.

Thanks again!

Your fstab should look like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb1
**/dev/sdb1 / ext3 relatime,errors=remount-ro 0 1**
# /dev/sdb5
**/dev/sdb5 none swap sw 0 0**
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

/dev/md0 /mnt/md0 ext3 defaults,errors=remount-ro 0 1
```

But now that you have it running you should be able to ssh into the box and edit fstab with the correct uuid, but it should work without error just using /dev/sdbx.

Notice, you did not list the mount point after your /dev/sdb1 and /dev/sdb5.

---

### Post by eatont9999 on 2010-06-07
I should have caught that. I made the changes and rebooted. The error messages went away and df -h shows my volume with the correct space. 

Thanks for your help. Very well written. I appreciate it!

-Tim

---

