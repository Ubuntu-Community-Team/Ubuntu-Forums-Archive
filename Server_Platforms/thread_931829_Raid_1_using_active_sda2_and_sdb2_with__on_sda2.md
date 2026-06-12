---
title: "Raid 1 using active sda2 and sdb2 with / on sda2"
date: 2008-09-27
forum: Server Platforms
---

### Post by xefialtis on 2008-09-27
I know I am asking a lot, but I want to make my ROOT system RAID1.

I have 2 identical drives with identical partitioning schemata...

I have /boot on sda1 
/ on sda2
swap on sdb1
"nothing" on sdb2

I want to take sda2 and sdb2 and make them RAID 1

I tried MDADM --create /dev/md0 -l1 -n2 /dev/sda2 /dev/sdb2
It gives me an error that the resource is busy.

Can I do this with an active ROOT partition on one of the disks?

Then, after I get the raid completed, I will have to change the mount point for / from /dev/sda2 to /dev/md0

Where can I do this?

---

### Post by fjgaude on 2008-09-27
You likely have to have the two drives unmounted to create the md0. You might be able to do it from a liveCD, install mdadm, and then do the --create.

---

### Post by xefialtis on 2008-09-28
normally, I would just set this up during install...
There WAS a selection to use a device as a RAID device...after you selected that for the number of devices you wanted to RAID, you would get the option to create a raid, set the level, select the devices, set the mount points, and install Ubuntu.
HOWEVER, (and maybe I need to go back to 7.10 for this) it seems that this option is no longer available? (in Hardy?)
Or do I have to use the SERVER version instead of the Desktop version?
Which begs the question, WHY isn't it available for the Desktop version?

Anyway, I was able to get it to MDADM and force an array in Live CD, only, with a reboot you loose the MDADM.conf file, and a new install process does not recognize the array...

So, I will try Gutsy, see if it works, then I will try the server version, and install the desktop...

But really, this shouldn't be so hard. People like to run RAID when they want a secure and safe environment to run in...

---

### Post by fjgaude on 2008-09-28
Well, all I can say is I've had to learn what to do and not do as I've learned really how to use **mdadm**, a powerful software raid utility.

I'd be the first to admit that it should be easier to master, and that many just jump in and gets themselves into trouble.

The oldline program, **webmin**, handles **md** raid pretty well, and gets better all the time. You might wish to look into it for server useage.

---

### Post by xefialtis on 2008-09-29
I tried earlier versions of Ubuntu, they failed miserably...

What is it about Raid that the partitioning tool (whatever it is that Ubuntu uses during install) that doesn't like Raid...???

I ended up installing Ubuntu Server, the partitioning tool worked just fine. Then I had to install the GUI (xorg core, ubuntu-desktop, etc) and now it is running just fine with sda1 = /boot, sdb1 = swap, sda2&sdb2 = md0 = /(root)...

It doesn't need to be that hard....Ubuntu needs a better partitioning tool for install (even gparted found the raid array)

---

### Post by fjgaude on 2008-09-29
All I can say is "file a bug report"... 

Glad to see you got your setup working as you wanted.

---

