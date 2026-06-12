---
title: "Ubuntu Server Hacked/Crashed Config Files and Data Deleted"
date: 2010-04-14
forum: Server Platforms
---

### Post by PCWiseButNotLinuxYet on 2010-04-14
Okay, so I'm a newbee.
Had to let my network administrator go who new everything about Linux about 5 months ago.
 
I'm primarily a windows geek, not Linux.
 
This person has remotely logged into my network and brought down a VmWare server with 4 virtual server machines and a seperate Ubuntu server running as a backup server running PcBackup.
 
Data was deleted before crashing the servers by deleting config files. Once these servers were rebooted obviously they did not come back up.
 
I desperately need some good resources and instruction on how to recover/undelete these files as there has been little to no activity on these 2 servers since the damage has been done.
 
VmWare says they can not help. Ontrack wants  from $500 up to $8,000 to help restore the VmServer.
 
From what I can tell, through on-line research, I need to boot from a live Ubuntu CD, launch a recovery/undelete program and save what is found to an external usb hard drive. However I can not find a good utility to do this or an ISO for a live Ubuntu CD.
 
Please help, my business is down, web server, PBX, E-mail, Windows Server 2003 etc.
 
Thx.....

---

### Post by dudumomo on 2010-04-15
Bad situation indeed.
So you guess well, the easiest solution is to run a live CD on your machine ([http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download))
then you will need to use a software to recover your data.
I suggest you the software testdisk

To use it, run:
sudo testdisk /dev/yourharddrive

and this link should help you: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by cdenley on 2010-04-15
If the configuration files were deleted, they are basically gone. The data is still there, but all meta-data which would be used to identify where/what the data is has been zeroed out. You can recover files like images or common document formats since tools like testdisk's photorec can scan the raw data of your disk picking out common file types using magic numbers and stuff, but text files aren't really identifiable. I think the only way to recover them would be to pull all text off your disk with the strings command, then look through the text and pick out what you can identify as configuration files by hand. Unless you have backups for your backup server.

---

