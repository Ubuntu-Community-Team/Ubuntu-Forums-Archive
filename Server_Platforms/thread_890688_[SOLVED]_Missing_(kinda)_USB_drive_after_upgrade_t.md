---
title: "[SOLVED] Missing (kinda) USB drive after upgrade to 8.0.4"
date: 2008-08-15
forum: Server Platforms
---

### Post by TWGTech on 2008-08-15
I upgraded Ubuntu Server 6.06.2 to 8.04.1 on a Dell 2450. Prior to the upgrade, my USB drive was showing in DF and Mount. After the upgrade, I cannot see it in either command, but I can still access it. If I run a Mount -a, I receive the error "mount: unknown filesystem type 'linux_raid_member'".

Here's the detail of the above commands, as well as my /etc/fstab file...

root@gldubsec01:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              9.2G  5.1G  3.8G  58% /
varrun               1014M   56K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   84K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
/dev/md1               56G  1.2G   52G   3% /home
root@gldubsec01:/# mount
/dev/md0 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/md1 on /home type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
root@gldubsec01:/# mount -a
mount: unknown filesystem type 'linux_raid_member'
root@gldubsec01:/# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0 -- converted during upgrade to edgy
UUID=e2fc596b-9946-4a3c-95fa-af030f832043 / ext3 defaults,errors=remount-ro 0 1
# /dev/md1 -- converted during upgrade to edgy
UUID=8f1a7b9d-762b-4c55-998a-967ac42f3c91 /home ext3 defaults 0 2
# /dev/md2 -- converted during upgrade to edgy
UUID=8966a6f7-3b5e-4e37-a0a3-4ff27904c9c3 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/usb0     auto    defaults        0       0

I have all of my data off of the USB drive, so formatting is an option, but I would like to know why this is the way it is, since I have 15 more systems to upgrade, and don't want to format all of my USB devices.

I searched the forums and googled with little results, so if I missed a current fix, please add the link.

Any help is greatly appreciated.

---

### Post by TWGTech on 2008-08-15
Found it. 

FSTAB shows /dev/sda1 /media/usb0
After the upgrade, my device moved to /dev/sdc1

Tested mount with mount -t ext3 /dev/sdc1 /media/usb0

worked.

Modified /etc/fstab to reflect the new dev location.

---

