---
title: "error: sparse file not allowed (Btrfs)"
date: 2013-08-02
forum: Ubuntu, Linux and OS Chat
---

### Post by King Dude on 2013-08-02
When do you guys think this will be fixed? It seems as though the problem has spanned as far back as Ubuntu 9.10.

---

### Post by ssam on 2013-08-03
do you mean this issue?
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/736743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/736743)

---

### Post by ZoiaGuyver on 2013-08-03
Yep think it is the same bug.

It's been around a long time indeed, maybe one day it will get fixed

---

### Post by King Dude on 2013-08-03
> **ssam said:**
> do you mean this issue?
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/736743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/736743)
I believe so. I have a different architecture and Ubuntu version, but yep it's the same problem. I wonder why it still hasn't been fixed.

---

### Post by grahammechanical on 2013-08-03
According to the bug report 1) It is a Grub bug. 2) it is possible to comment out some lines in a Grub configuration file. 3) a patch to the grub configuration file has been put forward so that a new install will detect if root ( / ) is on btrfs and comment out those lines part of the installation process

date: 2013-01-28
> 
Short of implementing btrfs environment-block support for GRUB, we  need a better workaround that doesn't involve manually hacking config  files.

 The scripts in /etc/grub.d/ can determine the type of the root filesystem---we see this in /etc/grub.d/10_linux, assigning to GRUBFS---so there's no reason why the workaround Colin gave in comment 10 cannot be automated.


 I'm attaching a proof-of-concept patch, against /etc/grub.d/00_header  as of Quantal, that conditionalizes inclusion of the grubenv code on  the type of the root filesystem. If "/" is on btrfs, then a warning is  printed, and an alternate bit of code is put into /boot/grub/grub.cfg.



I use btrfs on my main saucy install and also on saucy+mir on Ubuntu and the flavours except Lubuntu which crashes the install if I try to install it on btrfs. This minor issue is no problem for me. And yet some see insignificant bugs like this as a symptom of all they see wrong with Ubuntu. 

The truth is without a snapshot management utility btrfs is not ready for being a Ubuntu default file system. So, btrfs still comes under the heading of "Experimental" as far as I am concerned. New installs are going in on Ext4. The vast number of users will never see this message. Those that do see it should accept that it is the price paid for experimenting.

Regards.

---

### Post by King Dude on 2013-08-04
I reported this bug to the Grub bug tracker. I hope somebody fixes it, finally.
[https://savannah.gnu.org/bugs/?39688](https://savannah.gnu.org/bugs/?39688)

---

### Post by man-walking on 2014-01-04
I'm using and installing 13.10 and this error is clearly related with BTRFS as root/boot file system and usage of "GRUB_DEFAULT=saved" and "GRUB_SAVEDEFAULT=true" in /etc/default/grub.
I can confirm this since appear in several installations I made, and appear ONLY the moment I want set a more flexible dual-boot system (Windows/Linux) with those 2 useful autosaving settings.
BTRFS per se is not the problem (that one always saying the same "sparse file not allowed" was fixed in 12.10 or 13.04), but in conjunction with that grub options it POPS OUT AGAIN.

---

### Post by trivietnam on 2014-02-07
using 12.04.4, same problem here

---

