---
title: "Lost Mount point after reboot"
date: 2013-01-01
forum: Virtualisation
---

### Post by GoldTipu on 2013-01-01
I am running Ubuntu Server (latest updated )on Vmware ESX 5. 
I have mounted 60 GB Disk , disk is working fine i have copied the data in Disk . However i found issue every time i reboot the server i lost my mount point for the disk mounted disk  . 
- I ran MIBWalk to confirm that is true you can see the 60gb "/mnt/60gb" missing after reboot . I need to know if this is known issue ? or is there any fix for this to made that change permanent ? 


********** Before reboot *********

.1.3.6.1.2.1.25.2.3.1.2.35 = OID: 1.3.6.1.2.1.25.2.1.4
.1.3.6.1.2.1.25.2.3.1.3.1 = String: "Physical memory"
.1.3.6.1.2.1.25.2.3.1.3.3 = String: "Virtual memory"
.1.3.6.1.2.1.25.2.3.1.3.6 = String: "Memory buffers"
.1.3.6.1.2.1.25.2.3.1.3.7 = String: "Cached memory"
.1.3.6.1.2.1.25.2.3.1.3.8 = String: "Shared memory"
.1.3.6.1.2.1.25.2.3.1.3.10 = String: "Swap space"
.1.3.6.1.2.1.25.2.3.1.3.31 = String: "/"
.1.3.6.1.2.1.25.2.3.1.3.32 = String: "/sys/fs/fuse/connections"
.1.3.6.1.2.1.25.2.3.1.3.33 = String: "/dev"
.1.3.6.1.2.1.25.2.3.1.3.34 = String: "/boot"
[SIZE="3"].1.3.6.1.2.1.25.2.3.1.3.35 = String: "/mnt/60gb"[/SIZE] <<<<<< /mnt/60gb  missing in the MIBwalk after reboot  ..




********** After reboot *********

.1.3.6.1.2.1.25.2.3.1.3.1 = String: "Physical memory"
.1.3.6.1.2.1.25.2.3.1.3.3 = String: "Virtual memory"
.1.3.6.1.2.1.25.2.3.1.3.6 = String: "Memory buffers"
.1.3.6.1.2.1.25.2.3.1.3.7 = String: "Cached memory"
.1.3.6.1.2.1.25.2.3.1.3.8 = String: "Shared memory"
.1.3.6.1.2.1.25.2.3.1.3.10 = String: "Swap space"
.1.3.6.1.2.1.25.2.3.1.3.31 = String: "/"
.1.3.6.1.2.1.25.2.3.1.3.32 = String: "/sys/fs/fuse/connections"
.1.3.6.1.2.1.25.2.3.1.3.33 = String: "/dev"
.1.3.6.1.2.1.25.2.3.1.3.34 = String: "/boot"
.1.3.6.1.2.1.25.2.3.1.4.1 = INTEGER: 1024

Kind Regards
GoldTipu

---

### Post by Bashing-om on 2013-01-01
GoldTipu; Hi !

Do you have a correct entry for "/mnt/60gb" in /etc/fstab ?
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.comunity/Mount/](https://help.ubuntu.comunity/Mount/)
[INDENT]hth <== BDQ

[/INDENT]

---

### Post by GoldTipu on 2013-01-02
> **Bashing-om said:**
> GoldTipu; Hi !

Do you have a correct entry for "/mnt/60gb" in /etc/fstab ?
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.comunity/Mount/](https://help.ubuntu.comunity/Mount/)
[INDENT]hth <== BDQ

[/INDENT]

Thank you for the reply and link currently i am going through the details . i dont see the entry in fstab file for my 60gb disk . i have simply used fdisk and them mounted 

sudo mkdir /mnt/60gb
sudo mount /dev/sdb /mnt/60gb -fl

then i ran the mibwalk and find the disk is available under mibs . then i did sudo mount to verify the mount is available .  is this correct way to mount ? 

***************mount *****************
/dev/mapper/WebServer--Linux-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sda1 on /boot type ext2 (rw)
/dev/sdb on /mnt/60gb type none (rw)


*************** fsbtab *************
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/WebServer--Linux-root /               ext4    errors=remount-ro 0                                             1
# /boot was on /dev/sda1 during installation
UUID=a070ba72-5b83-4ec7-a604-276df6c9372e /boot           ext2    defaults                                              0       2
/dev/mapper/WebServer--Linux-swap_1 none            swap    sw              0                                             0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



***************** fdisk *****************

Disk /dev/sdb: 64.4 GB, 64424509440 bytes
255 heads, 63 sectors/track, 7832 cylinders, total 125829120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders, total 20971520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e5db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758    20969471    10233857    5  Extended
/dev/sda5          501760    20969471    10233856   8e  Linux LVM

Disk /dev/mapper/WebServer--Linux-root: 9403 MB, 9403629568 bytes
255 heads, 63 sectors/track, 1143 cylinders, total 18366464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/WebServer--Linux-root doesn't contain a valid partition table

Disk /dev/mapper/WebServer--Linux-swap_1: 1073 MB, 1073741824 bytes
255 heads, 63 sectors/track, 130 cylinders, total 2097152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/WebServer--Linux-swap_1 doesn't contain a valid partition table

***************blkid ******************
/dev/sda1: UUID="a070ba72-5b83-4ec7-a604-276df6c9372e" TYPE="ext2"
/dev/sda5: UUID="l7zcuR-4azf-Ze6G-ZJEr-f3tM-5GoB-Bleb89" TYPE="LVM2_member"
/dev/mapper/WebServer--Linux-root: UUID="4ac7c04e-1a18-4e56-b3c5-86bae1c99a5b" TYPE="ext4"
/dev/mapper/WebServer--Linux-swap_1: UUID="98cab820-75eb-4cfa-865f-9b2b68d79bbc" TYPE="swap"

---

### Post by Bashing-om on 2013-01-02
GoldTipu;

From the outputs provided you are using LVM device management on your server. I do not have the knowledge to advise on how to add the sdb as a volume to the volume group and mount that group, nor how to configure the physical space for LVM.

Others will have to advise on this matter.


[INDENT][INDENT]best regards <== BDQ

[/INDENT][/INDENT]

---

