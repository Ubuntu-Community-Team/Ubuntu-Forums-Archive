---
title: "Grub fails to install during install"
date: 2008-11-23
forum: Server Platforms
---

### Post by vocoder42 on 2008-11-23
I have 5 1TB drives connected to a PCI RAID card.  I'm trying to install Ubuntu Server 8.04 onto this server, yet when going through the setup process, it fails when trying to install grub (red screen displayed).

If I boot into rescue mode, then try to install grub from the shel using grub-install, it comes back with 

"The file /boot/grub/stage1 not read correctly"

and if I try to run "find /boot/grub/stage1" it has that same message.

If I try to reboot the server without the CD, it says "Operating System Not Found"  I have tried uninstalling grub and installing lilo, but the same thing happens regarding "operating system not found"

when using the rescue mode and going into shell, fdisk -l correctly shows the drive partition.  

Any idea what is going on here?

---

### Post by caljohnsmith on 2008-11-23
How about first posting the output of:
```
sudo fdisk -l
```
So we can get a clearer picture of your setup as seen by Ubuntu.

---

### Post by vocoder42 on 2008-11-24
I don't have the server in front of me atm, but when I do that, it shows /dev/sda1 and shows it having 4TB, which is correct

---

### Post by vocoder42 on 2008-11-24
could the problem be that the disk is showing up as 4TB? I read 1 page that said grub doesn't support disks larger than 2TB ...so grub-pc must be used.  How do I go about installing grub-pc instead of grub during install?

---

