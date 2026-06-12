---
title: "samba problem. NT_STATUS_MEDIA_WRITE_PROTECTED"
date: 2009-10-16
forum: Server Platforms
---

### Post by implor on 2009-10-16
I have a problem with samba. I can read all my folders but when I try to write I'm getting NT_STATUS_MEDIA_WRITE_PROTECTED. This use to work! I only change the name in smb.conf for my share and added a few extra shared folders (I copy the code  and edited path and name). I don't understand what's wrong, do samba us dual config files?

my smb.conf

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
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[homes]
	comment = Home Directories
	read only = No
	create mask = 0775
	directory mask = 0775

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[ljet]
	path = /var/spool/lpd/lp
	read only = No
	guest ok = Yes
	printable = Yes
	print command = lpr -r -h -P %p %s
	printer name = lp

[common]
	path = /home/delat/common
	valid users = evor0001
	read only = No

[resources]
	path = /home/delat/resources
	valid users = evor0001
	read only = No

[project]
	path = /home/delat/project
	valid users = evor0001
	read only = No

[salary]
	path = /home/delat/salary
	valid users = evor0001
	read only = No
	create mask = 0775
	directory mask = 0775

```

---

### Post by lykwydchykyn on 2009-10-16
Not 100% sure, but that error would tend to indicate to me that there is a problem with the filesystem (unix) permissions on the shared directory.

What are the permissions set to on your shared folder, and what user are you connecting as?

---

