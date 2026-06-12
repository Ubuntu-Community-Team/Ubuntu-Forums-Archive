---
title: "VirtualBox Ubuntu 11.10 Server - Gave up waiting for root device ..."
date: 2011-10-28
forum: Virtualisation
---

### Post by aslamplr on 2011-10-28
Hello 

I've downloaded ubuntu-11.10-server-amd64.iso 
* Installed on a VirtualBox VDI (8gb)
* It is a minimal installation - OpenSSH server and Ubuntu base server
* I'm getting a busybox (initramfs) shell
* The message is as follows --
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
 - Check rootdelay= (did the system wait long enough?)
 - Check root = (did the system wait for right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda1 does exist. Dropping to a shell!

* Output of `cat /proc/cmdline`
BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-virtual root=/dev/sda1 ro
* Output of `cat /proc/modules`
e1000 108573 0 - Live 0xffffffffa0000000
* ls -l /dev/sda1
No such file or directory
* I tried putting rootdelay=90; Not much of a help !!

Host:
* VirtualBox 4.1.4
* Ubuntu 11.10 (64bit)
* 3.7 GB, Intel core i5 
Guest:
* 8.0 GB VDI
* VT-x Enabled
* Nested paging Enabled
* Execution Cap 85%

I'm ready to give more information to get it resolved. 
Or may be I'm wrong that this setup may not work. 

Please provide suggestions.

---

### Post by aslamplr on 2011-10-28
:popcorn:

Resloved !! Previously I was using a SATA Controller to add the VDI

Changed to a SCSI Controller. It worked... Now I'm in

Byobu is really cool tool...

---

