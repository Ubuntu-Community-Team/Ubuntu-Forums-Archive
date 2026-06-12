---
title: "New sysadmin"
date: 2007-10-03
forum: Server Platforms
---

### Post by benne on 2007-10-03
Hi there!

I have just started working as a sysadmin and according to co-workers and boss doing great (a little bragging ;) ). 

I work in a primarily Windows enviroment but there are a couple of Linux machines and they are getting more and more. I have a few questions id like to ask, both for my personal server and the work. 

I use ubuntu mostly. I used to use gentoo but i like ubuntu better nowdays. 

My own server has 2 discs now. One for / and anotherone is running /home. I want to add one disc for user data, a larger one. /home is a scsi disk on 20 gb or so but i have a IDE disc on 120gb i would like to add. I just cant figure out a smart way to do it.. mounting it as /media/storage and giving all users permissions, or how should i do it?

I got a ubuntu server running on one scsi disc. And its a (quite) important webserver (didnt start out as a important one so it just got  one disc). Now i want (and kinda have to, if the disc crashes my head is on the line) to put anouther scsi disc and raid them. Never having done this before, is it possible to do it when there is already a existing system or will i have to re-install everything?

Also one small note. I have installed a lamp server on 6.06 LTS and i did it on 7.04 today (At home). On 6.06 the UserDir module in apache worked out of the box. It doesnt seem to work in 7.04.. How do i get it starting?

Cheers,
Benne

---

### Post by peabody on 2007-10-03
It sounds like you should be looking into learning LVM (logical volume manager).  LVM can't be installed from the desktop CD, it has to be installed from the alternative or server CDs.

LVM basically allows virtual partitions to span multiple media and dynamically shrink and grow (although dynamic shrinking isn't supported by the vast majority of filesystems out there though I believe dynamically growing filesystems is no problem for most of them.  You can shrink ext3 but requires bringing the system down).  It's seriously the wave of the future for Linux servers.  Need more space?  Add a disk array and then boot and grow your filesystems.  You can do it on RAID, external drives, whatever you wish.

Bad news for you is this basically means reinstalling as you have to setup the partitions for it.

---

### Post by seamuso on 2007-10-04
> **benne said:**
> 
Also one small note. I have installed a lamp server on 6.06 LTS and i did it on 7.04 today (At home). On 6.06 the UserDir module in apache worked out of the box. It doesnt seem to work in 7.04.. How do i get it starting?

Cheers,
Benne


go into /etc/apache2/mods-enabled .. Do you have 
userdir.conf and userdir.load in there? If not, you need to make 2 symlinks to the files that are located in the /etc/apache2/mods-available directory

from the mods-enabled dir, 

sudo ln -sf ../mods-available/userdir.conf .
sudo ln -sf ../mods-available/userdir.load .
sudo /etc/init.d/apache2 restart

---

### Post by conjur3r on 2007-10-04
> **peabody said:**
> It sounds like you should be looking into learning LVM (logical volume manager).  LVM can't be installed from the desktop CD, it has to be installed from the alternative or server CDs.
...

Bad news for you is this basically means reinstalling as you have to setup the partitions for it.

Great suggestion but just a little amendment:

LVM cannot be configured during installation of Ubuntu using the desktop CD.  You need the alternative or server disc.  That said, you can always install the package after installation which is exactly what this how to describes: [https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

Because of this, you do not need to reinstall to prepare hard disks/partitions for LVM.

The highest risk is running LVM on a non redundant RAID set of hard disks.  This is identical to RAID 0 where if one hard disk fails, you lose everything.

---

### Post by MJN on 2007-10-04
> **seamuso said:**
> sudo ln -sf ../mods-available/userdir.conf .
sudo ln -sf ../mods-available/userdir.load .
 
Better to simply use **sudo a2enmod userdir** (or leave the module name blank for a list) as whilst the tool doesn't do much more than add the symlinks now it is paving the way for more intelligent module handling further down the line so it's a good practice to get into.
 
(Note: sudo a2dismod <module> removes it)
 
Mathew

---

