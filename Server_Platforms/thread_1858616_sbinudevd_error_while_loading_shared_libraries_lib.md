---
title: "/sbin/udevd: error while loading shared libraries: libselinux.so.1"
date: 2011-10-12
forum: Server Platforms
---

### Post by catscratch on 2011-10-12
Hi - I have Ubuntu 10.04.3 LTS Server and when I last did:

apt-get dist-upgrade

It all appears to install fine but when I restart the machine I get:

/sbin/udevd: error while loading shared libraries: libselinux.so.1: cannot open shared object file: No such file or directory
wait-for-root: error while loading shared libraries: libudev.so.0: cannot open shared object file: No such file or directory
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/5bee485a-xxxx-xxxx-xxxx-xxxxxxxxxxxx does not exist. Dropping to a shell!

BusyBox v1.13 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initframfs)

Without the kernel upgrade, the apt-get upgrade works fine, but when did dist-upgrade and was upgrading from 2.6.32-33-server kernel to 2.6.32-34-server kernel - this is when I saw the error above upon reboot. There is a /lib/libselinux.so.1 file on the system and also a /lib/libudev.so.0

I googled around quite a bit but could not find this exact error. 

I tried reverting back to my backup image (using Clonezilla) and just for fun I installed selinux (which was not installed) since it seemed to want that and then disabled it, but I still get that error every time. How do I remove selinux and the its associate libraries? Or does anyone have any other suggestions as to how to get past this?

Why does the kernel update hose my system?

---

