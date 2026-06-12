---
title: "can't mount any ntfs device after 16.4.2"
date: 2017-03-26
forum: Windows
---

### Post by spystrach on 2017-03-26
Hello
I have a Dual Boot Window 10 and Ubuntu 14.04 and it worked fine
yesterday i decided to upgrade to 16.04 using "sudo do-release-upgrade". Since that, Grub did not detect window 10 :(

I dit a little digging and figured that ubuntu can't mount any ntfs devices : my external drive and my window 10 partition, saying
"Error mounting system-managed device /dev/sdb1: Command-line `mount "/media/tux"' exited with non-zero exit status 21: mount: according to mtab, /dev/sdb1 is already mounted on /media/tux"
Also, os-prober failed
(sdb1 is my external drive, i don't want to delete my sda1 sda2 sda3 windows partitions)

I add the correct line in /etc/fstab in order to mount my external harddrive "UUID=C25437C25437B7CD /media/tux    ntfs-3g    defaults,windows_names,locale=fr_FR.UTF-8   0   0"
but when i try to mount using "mount -a" it write "mount: according to mtab, /dev/sdb1 is already mounted on media/tux"
BUT when i try "umount /dev/sdb1" I get "umount: /dev/sdb1: not mounted"

This situation drives me mad, i really want to recover my dual boot without losing all my data

---

### Post by spystrach on 2017-03-28
Ok after a lot of testing i managed to recover my computer !!

- the problem with mounting ntfs device was solve by re-installing ntfs-3g with the command "sudo apt-get install ntfs-3g"

- GRUB did not see my windows10 partition : i created a live-USB ubuntu 14.04 and boot on it (select "try"). I delete the linux partition /dev/sda6 and the linux swap /dev/sda5 and also a logical partition /dev/sda4
i reboot on the live-usb and select "install" then "ubuntu alongside with windows" and it's done !!

i hope this will help somebody in the future

---

