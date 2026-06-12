---
title: "Ubuntu Server Boot Failed after update to 12.04"
date: 2012-05-27
forum: Server Platforms
---

### Post by boardmain on 2012-05-27
After an update to ubuntu 12.04  the server started to have problem, the boot fail to reboot
i can access to it with rescue account

im in this situazion now

i tryed to mount again it , i do this command.

mount /dev/hda3 /mnt
 mount --bind /dev /mnt/dev/   
mount --bind /sys /mnt/sys/
mount --bind /proc /mnt/proc/
chroot /mnt /bin/bash

if i do Mount Command i see

/dev/sda3 on / type ext4 (rw,errors=remount-ro,usrjquota=quota.user,grpjquota=quota.group,jqfmt=vfsv0)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/hda2 on /boot type ext3 (rw)


why i mounted hda3 and now i see sda3???
and boot is in another partition if i look in /boot/ there is only grub dir..
after umount and mount again of /dev/hda2 to /boot i see all kernel files...

i tryed to reinstall grub to /dev/hda but after reboot same problem.. unable to start the server.. :(
please help me

---

### Post by darkod on 2012-05-27
Ubuntu calls the disks with S not with H, so it's /dev/sda.

Did you try to reinstall grub2 with /boot mounted or not? When you have separate /boot partition it needs to be mounted too.

---

### Post by boardmain on 2012-05-27
Yes i tried with this command

grub-install /dev/hda
update-grub2


but after a reboot notting

how i can check what don't work?
i need to startup again this server

---

### Post by boardmain on 2012-05-27
i tried to reinstall grub

i have strage fdisk

root@rescue:/boot# fdisk -l

Disk /dev/hda: 85.9 GB, 85899345920 bytes
255 heads, 63 sectors/track, 10443 cylinders, total 167772160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00098c17

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1            2048     4194303     2096128   82  Linux swap / Solaris
/dev/hda2         4194304     5242879      524288   83  Linux
/dev/hda3         5242880   167771910    81264515+  82  Linux swap / Solaris



why hda3 is linux swap? hda1 is swap, hda2 is boot and hda3 is the root

---

### Post by darkod on 2012-05-27
I don't know man, that's what fdisk says. You can tyr running an ubuntu desktop cd in live mode, downloading testdisk and doing the deep search to see if it can recover the partition as Linux.

---

### Post by LHammonds on 2012-05-27
Do you have a backup you can restore to?

I had a similar problem with grub after an in-place upgrade from 10.04 LTS to 12.04 LTS.  I had my config files backed up so I simply started over with a fresh install of 12.04 and I am putting Nagios back on right now.

I had two other almost identical (virtual) servers that upgraded without a problem.  I am not sure why it failed but I was taking too long troubleshooting the problem and needed to restore or rebuild.  I chose to rebuild.

LHammonds

---

