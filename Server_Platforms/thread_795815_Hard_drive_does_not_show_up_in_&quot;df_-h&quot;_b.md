---
title: "Hard drive does not show up in &quot;df -h&quot; but is mounted"
date: 2008-05-15
forum: Server Platforms
---

### Post by ocdude on 2008-05-15
I am incredibly confused. Here goes:

Back in December or so I added a hard drive to my web server. During the process, I formatted it and added it to /etc/fstab so it would automatically mount on boot.

However, now I'm noticing that when I run df -h, it does not show up in the list. Furthermore, the mount point that it's supposed to be on has stuff in it, but now I'm wondering if it is actually on the hard drive I installed or on the main boot disk.

Here is the results of df -h:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G  5.2G   30G  15% /
varrun                471M  236K  471M   1% /var/run
varlock               471M     0  471M   0% /var/lock
udev                  471M   40K  471M   1% /dev
devshm                471M     0  471M   0% /dev/shm

```And the results of fdisk -l (as sudo):

```


Disk /dev/sda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca20ca20

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4798    38539903+  83  Linux
/dev/sda2            4799        5005     1662727+   5  Extended
/dev/sda5            4799        5005     1662696   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux


```and finally, my /etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=9dbe8086-8d06-42b6-b43e-ca9fcfb03e38 / ext3 defaults,errors=remount-ro,usrq
uota,grpquota 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=12475df8-ba14-495e-ba3e-a87d7036215a none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

```Note, I don't see the drive anywhere in fstab, which probably means I did not set something up correctly. It's supposed to be mounted at /multimedia

I run a small webserver and I do not have physical access to the machine (400 miles away).

Did I just fail to add the drive to /etc/fstab?

I should probably add that the drive is formatted as ext3 if that makes any difference.

---

### Post by p_quarles on 2008-05-15
No, the drive isn't mounted. The fact that it shows up in fdisk -l only means that it's attached. 

You'll need to add it to /etc/fstab manually.

---

### Post by ocdude on 2008-05-15
Aha! I knew I was missing something somewhere. Thanks. I guess I just needed another set of eyes to catch what I was missing.

---

### Post by MJN on 2008-05-16
Remember to remove/move the stuff out of the mount point (/multimedia) before mounting the drive otherwise you'll be wasting space and/or have an inconsistent set of files.
 
You may prefer to temporarily mount your other drive elsewhere, copy the stuff from /multimedia to it, clear out /multimedia, then mount the drive on /multimedia (either manually or via fstab).
 
Mathew

---

### Post by ocdude on 2008-05-16
Thanks dudes. When I actually mounted the drive I mounted it to /mnt/multimedia and copied everything over from /multimedia, deleting the originals freeing up space. Thanks again.

---

