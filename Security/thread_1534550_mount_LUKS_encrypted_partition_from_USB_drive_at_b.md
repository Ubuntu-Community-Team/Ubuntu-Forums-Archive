---
title: "mount LUKS encrypted partition from USB drive at boot"
date: 2010-07-19
forum: Security
---

### Post by BarryDocks on 2010-07-19
HELP!!!
I have managed to encrypt a partition on my HDD which mounts with a passphrase at boot.  I basically followed these to guides:
[http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile]("http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile")
[http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/]("http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/")

here are the steps I took:
```
:~# apt-get install cryptsetup

:~# nano /etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
aes
dm-crypt
dm_mod

:~# nano /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# /boot was on /dev/sda1 during installation
UUID=c39d70a8-ac50-4a0e-8cf6-efd409d26c62 /boot           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=c1d8ce50-554a-44b9-ba0d-d7514076f0b7 none            swap    sw              0       0
# / was on /dev/sda3 during installation
UUID=c873bbe3-37d3-49e9-8f76-37bccb1e07c3 /               ext4    errors=remount-ro 0       1
# /media/disc was on /dev/sda4 during installation
##UUID=ed0d76a6-0655-47fa-a97d-ce7042ac274d /media/disc     ext4    defaults        0       2
#
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

:~# umount /dev/sda4
:~# cryptsetup luksFormat /dev/sda4

WARNING!
========
This will overwrite data on /dev/sda4 irrevocably.

Are you sure? (Type uppercase yes): YES
Enter LUKS passphrase: 
Verify passphrase: 


:~# cryptsetup luksOpen /dev/sda4 encrypt
Enter passphrase for /dev/sda4: 
Key slot 0 unlocked.

:~# mkfs.ext4 /dev/mapper/encrypt
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
609600 inodes, 2435199 blocks
121759 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2495610880
75 block groups
32768 blocks per group, 32768 fragments per group
8128 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 27 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

:~# mkdir /media/encrypt

:~# mount /dev/mapper/encrypt /media/encrypt

:~# fdisk -l

Disk /dev/sda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00070bfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13       96256   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              13          61      390144   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3              61        1398    10741760   83  Linux
/dev/sda4            1398        2611     9741312   83  Linux


:~# mount
/dev/sda3 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda1 on /boot type ext4 (rw)
/dev/mapper/encrypt on /media/encrypt type ext4 (rw)

:~# nano /etc/crypttab

# <target name> <source device>         <key file>      <options>
encrypt         /dev/sda4       none    luks

:~# nano /etc/fstab

  GNU nano 2.2.2                                File: /etc/fstab                                                                       

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# /boot was on /dev/sda1 during installation
UUID=c39d70a8-ac50-4a0e-8cf6-efd409d26c62 /boot           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=c1d8ce50-554a-44b9-ba0d-d7514076f0b7 none            swap    sw              0       0
# / was on /dev/sda3 during installation
UUID=c873bbe3-37d3-49e9-8f76-37bccb1e07c3 /               ext4    errors=remount-ro 0       1
# /media/disc was on /dev/sda4 during installation
##UUID=ed0d76a6-0655-47fa-a97d-ce7042ac274d /media/disc     ext4    defaults        0       2
#
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# CryptoDevices
/dev/mapper/encrypt     /media/encrypt  auto    defaults        0       0

```

Now I want to mount the partition at boot from a keyfile on a usb drive and took help from here:
[http://www.debianhelp.org/node/6797]("http://www.debianhelp.org/node/6797")

here are the steps I took:
```
:~# fdisk -l

Disk /dev/sda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00070bfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13       96256   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              13          61      390144   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3              61        1398    10741760   83  Linux
/dev/sda4            1398        2611     9741312   83  Linux

Disk /dev/sdb: 2006 MB, 2006728704 bytes
62 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c5862

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1019     1958487    c  W95 FAT32 (LBA)

:~# mkdir /media/usbkey
:~# mount /dev/sdb1 /media/usbkey
:~# mount
/dev/sda3 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda1 on /boot type ext4 (rw)
/dev/mapper/encrypt on /media/encrypt type ext4 (rw)
/dev/sdb1 on /media/usbkey type ext4 (rw)

:~#reboot

:~# nano /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# /boot was on /dev/sda1 during installation
UUID=c39d70a8-ac50-4a0e-8cf6-efd409d26c62 /boot           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=c1d8ce50-554a-44b9-ba0d-d7514076f0b7 none            swap    sw              0       0
# / was on /dev/sda3 during installation
UUID=c873bbe3-37d3-49e9-8f76-37bccb1e07c3 /               ext4    errors=remount-ro 0       1
# /media/disc was on /dev/sda4 during installation
##UUID=ed0d76a6-0655-47fa-a97d-ce7042ac274d /media/disc     ext4    defaults        0       2
#
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1      /media/usbkey   auto    defaults        0       0

# CryptoDevices
/dev/mapper/encrypt     /media/encrypt  auto    defaults        0       0

:~# mount -a
:~# mount
/dev/sda3 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda1 on /boot type ext4 (rw)
/dev/mapper/encrypt on /media/encrypt type ext4 (rw)
/dev/sdb1 on /media/usbkey type ext4 (rw)

:~# cd /media/usbkey
:/media/usbkey# ls
lost+found

:/media/usbkey# dd if=/dev/urandom of=/media/usbkey/keyfile1 bs=1024 count=4 
4+0 records in
4+0 records out
4096 bytes (4.1 kB) copied, 0.00268162 s, 1.5 MB/s

:/media/usbkey# chmod 0400 /media/usbkey/keyfile1
:/media/usbkey# cryptsetup luksAddKey /dev/sda4 /media/usbkey/keyfile1
Enter any passphrase: 
Verify passphrase: 
Key slot 0 unlocked.

cd /root

:~#nano /etc/crypttab
# <target name> <source device>         <key file>      <options>
#encrypt                /dev/sda4       /media/usbkey/keyfile1  luks
encrypt         /dev/sda4       none    luks

:~#nano /etc/default/cryptdisks
# Run cryptdisks at startup ?
CRYPTDISKS_ENABLE=Yes

# Mountpoints to mount, before starting cryptsetup. This is useful for
# keyfiles on removable media. Seperate mountpoints by space.
#CRYPTDISKS_MOUNT=""
CRYPTDISKS_MOUNT="/media/usbkey"

# Default check script, see /lib/cryptsetup/checks/
# Takes effect, if the 'check' option is set in crypttab without a value
CRYPTDISKS_CHECK=blkid

# Default precheck script, see
# Takes effect, if the 'precheck' option is set in crypttab without a value
CRYPTDISKS_PRECHECK=

:~#update-initramfs -u
:~#reboot
```

now the system hangs at boot:
[[img]http://a.imagehost.org/t/0527/Screenshot-Ubuntu_no_encrypt_VMware_Player.jpg[/img]](http://a.imagehost.org/view/0527/Screenshot-Ubuntu_no_encrypt_VMware_Player)

There must be something very simple I am missing but I can't see the wood from the trees.  Any help would be greatly appreciated.  Thanks

---

