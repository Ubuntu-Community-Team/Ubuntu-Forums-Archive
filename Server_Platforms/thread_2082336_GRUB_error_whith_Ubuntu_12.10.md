---
title: "GRUB error whith Ubuntu 12.10"
date: 2012-11-09
forum: Server Platforms
---

### Post by MitsuTomoe on 2012-11-09
Hello, 
I tried to update a server from 12.04 to 12.10 and had an error with GRUB update.
> Paramétrage de grub-pc (2.00-7ubuntu11) ...
Installation finished. No error reported.
/usr/sbin/grub-bios-setup: warning: File system `ext2' doesn't support embedding.
/usr/sbin/grub-bios-setup: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.
Generating grub.cfg ...
/etc/grub.d/06_OVHkernel: line 6: /usr/lib/grub/update-grub_lib: No such file or directory
dpkg: erreur de traitement de grub-pc (--configure)*:
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 1


My disks :

> cat /etc/fstab
# <file system>	<mount point>	<type>	<options>	<dump>	<pass>
proc	/proc	proc	defaults	0	0
/dev/sda1	/	ext4	errors=remount-ro,relatime	0	1
/dev/sda2	/home	ext4	defaults,relatime	1	2
/dev/sda3	swap	swap	defaults	0	0
sysfs	/sys	sysfs	defaults	0	0
dev	/dev	devtmpfs	rw	0	0

Volumes :
 > *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: ca91b4d0-086b-4000-8634-f590e48524ac
                   size: 9999MiB
                   capacity: 9999MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-06-20 04:08:05 filesystem=ext4 lastmountpoint=/ modified=2012-06-20 04:10:25 mounted=2012-10-20 22:01:31 state=clean
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /home
                   version: 1.0
                   serial: 58cff4c2-ad19-47f5-af52-ebec61f552a6
                   size: 921GiB
                   capacity: 921GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-06-20 04:08:08 filesystem=ext4 lastmountpoint=/home modified=2012-10-20 22:01:32 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,acl,barrier=1,data=ordered mounted=2012-10
-20 22:01:32 state=mounted
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: 7cff4150-60d7-4fe8-89d9-0123d186e8a8
                   size: 511MiB
                   capacity: 511MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
Of course, I've got this error whenever I try apt-get dist-upgrade .
After some googling, I understand GRUB 2 is trying to replace an older version, but I couldn't find a solution. Any help would be appreciated.

---

### Post by darkod on 2012-11-09
You might have had grub2 installed on a partition. In general, that's not recommended so it complains if it needs to reinstall it on a partition.

In any case, if the upgrade finished OK and only the grub2 upgrade failed, I would chroot into the installation (if you can't boot it right now), remove/purge grub-pc and reinstall it again. Also making sure to install grub to the MBR of the disk which is /dev/sda.

---

### Post by MitsuTomoe on 2012-11-09
Thank you for your reply, but my knowledge of Ubuntu is very limited.
As for now, server is up and running. I guess rebooting would be a bad idea right now.
What is the safest way to uninstall GRUB ? Playing with a bootloader makes me anxious.
I've got backups, so I could reformat and reinstall from scratch, but I'd prefer to avoid that.

---

### Post by MitsuTomoe on 2012-11-09
After further searching, I think you mean something like this :

> mount /dev/sda3 /mnt
chroot /mnt
install-grub /dev/sda
update-grub

Problem is I didn't find how to remove grub before install ???

---

### Post by darkod on 2012-11-09
Of course, I am anxious too when it comes to playing with the bootloader.

But since your system is working right now, removing grub2 and installing it again should be very easy and safe. You don't need to use chroot, no mounting, nothing. That's only for when you can't boot the system so you have to work from live mode from the cd.

From within a working system, you can do:
```
sudo apt-get remove --purge grub-pc grub-common grub (to remove the packages and config files)
sudo apt-get install grub-pc (it installs all needed files)
sudo grub-mkconfig (create new config files)
sudo update-grub (usually there is nothing to update but run it anyway)
sudo grub-install /dev/sda (to install the new version on the MBR)
```

That should do it.

---

### Post by MitsuTomoe on 2012-11-13
I tried the updates . After that, apt-get update did not find any error. Problem was I couldn't reboot.
I access the server only by ssh, and even an electrical shutdown with the ISP console did not solve the problem. So I reformatted the disk and reinstalled my backup.
After a few hiccups, all is fine now.
Thank you for your help

Alex

---

