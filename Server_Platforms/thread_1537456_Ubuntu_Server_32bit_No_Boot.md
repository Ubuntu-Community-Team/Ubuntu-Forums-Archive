---
title: "Ubuntu Server 32bit No Boot"
date: 2010-07-23
forum: Server Platforms
---

### Post by hkothari on 2010-07-23
So I just installed Ubuntu Server 32 bit on my 2 hard drive system, each drive is 160Gb, partitioned like this:
/dev/sda1 ext4 /
/dev/sda5 swap
/dev/sdb1 ext4 /home

I installed grub on /dev/sda with the server installer, but when I booted, I got nothing, just a blank screen with a blinking cursor on the top, no bootloader, nothing.

I tried to use the install cd to rescue the system, tried installing the bootloader on /dev/sdb, still nothing. Any ideas?

---

### Post by bobica257 on 2010-07-26
Hi, I have exact same problem so i appriciate help. I am also using 32-bit version. 
Help...I tried to treinstall grub but it is alwas the same thing.
Thanks

---

### Post by mr clark25 on 2010-07-26
you might have grub installed, it just likes to be quiet during boot. see if you can bring up the grub menu by holding SHIFT during boot.

if not, i would chroot into your system and re-install grub with a live cd. (i think the "fix-grub" option you mention does this)

---

### Post by bobica257 on 2010-07-27
Here i finely solved the problem. You need to reinstall ubuntu with no modeset selected and everything will work fine.

---

