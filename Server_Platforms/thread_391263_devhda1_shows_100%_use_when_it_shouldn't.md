---
title: "/dev/hda1 shows 100% use when it shouldn't"
date: 2007-03-23
forum: Server Platforms
---

### Post by lupes on 2007-03-23
Need some help here. Installed Ubuntu Edgy partitiong was done automatically during install using LVM.  Installed as a server and create a samba server. I have two 30GB drives formatted in Ext3 mounted for my Samba shares. 

Everything went fine and have been using it for a couple weeks. Today tried to copy over some files to my home directory (not to one of the samba shares) using SCP and was getting "not enough drive space" errors.

When I SSH into the server here is what I get for the df command:
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             7.6G  7.5G     0 100% /
varrun                126M  152K  125M   1% /var/run
varlock               126M     0  126M   0% /var/lock
procbususb             10M   76K   10M   1% /proc/bus/usb
udev                   10M   76K   10M   1% /dev
devshm                126M     0  126M   0% /dev/shm
/dev/hdb1              28G   11G   16G  40% /media/smb1

Here is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=be5e551c-8946-4964-959f-a7a47b3be9c0 / ext3  defaults 0       1
# /dev/hda5
UUID=53b63392-6f10-4114-8aa7-f3bc8c655a53 none            swap    sw              0       0
/dev/hdb1       /media/smb1     ext3    rw,acl,auto     0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd1       /media/smb2     ext3    rw,acl,auto     0       0

when I run ls h* in /dev I don't see my hdd drive:
hda  hda1  hda2  hda5  hdb  hdb1  hdc

As you can see from the df command above my hdd1 drive is not shown. Is this because its not in /dev?

My samba drives are mounted under /media/smbx and when I run the du command excluding the /media/smbx mount points I get the following:

745M    total

My samba drives show up as:
18G     total
one drive is 11.1G the other is 6.9G

Any ideas on what's going on with my system? My initial thought is that since hdd does not show up in /dev it is attributing the data from hdd to hda and maxing it out. I also think this because I have rsync setup between the shares and so they should both be 11.1GB but they are not the exact same size.

I may be totally wrong tho.

Any ideas on what's going wrong?

---

### Post by heimo on 2007-03-23
So you have three disks total? One for system (hda) and two externals for samba (hdb and hdd?) is hdc your cd/dvd drive (EDIT: Oh, I somehow missed your fstab listing first, yes hdc is supposed to be your cd/dvd)? You seems to have two separate problems, one is that your root partition is full - check how much data you have in your home dir. You may get more space by purging package cache using:
```
sudo aptitude clean
```Your other problem seems to be missing second external disk? I'm a little unsure about this, so could you run these commands and show us the output, so it'll be easier for me or someone else to help. Thanks! :)
```
mount
``````
sudo fdisk -l
```EDIT: Ups, you already did this, so no need to repeat.
```
cat /etc/fstab
```
Yet another edit: Are those external drives USB?  I'd probably try to run
```
 tail -f /var/log/messages
```
while attaching the missing hard disk and see if it gets detected.

---

### Post by lupes on 2007-03-23
heimo to answer your questions - 

- Yes, three drives, all are internal. 
- I understood my root partition was full, that is why I showed results from running the du command on the root while excluding the two samba shares. This shows that on my 7GB system drive I have less than 800MB (on hda1). That is why I am confused as to why the root partition shows full when executing the df command. 
The other sign of a problem is that with rsync I am forcing an exact copy between both 30GB drives (my samba shares mapped at /media/smbx). While the primary samba share shows 11.1GB the secondary shows 6.9GB. If you do a rough addition of the hda1 drive contents (~.8GB) and the samba share contents (~6.9GB) you come up with the total capacity of hda1 (~7GB). This tells me there is some confusion going on with my hard drives.

I think it may be a problem with the way I installed the internal drives. I think I remember having trouble putting the 7GB drive on the primary IDE channel and so I instead made it master on the secondary channel. This makes my internal IDE setup as follows:

Primary IDE
- Master - CDRom drive
- Slave - 30GB drive (used for samba)
Secondary IDE
- Master - 7GB system drive
- Slave - 30GB drive (used for samba)

Is this setup the reason I am having issues? If so, will moving the 7GB drive to master of the Primary IDE as well as placing the two 30GBs on the Secondary IDE work? Or will I screw up my whole system?

---

### Post by heimo on 2007-03-24
First thing to check is that BIOS detects all the drives correctly, and if not, check jumpers.

---

### Post by Mr. C. on 2007-03-24
Let's work with the data:

1) Most imporant is to find and remove files from /.  Run
```
du -s /*
```
and start working your way down the root directory tree to find where disk space is being used.  The df command is not mistaken.  The disk *is* essentially full.  Believe in the tools.

2) Don't bother trying to list devices in /dev.  If a device is not available to the system, it is because it either wasn't identified or it wasn't mounted.  Use fdisk /dev/hdd to determine what the partitions look like, and if the system can access the disk.

3) Move your root to the primary master channel.

4) Move your CD-ROM to be a slave instead of a master.  Master gets priority, and you don't want your disk to be lower priority than your CD.

Your current setup will not cause problems other than performance issues indicated by (3) & (4).

MrC

---

### Post by lupes on 2007-03-26
OK, I am an idiot. Finally realized my second 30GB drive died. Therefore rsync was writing all data to  the mount point for my samba share but since the drive wasn't mounting it was writing it all to Hda1. Deleted all the data at the mount point, re-arranged my fstab based on shifting my drives around and all is good.

Thank you all for taking the time to help me with this issue!

---

### Post by Mr. C. on 2007-03-26
Glad you found your troubles - sorry the disk is kaput.

MrC

---

