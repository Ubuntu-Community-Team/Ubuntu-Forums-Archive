---
title: "cryptsetup and swap"
date: 2010-06-05
forum: Security
---

### Post by spy_1134 on 2010-06-05
I'm currently working on getting and old laptop to load up two encrypted partitions at boot.

The partitions:
/dev/sda1 /boot (not encrypted)
/dev/sda2 /
/dev/sda3 swap

When the system starts up, it asks me for a password and then proceeds to unlock my root partition. After loading for a little while it attempts to unlock my swap partition. I am getting an error saying that my keyfile wasn't found. The filesystem that the keyfile is on was already mounted. (The keyfile is located in /root/ in sda2)

/etc/crypttab:
sda2crypt UUID=24699caa-0443-4b88-9b19-96dcefe74650 none luks,tries=3,check=vol_id
sda3crypt UUID=b9b70edf-8023-4a73-bb0f-a34555c8009b sda3crypt swap,/root/swapkey

/etc/fstab:
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/mapper/sda2crypt during installation
/dev/mapper/sda2crypt /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
/dev/sda1 /boot           ext4    relatime        0       2
# swap was on /dev/mapper/sda3crypt during installation
/dev/mapper/sda3crypt none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


[LIST]
[*]I have already checked the swap partition's UUID and it is correct in /etc/crypttab.
[*]I added / to /etc/default/cryptdisks: (CRYPTDISKS_MOUNT="/") - This didn't work.
[/LIST]
All help is appreciated! Thanks in advance.[INDENT]- spy_1134
[/INDENT]

---

### Post by spy_1134 on 2010-06-11
I could seriously use some help.

If I can't get this to work I will have to reinstall using a custom lvm. I don't want to have to backup and then restore all of my config files, etc.

---

### Post by spy_1134 on 2010-06-11
SOLVED!

I was putting the path to my keyfile in the wrong location in /etc/crypttab
The proper line was:
sda3crypt UUID=<disk uuid> <keyfile> <options>

---

