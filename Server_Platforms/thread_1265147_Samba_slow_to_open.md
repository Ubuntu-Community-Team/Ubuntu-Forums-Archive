---
title: "Samba slow to open"
date: 2009-09-13
forum: Server Platforms
---

### Post by Serangan on 2009-09-13
Hi,

I lost my old smb.conf (due to reinstall) and i made a new one, but now, whenever it is the first time to open a shared folder, it will take 30+ seconds to open. This didn't happen before and I was wondering if anyone has an answer.

This is my smb.conf
```

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	log level = 2
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	read raw = No
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	dns proxy = No
	wins support = Yes
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	read only = No
	oplocks = No

[homes]
	comment = Home Directories
	valid users = %S
	create mask = 0775
	directory mask = 0775
	browseable = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	read only = Yes
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	read only = Yes

[cdrom]
	comment = Samba server's CD-ROM
	path = /cdrom
	read only = Yes
	guest ok = Yes
	locking = No
	preexec = /bin/mount /cdrom
	postexec = /bin/umount /cdrom

[Photos]
	comment = Shared folder for photos
	path = /storage/photos/photos

[Backup]
	comment = Shared folder for backups
	path = /storage/backup

[Music]
	comment = Shared folder for music
	path = /storage/music/music

[Software]
	comment = Shared folder for software
	path = /storage/software

[Downloads]
	comment = Shared folder for downloads
	path = /storage/downloads/downloads

```

Is there anything wrong? or something that could be changed to improve speed? And the specs of the server are in my sig.

Thanks


Edit:

It seemed to speed up as soon as I disabled the cdrom share. No idea why but im happy now.

---

### Post by swerdna on 2009-09-13
Just passing, not sure if this is relevant, but FWIW:

Open a Gnome terminal and run the command testparm. You'll see this:
> Invalid combination of parameters for service homes. 			   Level II oplocks can only be set if oplocks are also set.
Invalid combination of parameters for service printers. 			   Level II oplocks can only be set if oplocks are also set.
Invalid combination of parameters for service print$. 			   Level II oplocks can only be set if oplocks are also set.
Invalid combination of parameters for service cdrom. 			   Level II oplocks can only be set if oplocks are also set.
Invalid combination of parameters for service Photos. 			   Level II oplocks can only be set if oplocks are also set.
Invalid combination of parameters for service Backup. 			   Level II oplocks can only be set if oplocks are also set.
Invalid combination of parameters for service Music. 			   Level II oplocks can only be set if oplocks are also set.
Invalid combination of parameters for service Software. 			   Level II oplocks can only be set if oplocks are also set.
Invalid combination of parameters for service Downloads. 			   Level II oplocks can only be set if oplocks are also set.


That's interesting

---

### Post by Serangan on 2009-09-14
Um, ok... no idea what all that means.

I get that without the cdrom share. So I guess it has nothing to do with that.

Should i change the oplocks = no to yes?

What will that do?

---

### Post by swerdna on 2009-09-14
> **Serangan said:**
> Um, ok... no idea what all that means.

I get that without the cdrom share. So I guess it has nothing to do with that.

Should i change the oplocks = no to yes?

What will that do?

I don't know anything about oplocks -- I just ran your smb.conf through testparm and out popped the error. You had put the line there for some reason I suppose -- but if not, then try this: Delete the line altogether and see what happens.

Also, you can check out oplocks here: [http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html).

---

