---
title: "Ubuntu server 16.04 LTS"
date: 2016-10-12
forum: Server Platforms
---

### Post by bernard14 on 2016-10-12
Hello,
I'm having an issue with setting up RAID 1 in ubuntu 16.04 server edition.
During installation I tried every possible configuration with partitions(LVM,noLVM, md0(boot) md1(root) md2(swap),..) and raid setups, no errors reported, worked like on the previous editions.

I can boot up the server just fine and everything works OK, I installed grub on the other disk drive, 
but when I plug any of the two drives, the system won't boot, it throws me in to busybox.

I installed 14.04 version with the same partition setup and works as it should if I pull out any of the hard drives.

I came across this problem when I started to build my new file storage on an old lenovo D20 thinkstation, I thought it had a faulty hardware so 
I tried everything on a VM machine, with same results.

I read some posts about the same issue, but non of them seems to work.

Does anyone have any ideas?

---

### Post by Vegan on 2016-10-12
raid is passe use JBOD and use a backup server for addition redundancy

---

### Post by QIII on 2016-10-12
Please stay on topic.  The OP asked about RAID.  Do not assume he/she has another server available for backup.

---

### Post by volkswagner on 2016-10-12
You'll want /boot on md0 without LVM.
You can reinstall grub to md0 to make sure both disks get boot loader installed.

What is the output of:
```
cat /boot/grub/grub.cfg | grep 'root='
```

---

### Post by bernard14 on 2016-10-18
cat /boot/grub/grub.cfg | grep 'root='
set root='mduuid/8ac92660462131262165003bdc087086'
        set root='mduuid/60bcaade88bc9dbf26532d4d0eeea863'
        linux   /vmlinuz-4.4.0-42-generic root=UUID=73645912-eece-4dae-bb4b-64ef6485c5f4 ro  quiet splash $vt_handoff
                set root='mduuid/60bcaade88bc9dbf26532d4d0eeea863'
                linux   /vmlinuz-4.4.0-42-generic root=UUID=73645912-eece-4dae-bb4b-64ef6485c5f4 ro  quiet splash $vt_handoff
                set root='mduuid/60bcaade88bc9dbf26532d4d0eeea863'
                linux   /vmlinuz-4.4.0-42-generic root=UUID=73645912-eece-4dae-bb4b-64ef6485c5f4 ro recovery nomodeset



And fstab

 cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/md1 during installation
UUID=73645912-eece-4dae-bb4b-64ef6485c5f4 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/md0 during installation
UUID=cfd48db9-9cde-4563-8521-9c7beb3633f6 /boot           ext4    defaults        0       2
# swap was on /dev/md2 during installation
UUID=2bca13fa-5ca2-4552-b934-ad4d684dcb45 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

