---
title: "Some imperfections"
date: 2009-08-13
forum: Server Platforms
---

### Post by ultimatebuster on 2009-08-13
I have an ubuntu server with Gnome installed. I use it to share network drive (samba) and share usb printer. I mainly uses webmin to manage. 

My primary user name is [FONT="Courier New"]administrator[/FONT]

Just to be clear, all these are working. (sharing drive, printers etc. Just some problem.)

Here are my SMB settings:

Folder Share
```

[data]
	guest account = administrator
	writeable = yes
	path = /media/DATA
	force user = administrator
	public = yes
	guest only = yes

```

Printer Share
```

[kksprinter]
	guest account = administrator
	printer = HP-LaserJet-1020
	writeable = yes
	printable = yes
	comment = HP LaserJet 1020
	public = yes
	guest only = yes

```

This is the problem:
[LIST=1][*]For some reason, if I turn off the printer or disconnect it, I have to delete the existing printer, and re-add it. This is a major annoyance when I have to reboot, or turn off the printer.
[*]I have multiple users using the hard drive. I want a user account for each of them, so they can log in when they map the drive in Windows. On the ubuntu side, I would just use "sudo chown -R <username> <their directory>". Here is the problem, how do I create an administrative account that's not root, to be able to manage (Read/Write) all the directories?
[*]Also, why do I already have 7GB used on an empty partition?
[/LIST]

---

### Post by cariboo on 2009-08-14
Your running Gnome, so why not use System-->Administration-->Users and Groups. No need to add ownership. You may want to change the home directory permissions to 700, so your users can't snoop in each others directories.

As far as using 7Gb of an empty drive, have you done any upgrades? All the downloaded packages are archived in /var/cache/apt/archives.

---

### Post by ultimatebuster on 2009-08-14
Maybe I wasn't clear enough, but these users won't have physical access to this machine. All the logins has to be done through SAMBA remotely.

This is what I would have
```
[data]
	writeable = yes
	path = /media/DATA

```

I would then give each user a directory within /media/DATA that they can read and write with. They cannot read and write the directory of other users.

Also, I want an admin account (not root) that can read and write the directory of all users, for administrative purposes.

---

