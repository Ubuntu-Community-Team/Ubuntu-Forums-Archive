---
title: "Directory permissions issue in Samba shares"
date: 2015-10-25
forum: Server Platforms
---

### Post by vaf on 2015-10-25
Hi all

I have an odd one, that I can not figure out.  I thought it would be obvious and easy, but it is not proving to be. Running Ubuntu Server 14.02. I'm trying to have a share that users can add to but some directories are read only the the base folders, and fully editable inside the base folders (users can create new projects in the base of the share, but every night a cron job changes all the project folders to read only for world, with rwx for some users ~ the "managers" group)

I have a share that I have setup as follows:
[Projects]
	path = /shares/Projects
	public = yes
	writeable = yes
	create mode = 0777
	force create mode = 777
	vfs objects = recycle
	recycle:keeptree = yes
	recycle:versions = yes
	recycle:repository = RecycleBin

And unix permission for the directory:

drwxrwxrwx 787 root   root    40960 Oct 26 07:28 Projects

and unix permissions for the folders inside that folder as follows

drwxrwxr-x   6 root managers    4096 Oct 25 12:54 zzzzzfd8gforppg00

and a set of folders inside each project as follows

drwxrwxrwt 2 root managers 4096 Oct 25 12:53 General
drwxrwxrwt 2 root managers 4096 May 27  2014 Jobs
drwxrwxrwt 2 root managers 4096 Jun 22  2010 Protocols
drwxrwxrwt 2 root managers 4096 Oct 13  2010 Communications

(ie share directory is 0777 and folders directly below that are 0775, with the preloaded folders inside that being 777)

I achieve this by running the following command as a root cronjob every night:

chmod 0775 /shares/Projects/*
chmod 0777 /shares/Projects/*/*
chown root:managers /shares/Projects/*
chown root:managers /shares/Projects/*/*

PROBLEM: We operate in a Windows 7 user environment, and in this share all users (ie both the 'managers' group users and all others) have the ability to change the Project folder names (despite them being read only to the non-managers). Only 'managers' can delete the folders, but I need to protect the name of the folders (to prevent accidental name change).

I have tried fiddling with the permissions (tried 774 but removing execute doesn't allow the set of sub folders to be browsable inside the project folders)

Any help would be greatly appreciated

Vince

---

### Post by vaf on 2015-11-03
Does anyone have any light to shed on this?

---

### Post by darkod on 2015-11-04
I don't know samba permissions that much in details, but since the create mode is 777 wouldn't that allow all to change folder names? You remove the W later during the night but when they "open" the share they get the 777 mode and can use it until you remove the W overnight. Right?

I think it can be related to that...

---

