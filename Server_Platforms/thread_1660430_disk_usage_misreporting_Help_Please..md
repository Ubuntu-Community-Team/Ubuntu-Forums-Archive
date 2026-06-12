---
title: "disk usage misreporting? Help Please."
date: 2011-01-05
forum: Server Platforms
---

### Post by ARhere on 2011-01-05
Hello people-who-are-smarter-then-me.

I think the available disk space on my date drives is being mis-reported.  I have a home built NAS running Ubuntu Server 10.04.1 with an OS disk (sdc) and two data disks (sda and sdb).  The partition sda1 is mounted at /data/main and sdb1 is mounted at /data/bkup and each night /data/bkup is mirrored to /data/main using rsync.
```
$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=8a55cba3-e158-45e4-a4a6-aa5eced5a1ea /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=42bb2a84-56e6-43ac-a839-9754dcd41711 none            swap    sw              0       0
/dev/sda1	/data/main	auto defaults 0 0
/dev/sdb1	/data/bkup	auto defaults 0 0

```

Last back up the OS and df report the drives are almost full.
```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1             6.6G  3.7G  2.6G  59% /
none                  490M  288K  490M   1% /dev
none                  494M  124K  494M   1% /dev/shm
none                  494M  3.4M  491M   1% /var/run
none                  494M     0  494M   0% /var/lock
none                  494M     0  494M   0% /lib/init/rw
/dev/sda1             463G  427G   12G  98% /data/main
/dev/sdb1             463G  438G  1.8G 100% /data/bkup

```

However, the drives should have about +100GB space left on each and the Disk Usage Analyzer tool reports this correctly.  Notice /data/main is only 326GB and /data/bkup is only 350GB and there are no other mounts to those disks.  What is going on!?  Suggestions to help debug please?
[IMG]http://www.arhere.com/help/DUA.png[/IMG]

Thank you,
-AR

---

### Post by dtfinch on 2011-01-05
I'm not at a system where I can test this, but I think the disk usage analyzer ignores hidden files and folders by default.

---

### Post by ARhere on 2011-01-05
Hi,

I do not see an option for this.  where is this set?

-AR

EDIT:  I checked and hidden files are being shown.  More ideas please?
[IMG]http://www.arhere.com/help/DUA2.png[/IMG]

---

### Post by psusi on 2011-01-05
What does sudo du -sh /data/main say?

---

### Post by Skadork on 2011-01-05
if i'm not mistaken - df shows the amount of free blocks.  You can see the discrepancies if you have large blocks and many small files.

here's an example:  if you have a file system that is 100MB in size with a block size of 1MB and and a single file on the file system that is one single byte (1 Byte).  df will report that there are only 99 MB remaining because df only shows how many free blocks there are.


Instead, trying issuing the following command to show the directory contents:
> du -h /data/main Another option that could be causing the discrepancy is that there could be a file is still open and has been deleted so the space is still "allocated" until the process that is keeping the file open is finished.  For further reading, try this link: [http://gcolpart.evolix.net/blog21/df-command-vs-du-command/](http://gcolpart.evolix.net/blog21/df-command-vs-du-command/)

---

