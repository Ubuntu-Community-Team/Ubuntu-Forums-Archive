---
title: "[SOLVED] Issue with fstab using discrete RAID card"
date: 2008-07-01
forum: Server Platforms
---

### Post by Titan8990 on 2008-07-01
I have been having a issue with my descrete RAID card. If I install Ubuntu or patch the kernel with my eSATA drive connected (not attached to my RAID controller) ubuntu will not boot giving a file not found error. 

Now the issue I am looking to solve here and the reason for this post is I would like my eSATA drive to automount via fstab. The problem is my fstab file currently looks like this:

```
jordan@einstein:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=eb90ff26-b99d-44b3-aedc-f641b6ed6faa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=567bbf65-3e84-4fc1-831e-74ee1603dd62 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

As you can see two partitions listed as sda1 sda2 are shown to be my main filesystem and automount on boot. This however is not the case. Whenever I attach my eSATA drive it will **always** get the drive letters sda. This really bothers me because I believe that it takes away from the fault tolerence of my server for it to change drive letters around when it feels like it.

The output of fdisk -l:

```
jordan@einstein:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10c310fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 250.0 GB, 250057219584 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b3151

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29920   240332368+  83  Linux
/dev/sdb2           29921       30401     3863632+  82  Linux swap /Solaris
```

How can I add sda1, my backup eSATA drive, to fstab so it will automount? Will fstab have a problem with two partitions listed as sda1 are in it&#347; list? Is there any way I can prevent Ubuntu from giving my external drive sda1? Is there anyway I can patch the kernel without it breaking?

Thank you in advance for any insight on this issue.

---

### Post by Titan8990 on 2008-07-01
Just an update, after a couple reboots the drive letters have once again changed.

root@einstein:/usr/share# sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250057219584 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b3151

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29920   240332368+  83  Linux
/dev/sda2           29921       30401     3863632+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10c310fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

---

### Post by Titan8990 on 2008-07-02
bump

---

### Post by Titan8990 on 2008-07-03
bump

---

### Post by fjgaude on 2008-07-03
I know what you are thinking but it is not as bad as you think. There has always been issues with drive naming, even Windows never solved the problem, but really it is not a true problem.

Ubunut uses UUIDs to mount and control drives no matter what the drive names happen to be.

So in your case, leave the UUIDs as they are in the fstab file, mount the eSATA and then see what its UUID is by using the ```
blkid
``` command.

After you know the eSATA's UUID use that in the fstab file:

```
gksu gedit /etc/fstab
```

Add this line to the bottom of the file:

```
UUID=nnn-nnn-nnn-nnn /media/mountpoint ext3 defaults 0 2
```

I assume you have the eSATA formatted as ext3 filesystem. Also use whatever mountpoint you wish.

Let us know what happens.

---

### Post by Titan8990 on 2008-07-03
Exactly what I was looking for, thank you. It worked perfectly, now i can remove the the part of my backup script that mounts the drive (and only works 50% of the time).

What does setting pass = 2 effect?

Also, will it be a big issue if it boots up and sda1 is not there?

---

### Post by fjgaude on 2008-07-03
Great, it's so good to find relief from a long-time issue.

Your question, it's the sixth field of a fstab file line... a zero (0) there means not to check filesystem at all, a 1 checks the filesystem, a 2 checks the filesystem after the "1" partition has been checked. The 1 usually is your boot partition, the first to be checked by fsck by the kernel scripts.

I found all this out from the **man fstab** pages.

Booting, I don't think so... but let us know.

Thanks for thanking me. <smile>

---

### Post by Titan8990 on 2008-07-03
I read the fstab man pages and my understanding was not quite the same as your explaination. Thank you for putting it better flavor of english for me.

---

