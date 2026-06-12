---
title: "Need recommendations/tips for partitioning and installed software..."
date: 2011-01-22
forum: Server Platforms
---

### Post by greennewb on 2011-01-22
I have the following setup on a dedicated server I just purchased:

Result of 'df -h' (as root):

Filesystem            Size  Used Avail Use% Mounted on
/dev/md1              3.7G  397M  3.3G  11% /
none                  992M  192K  992M   1% /dev
none                  997M     0  997M   0% /dev/shm
none                  997M     0  997M   0% /tmp
none                  997M   48K  997M   1% /var/run
none                  997M     0  997M   0% /var/lock
none                  997M     0  997M   0% /lib/init/rw
/dev/mapper/vg00-usr  4.0G  523M  3.5G  13% /usr
/dev/mapper/vg00-var  4.0G  141M  3.9G   4% /var
/dev/mapper/vg00-home 4.0G  4.2M  4.0G   1% /home

This is primarily for a web server but I want to be able to have plenty of space for other tasks as well.  This is supposedly 250GB in some RAID configuration of which only about 22GB appears to be used right now (see bottom of post for more details).

I know enough of the Linux command line to be dangerous but not savvy.  Kind of like being given a sword without any training - I'd flail it around thinking I look cool but end up losing a hand or foot.

Anyway, it looks like I get to install Apache (or maybe tinker with nginx?) and MySQL too.  But, before I set up any of that, I also want VMWare Player on the box.  Can VMWare Player be downloaded from the VMWare servers, installed, and run entirely from the command-line or do I need to install the full Ubuntu desktop environment (Gnome) on the server?  And if I need to install the GUI, how do I do that and then how do I access it given that I don't have physical access to the box?

Is 4GB for the '/' mount big enough?  What should I be looking to set the other mounts to - sort of looking for "good rules of thumb" here?


Result of 'mount':

/dev/md1 on / type ext3 (rw)
none on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /tmp type tmpfs (rw)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/mapper/vg00-usr on /usr type xfs (rw)
/dev/mapper/vg00-var on /var type xfs (rw,usrquota)
/dev/mapper/vg00-home on /home type xfs (rw,usrquota)


Result of 'fdisk -l':

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x57e57882

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         487     3911796   fd  Linux raid autodetect
/dev/sda2             488         731     1959930   82  Linux swap / Solaris
/dev/sda3             732       30401   238324275   fd  Linux raid autodetect

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe79f5e04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         487     3911796   fd  Linux raid autodetect
/dev/sdb2             488         731     1959930   82  Linux swap / Solaris
/dev/sdb3             732       30401   238324275   fd  Linux raid autodetect

Disk /dev/md3: 244.0 GB, 244043939840 bytes
2 heads, 4 sectors/track, 59581040 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md3 doesn't contain a valid partition table

Disk /dev/md1: 4005 MB, 4005560320 bytes
2 heads, 4 sectors/track, 977920 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

---

