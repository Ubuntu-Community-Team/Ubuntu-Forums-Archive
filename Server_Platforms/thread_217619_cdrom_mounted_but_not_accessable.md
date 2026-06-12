---
title: "cdrom mounted but not accessable"
date: 2006-07-17
forum: Server Platforms
---

### Post by Distue on 2006-07-17
Hi community,

**My System:**
*hardware:*
IBM Netfinity 5500 Server
ServeRaid II Controller
CD-Rom is IDE

*software:*
Ubuntu 6.06 Server
Lamp Installation

**My Problem**
This is a completeley new installation so I wanted to install ssh. I did update the sources.list table then

```
sudo apt-get install ssh openssh-server

Reading package lists... Done
Bulding dependency tree... Done
The following extra packages will be installed:
  openssh-client
Suggested packages:
  ssh-askpass xbase-clients rssh
The following NEW packages will be installed:
  openssh-client sopenssh-server ssh
0 upgraded, 3 newly installed, 0 to remove and 0 no upgraded
Need to get 0B/742kB of archives
After unpacking 1888 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y

[B]Failed to fetch cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/pool/main/o/openssh/openssh-client_4.2p1-7ubuntu3_i386.deb MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/B]
```

so i wanted to check the cdrom 

```
cd /media/cdrom0
ls -l
**total 0**
```

I did the installation with this CD-Rom (there is just one) and it is the correct CD, so help me plz :-/

---

### Post by wahman143 on 2006-07-17
Hi, 
You need to edit your /etc/apt/sources.list file and comment out the first line like such:

```

#deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

```

That should fix your problem with apt.

Cheers, and hope that helps,
W.

---

### Post by fdamstra on 2006-07-17
Commenting out that line in /etc/apt/sources.list will make the system grab files from the Internet and will ignore the cdrom.

If, for some reason (no network?), you want to install packages off the cdrom, you simply need to mount it first, by running 'mount /mnt/cdrom'.  When you're done, unmount the cdrom by typing 'umount /mnt/cdrom'.

---

### Post by Distue on 2006-07-18
Thanks for the answers.

@wahman143
well i'd like to use the cdrom

@fdamstra
mount /mnt/cdrom
-> mount: can't find /mnt/cdrom in  /etc/fstab or /etc/mtab

umount /mnt/cdrom
-> umount: /mnt/cdrom: not found

ls -l /mnt
total 0

ls /media
cdrom cdrom0 floppy floppy0

;/

---

### Post by fdamstra on 2006-07-18
Sorry about that.  /mnt/cdrom would be my other linux distro.  In Ubuntu, it's /media/cdrom0.

So, to mount the cdrom, run 'mount /media/cdrom0', and to unmount, use 'umount /media/cdrom0'.

If you still have problems, do a 'cat /etc/fstab' and post it here... the line that contains your cdrom will tell us what the parameter to mount should be.

---

