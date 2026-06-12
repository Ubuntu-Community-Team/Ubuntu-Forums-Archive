---
title: "User Home Dir Issue on Ubuntu 8.04 Server"
date: 2010-09-02
forum: Server Platforms
---

### Post by freakrz on 2010-09-02
Hello,

   I am running Bugzilla Server on Ubuntu 8.04 64bit. its been up and running for about3 weeks. I am also using backuppc on ubuntu 8.04 on another VM for backup's , today i noticed that the backup is'nt done.so i logged into the Bugzilla using a regular user account and noticed that its not mounting my user folder in the home dir.so i wanted to check if any issues and $cd /home then i see the root directory and i tried to check the home dir within $cd /home there lies my user folders,so my home folders are in $cd /home/home and there is an entire root dir in the /home dir.i am not sure how this happend,do you think the /home dir is linked to /,which log would provide me the last changes done.i am not sure of doing any changes,the last time the machine was shutdown for Vmware maintenance purpose.could there be a possibility of intrusion or fraudulent act. 

Thank You.

Frk

---

### Post by clrg on 2010-09-02
Did you mount your / partition on both / and /home? What does ```
cat /etc/fstab && cat /etc/mtab && mount && sudo fdisk -l
```

show?

---

### Post by freakrz on 2010-09-03
> **clrg said:**
> Did you mount your / partition on both / and /home? What does ```
cat /etc/fstab && cat /etc/mtab && mount && sudo fdisk -l
```

show?

Output for the above command

[I]> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0387c295-66a6-4cdd-8ed8-8513407166c7 /home               ext3    relatime,errors=remount-ro,usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0   0       1
# /dev/sda5
UUID=0477f600-2c82-4d3f-963d-21f722b31bed none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/sda1 /home ext3 rw,relatime,errors=remount-ro,usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0 0 0
securityfs /sys/kernel/security securityfs rw 0 0
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda1 on /home type ext3 (rw,relatime,errors=remount-ro,usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0)
securityfs on /sys/kernel/security type securityfs (rw)

Disk /dev/sda: 5368 MB, 5368709120 bytes
255 heads, 63 sectors/track, 652 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00013572

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         617     4956021   83  Linux
/dev/sda2             618         652      281137+   5  Extended
/dev/sda5             618         652      281106   82  Linux swap / Solaris
[/I]
I also have an error while booting up.check the image below

---

### Post by clrg on 2010-09-03
It looks like one of your filesystems is messed up (hence the e2fsck failure). What have you done?

---

### Post by freakrz on 2010-09-03
The last i remember is i had to reboot coz of changes being made to Vmware Esxi and after the reboot it worked for about a day and then on i noticed the issue.This is a new system and i luckyly dont have any data on it, i guess its better to redo the entire system then.

---

