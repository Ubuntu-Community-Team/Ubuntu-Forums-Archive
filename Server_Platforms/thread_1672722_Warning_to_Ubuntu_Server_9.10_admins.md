---
title: "Warning to Ubuntu Server 9.10 admins"
date: 2011-01-21
forum: Server Platforms
---

### Post by Jan82 on 2011-01-21
Feel free to post this to lauchpad or where ever you post bugs in the ubuntu community. I don't have time for that. This happened last year also with the network commands to. 

__
Date: 20 jan 2011

Platform: Ubuntu 9.10 Karmic Koala i686

Problem: Latest system updates break server ability to boot. Updates place core files needed to boot on Ubuntu server with wrong file permissions. That is, no file permissions at all. 

Packages responsible for the problems:
util-linux 2.16-1ubuntu5.1: after update fsck got perm 000.
mount 2.16-1ubuntu5.1: after update mount, swapon, swapoff and umount got perm 000

There where one or two more files with incorrect file permissions after these updates, but these I mentioned here will make your server impossible to boot if the permissions are 000.

My repos are nl.archive.ubuntu.com and security.ubuntu.com

Fix if you rebooted after these updates:

The only way to fix this is by booting into a rescue environment. In single user mode over the console you can't do anything with mount on 000. 

After you patched your system take a look at the patched files before you reboot your Ubuntu server 9.10 i686.

---

