---
title: "Upgrade, reformat or change everything, PLEASE HELP ME"
date: 2009-05-01
forum: Server Platforms
---

### Post by rgotten on 2009-05-01
Last year i started my server with the following configuration:
I am installing the boot on Raid 1 128mb, Swap on Raid 1 (2gb), the root on raid 5 (10 gb) and the rest for home on Raid 5 ( aprox. 960 gb).
Today when trying to upgrade a message came and said there was not enough space on the boot area. After reading on the Internet I saw an option of resizing the raid partition. First I shrink the raid 5 for home from 960 gb to 900, then I try to increase the boot from 128mb to 1 gb and I still got a message of, not enough space. Looking into my configuration I realized that the boot is on a primary partition, and the rest of the raids( swap,root and home at each one created on an extended partition)

this are my question:
1) Is there a way to resize raid one were i have the boot, or this is impossible since is a primary partition
2) If i can not resize, and i have to reformat everything how should i do this to avoid this problem in the future?
3) What is better to have evertyhing like this with 4 different raids and give 500 mb to the boot, or is better to place on top of the raid a LVM

Thanks for your help

rgotten

---

### Post by konsole on 2009-05-12
> **rgotten said:**
> Last year i started my server with the following configuration:
I am installing the boot on Raid 1 128mb, Swap on Raid 1 (2gb), the root on raid 5 (10 gb) and the rest for home on Raid 5 ( aprox. 960 gb).
Today when trying to upgrade a message came and said there was not enough space on the boot area. After reading on the Internet I saw an option of resizing the raid partition. First I shrink the raid 5 for home from 960 gb to 900, then I try to increase the boot from 128mb to 1 gb and I still got a message of, not enough space. Looking into my configuration I realized that the boot is on a primary partition, and the rest of the raids( swap,root and home at each one created on an extended partition)

this are my question:
1) Is there a way to resize raid one were i have the boot, or this is impossible since is a primary partition
2) If i can not resize, and i have to reformat everything how should i do this to avoid this problem in the future?
3) What is better to have evertyhing like this with 4 different raids and give 500 mb to the boot, or is better to place on top of the raid a LVM

Thanks for your help

rgotten

Investigate what's filled up your /boot partition. 128 MB is more than ample.

---

### Post by rgotten on 2009-05-12
Thanks for your reply. Since I am new with Ubuntu, How can i check that and see what can i delete..

This is what i see on that folder:

abi-2.6.24-16-server             initrd.img-2.6.24-21-server
abi-2.6.24-18-server             initrd.img-2.6.24-21-server.bak
abi-2.6.24-19-server             initrd.img-2.6.24-23-server
abi-2.6.24-21-server             initrd.img-2.6.24-23-server.bak
abi-2.6.24-23-server             lost+found
config-2.6.24-16-server          memtest86+.bin
config-2.6.24-18-server          System.map-2.6.24-16-server
config-2.6.24-19-server          System.map-2.6.24-18-server
config-2.6.24-21-server          System.map-2.6.24-19-server
config-2.6.24-23-server          System.map-2.6.24-21-server
grub                             System.map-2.6.24-23-server
initrd.img-2.6.24-16-server      vmlinuz-2.6.24-16-server
initrd.img-2.6.24-16-server.bak  vmlinuz-2.6.24-18-server
initrd.img-2.6.24-18-server      vmlinuz-2.6.24-19-server
initrd.img-2.6.24-18-server.bak  vmlinuz-2.6.24-21-server
initrd.img-2.6.24-19-server      vmlinuz-2.6.24-23-server
initrd.img-2.6.24-19-server.bak

What can i delete and how can i delete it?



Thanks in advance

rgotten

---

### Post by a9k3d on 2009-05-12
You have 5 versions of linux installed.
vmlinuz-2.6.24-16-server
vmlinuz-2.6.24-18-server
vmlinuz-2.6.24-19-server
vmlinuz-2.6.24-21-server
vmlinuz-2.6.24-23-server
The simplest way to remove some is probably in a terminal. Run sudo aptitude
Once you're in aptitude, type slash (/) and it will popup a search box.
Type: linux-image
That will get you close to where you need to be.
Use the arrow keys to move up and down to an linux-image you'd like to remove, hit minus (-) or underscore (_). Underscore gets rid of all files associated with the selected item including configurations, so it frees more space.
Repeat 2 more times. Probably you'll want to get rid of linux-image-2.6.24-16-server, 18 and 19. Make sure you leave a linux-image you know works (like what ever you booted with).
Once you have selected for deletion some of the images (they will be purple if you have color), then hit g for GO. Follow the prompts. When your done, hit q to QUIT.
You should now have more free space on /boot

---

### Post by rgotten on 2009-05-13
Ok, thanks for the last reply, i did the aptitude and this is what I got:

linux-image-2.6.24.16-server    2.6.24-16. 2.6.24-16
linux-image-2.6.24.18-server    2.6.24-18. 2.6.24-18
linux-image-2.6.24.19-server    2.6.24-19. 2.6.24-19
linux-image-2.6.24.21-server    2.6.24-21. 2.6.24-21
linux-image-2.6.24.23-server    2.6.24-16. 2.6.24-23
linux-ubuntu-modules-2.6.24-16-server   2.6.24-16. 2.6.24-16
linux-ubuntu-modules-2.6.24-18-server   2.6.24-18. 2.6.24-18
linux-ubuntu-modules-2.6.24-19-server   2.6.24-16. 2.6.24-19
linux-ubuntu-modules-2.6.24-21-server   2.6.24-16. 2.6.24-21
linux-ubuntu-modules-2.6.24-23-server   2.6.24-16. 2.6.24-23

Before i erase any of them, how can i know which is the one being use at the present moment? I agree that probably is the last ones, but since i am new to ubuntu i would like to be sure

Thanks

rgotten

---

### Post by cariboo on 2009-05-13
Try uname -a, it will tell you what kernel version you are running.

---

### Post by rgotten on 2009-05-14
Thanks to everybody, i recover about 90 mb

---

