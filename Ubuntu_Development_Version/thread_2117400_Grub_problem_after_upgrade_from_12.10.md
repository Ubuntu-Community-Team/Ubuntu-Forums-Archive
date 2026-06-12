---
title: "Grub problem after upgrade from 12.10"
date: 2013-02-18
forum: Ubuntu Development Version
---

### Post by P-I H on 2013-02-18
I got tired of waiting for a fix on this bug
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701)

I had two 120GB SSDs on my main system. Sdb with 12.10 and an empty sda. I copied my 12.10 version on sdb to sda with sudo dd. Started the copied 12.10 system on sda and made sudo do-release-upgrade -d.
The upgrade worked fine and was done in about 1 hour. After the upgrade, 13.04 is on sda and 12.10 is on sdb.

When I boot from sda, the boot options in the Grub menu behaves very strange
- menu item Ubuntu starts 12.10 on sdb, without panel and launcher. Expected is 13.04 with the 3.8.0-6 kernel
- menu item Ubuntu 12.10, starts Ubuntu 13.04 on sda with the 3.5.0-23 kernel. Expected is Ubuntu 12.10 on sdb with kernel 3.5.0-23
- menu item Advanced options for Ubuntu and Ubuntu 13.04 kernel 3.8.0-6 starts sometimes as expected, but sometimes with 12.10.

I made update-grub, but that didn't change anything.

Boot from sdb is also strange. In this case there is only one alternative in Grub. Expected is of course start of Ubuntu 12.10. However either 13.04 on sda or 12.10 on sdb starts. I have not managed to figure out when 13.04 or 12.10 starts. I do not dare to do sudo update-grub.

When I disconnect sdb, boot time is longer than normal, but I get the expected result from Grub
-menu item Ubuntu starts 13.04 with kernel 3.8.0-6

---

### Post by dino99 on 2013-02-18
its time to clean the room  :)
copying may have done crossed links.

if you want 13.04 having the master grub, then boot on it (taking care of the actual fake menu), then:

- sudo dpkg-reconfigure grub-pc
- uncheck all the partitions and validate that choice : grub fully purged

- sudo apt-get install grub-pc grub-common
-sudo update-grub

-sudo reboot

---

### Post by oldfred on 2013-02-18
When you used dd you copied internal structures also, so UUIDs are the same on both drives. Depending on which drive comes up first all references to UUID may be one drive or the other. 

You either need a full new install with reformatting of partitions to reset UUIDs or manually change UUIDs and edit fstab with correct entires & reinstall grub.

Post this in code tags to preserve formatting:

       # To clear cache and get new view:
sudo blkid -c /dev/null -o list

---

### Post by P-I H on 2013-02-18
OK, I should have thought about that.
The disks have the same UUID

```
p-i@pi-GA-990FXA-UD3-1210:~$ sudo blkid -c /dev/null -o list
[sudo] password for p-i: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              5f40b6d1-e096-42d0-a68f-9c15b7f5978a
/dev/sdb1  ext4             (not mounted)  5f40b6d1-e096-42d0-a68f-9c15b7f5978a
p-i@pi-GA-990FXA-UD3-1210:~$ 

```

A new installation will not work according to this bug
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701)

I suppose I have to have only one disk connected, depending on the system I want. It realy doesn't matter as all my data is on a server.
For now I will switch to 13.04 as the applications I am using seems to work fine.

---

### Post by oldfred on 2013-02-18
You can change UUID.

       Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid

    
But you then have to update fstab with new UUID and reinstall grub. You can edit grub.cfg (one line's UUID) just to boot once and then from inside your install update grub.

---

