---
title: "Samba login fail"
date: 2008-06-27
forum: Server Platforms
---

### Post by BMOE on 2008-06-27
Hello everyone.

I'm using Ubuntu 8.04 Server Edition.

I'm about to set up a fileserver at home using SAMBA and SWAT as GUI interface.

I have put in a new HDD as I have partitioned and mounted as /mnt/files and then CHMOD'ed /mnt/files to 777.

I have added a user called bmoe to linux, and samba with the exact sama password.

Now to my problem.
From my windows laptop at home I can see the server when I browse my Windows Network, and I can login using bmoe as login name and the password, and see my shares, but when I "double click" my shared folder I get promted for a usernam and password once again but now i cant login.

Please help me.

This is what my smb.conf file looks like.

```
# Samba config file created using SWAT
# from 192.168.0.4 (192.168.0.4)
# Date: 2008/06/28 00:10:46

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
	ldap ssl = no
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Share /mnt/files]
	comment = Share /mnt/files
	path = /mnt/files
	valid users = bmoe
	read only = No
	guest ok = Yes

```

---

