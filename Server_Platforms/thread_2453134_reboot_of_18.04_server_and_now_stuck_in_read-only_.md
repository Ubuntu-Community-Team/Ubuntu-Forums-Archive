---
title: "reboot of 18.04 server and now stuck in read-only mode"
date: 2020-11-03
forum: Server Platforms
---

### Post by egiblock on 2020-11-03
i've tried everything i could find to recover, but i still need help.   upon booting the server i get a ton of red [COLOR=#ff0000]ERROR [/COLOR][COLOR=#000000]messages on the screen and can get to a login.  but even running things as root, tells me it's read-only and i can't do anything.  I've tried to fix the filesystem with a liveCD, but still nothing.   any ideas ?  ive changed the name to "[/COLOR]server1" here for the posting.[COLOR=#000000]
[/COLOR][COLOR=#ff0000]
[/COLOR]```
root@server1:~$ sudo fsck /dev/sda1fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
fsck.ext2: Permission denied while trying to open /dev/sda1
You must have r/w access to the filesystem or be root

```

```
root@server1:~$ lsblk
NAME                             MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda                                8:0    0  100G  0 disk
&#9492;&#9472;sda1                             8:1    0  100G  0 part
  &#9500;&#9472;server1--vg-root   253:0    0   99G  0 lvm  /
  &#9492;&#9472;server1--vg-swap_1 253:1    0  980M  0 lvm  [SWAP]
sr0                               11:0    1 1024M  0 rom
root@server1:~$

```

```
&#9679; server1
    State: degraded
     Jobs: 1 queued
   Failed: 24 units
    Since: Tue 2020-11-03 11:04:00 MST; 23min ago
   CGroup: /

```

---

### Post by TheFu on 2020-11-03
You installed using LVM.  The fsck has to be done after the LV has been activated.  The easy answer is to boot into rescue mode and in the menu, tell it to run fsck on all file systems.  Hopefully, that will correct any issues.  It is easiest to do this from a Desktop **Try Ubuntu **environment.  The device should be something like **/dev/mapper/server1--vg-root**, but that location gets dynamically created by the mapper tool using the VG and LV names.

If that doesn't work, there are 2 more things to attempt.  One is modifying grub entries - which is hard on a read-only file system. The other is manual and more shell commands than I'd like to type and get wrong. ;)

---

### Post by egiblock on 2020-11-04
> **TheFu said:**
> You installed using LVM.  The fsck has to be done after the LV has been activated.  The easy answer is to boot into rescue mode and in the menu, tell it to run fsck on all file systems.  Hopefully, that will correct any issues.  It is easiest to do this from a Desktop **Try Ubuntu **environment.  The device should be something like **/dev/mapper/server1--vg-root**, but that location gets dynamically created by the mapper tool using the VG and LV names.

If that doesn't work, there are 2 more things to attempt.  One is modifying grub entries - which is hard on a read-only file system. The other is manual and more shell commands than I'd like to type and get wrong. ;)



Recovery Mode (images 1,2,3)
[ATTACH=CONFIG]287314[/ATTACH]

[ATTACH=CONFIG]287313[/ATTACH]

[ATTACH=CONFIG]287312[/ATTACH]

Live mode (image 4)
[ATTACH=CONFIG]287311[/ATTACH]

after reboot of everything (image 5)
[ATTACH=CONFIG]287315[/ATTACH]

---

### Post by TheFu on 2020-11-04
Next I'd guess it is a failing HDD/SSD, but we needed to run an fsck first.  
I'd use smartmontools (smartctl) to check. There are multiple exact commands in these forums about that.  smartmontools is the package. **smartclt** is the program. I'd use the same Try Ubuntu desktop flash drive to run the tests, wait for those to finish, then run the reports. A long test probably takes a few hours for most HDDs and 20 min for an SSD.  The test request command returns in a few seconds, but you need to wait for the test to actually complete before asking for the report.

---

### Post by egiblock on 2020-11-06
actually it's a virtual machine in a vmware cluster.  everything was running fine till i rebooted the server :(

---

### Post by slickymaster on 2020-11-06
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2020-11-06
> **egiblock said:**
> actually it's a virtual machine in a vmware cluster.  everything was running fine till i rebooted the server :(

Then I'd contact VMware support. That's why people pay for that hypervisor - so they can call and get expert help. 
HDDs fail under VMware too.

---

### Post by darkod on 2020-11-06
In the third screenshot you have an advice to check systemctl status and journalctl for more info. Did you do that? Sometimes it can give you a clue what to look at further.

Also, did you try to chroot into the installation? Don't depend only on the rescue process. Use Try Ubuntu, open terminal and try to chroot into the installation. That can help you even to run commands inside your installation.

---

