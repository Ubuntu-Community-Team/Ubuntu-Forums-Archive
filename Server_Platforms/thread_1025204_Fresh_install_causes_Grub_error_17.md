---
title: "Fresh install causes Grub error 17"
date: 2008-12-29
forum: Server Platforms
---

### Post by borahshadow on 2008-12-29
Hi, I just took my home file server off line to upgrand it from dapper to hardy. I installed Hardy and rebooted only to get a grub Error 17: Cannot mount selected partition 
Press any key to continue..._

Pressing any key just brings me back to the grub menu.
I reinstalled and made sure that the bootable flag was set on the right drive and  partition and not on something like swap. However I got the same problem.

Help please the server is down so it is kinda urgent.

---

### Post by caljohnsmith on 2008-12-29
How about when you get the Grub menu on start up, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Most likely that should work, but if not, try X=1,2,... Note that the change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "# groot=(hdX,Y)" to use the (hdX,Y) that worked to boot Ubuntu. Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems.

---

### Post by borahshadow on 2008-12-29
Ok more time for some more detail.
The OS drive is a 6GB hard drive IDE.
There are 2 250GB drives used for swap and raid SATA with pci SATA card.
The os drive showed up in the partitioner as SCSI3 and the 2 250s were above it as 1 and 2

That GRUB line shows (hd2,0) currently
If I change it I get grub error 21 drive does not exist or something like that.

---

### Post by caljohnsmith on 2008-12-29
OK, how about when you get the Grub menu, press "c" to get the command line, and then do:
```
grub> find /boot/grub/stage2
grub> find /grub/stage2
```
One of those commands should return your server partition or your /boot partition if you have one in the form of (hdX,Y). Use that answer to modify your Ubuntu entry in the Grub menu as per the previous directions. Let me know if that works or not.

---

### Post by borahshadow on 2008-12-29
ok thanks that worked.
It returned 0,0 and that allowed me to boot but I hope it didn't touch my raid drives as it was not supposed to.

EDIT: Ok it didn't touch my raid drives but apparently grub doesn't see my sata drives and therefore the 3rd drive is actually the first to grub.

---

