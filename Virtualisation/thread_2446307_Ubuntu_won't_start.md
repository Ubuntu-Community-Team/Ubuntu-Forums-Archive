---
title: "Ubuntu won't start"
date: 2020-06-28
forum: Virtualisation
---

### Post by daanleiden on 2020-06-28
A friend of mine installed Windows on my computer and put Ubuntu in a VMware Workstation. For a half year it worked okay, with problems that grew worse throughout the months. And now it won't start anymore. I got some data on Ubuntu that i want to recover. This friend of mine is very busy, so he can't help. He said i had to try safe mode. I used shift and escape but it didn't work. This is the error log at the end:

[      3.235583] piix4_smbus 0000:00:07.3: SMBus Host Controller not enabled!
[      3.787433] sd 32:0:0:0: [sda] Assuming drive cache: write through
/dev/sda1 contains a file system with errors, check forced.
/dev/sda1:
Inodes that were part of a corrupted orphan linked list found.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
            (i.e., without -a or -p options)
fsck exited with status code 4
The root filesystem on /dev/sda1 requires a manual fsck

BusyBox v1.27.2 (Ubuntu 1:1.27.2-2ubuntu3.2) built-in shell (ash)
Enter 'help'for a list of built-in commands.

(initramfs)

---

### Post by ajgreeny on 2020-06-28
I don't  know  vmware  but if it is similar to virtualbox you probably need to insert a live Linux iso image into the virtual system, boot from that and run the fsck from that live system. 

Wait for others who know VMware before you  do anything drastic. It certainly should be possible to retrieve any data from that vmware installation.

---

### Post by ajgreeny on 2020-06-28
Moved to Virtualisation for a better fit.

---

### Post by daanleiden on 2020-06-28
Sure, i will wait. Thanks for the reply!

---

### Post by uninvolved on 2020-06-30
What you can do is download the current Ubuntu ISO, mount that in VirtualBox, boot, press F12, select the CD/DVD option, load the Live Ubuntu instance, and recover your data. You may want to make a shared folder and then move the data to that folder. It's effectively the same as it would be doing it on bare-metal, except you're doing it in VirtualBox.

This way you can recover your data. Then you can worry about getting the VM working again.

---

### Post by daanleiden on 2020-07-03
Thanks, i already gathered my data from other sources. On sunday i hoped i wouldn't have to spend hours on it.

---

