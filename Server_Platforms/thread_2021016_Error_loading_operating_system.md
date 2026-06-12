---
title: "Error loading operating system"
date: 2012-07-08
forum: Server Platforms
---

### Post by razor7 on 2012-07-08
Hi, a client needs an IBM System x3100 M4 loaded with Ubuntu Server 12.04 LTS.

I followed the simple installation steps from the installation CD with no hassle!, but when trying to boot the Server, I keep getting this awful message "Error loading operating system" and no more options are displayes!

Is there any guide to install Ubuntu Server in this entry level Server platform?

The server have onle 4GB RAM and one 1TB WD Green HDD.

Thanks a lot in advise!

---

### Post by violinuxer on 2012-07-08
Did the computer previously have windows? If so, you might have an issue with the GRUB bootloader. This link seems to be something similar:

[http://ubuntuforums.org/showthread.php?t=1397248](http://ubuntuforums.org/showthread.php?t=1397248)

Good Luck!

violinuxer

---

### Post by razor7 on 2012-07-08
Great! for some reason GRUB2 didn't got installed! Ran this command from liveCD and everything went OK.

> sudo fdisk -l

> sudo mount /dev/sda1 /mnt

> sudo grub-install --root-directory=/mnt/ /dev/sda

---

### Post by violinuxer on 2012-07-09
Glad it worked! :D

violinuxer

P.S. You might want to mark this as being solved :)

---

