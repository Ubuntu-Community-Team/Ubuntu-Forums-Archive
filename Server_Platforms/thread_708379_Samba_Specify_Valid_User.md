---
title: "Samba Specify Valid User?"
date: 2008-02-26
forum: Server Platforms
---

### Post by Rufe0 on 2008-02-26
Hi
I'm having problems specifying a valid user for a shared folder on my samba server. It does work when I set a local user(adam) but I am needing to set domain users. I used the utility to make the code but then went into the file and changed some stuff I could see but its mostly unchanged from what was made automatically. Here is my code

[global]
	workgroup = choices
	security = domain
	idmap uid = 15000-20000
	idmap gid = 15000-20000
	winbind use default domain = Yes
	server string = 
	wins server = 91.43.10.30
	name resolve order = host wins
	winbind separator = +
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	passdb backend = tdbsam
	obey pam restrictions = yes
	invalid users = root
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
	load printers = no
	password server = 91.40.10.30
	winbind enum groups = yes
	winbind enum users = yes

[AdamsSharedFolder]
	public = yes
	path = /home/adam/Desktop/shared
	writable = yes
	create mask = 0775
	directory mask = 0775

[jrowson]
	path = /home/adam/Desktop/jrowson
	writable = yes
	valid users = jrowson
	admin users = adam
	create mask = 0775
	directory mask = 0775

[ahill]
	path = /home/adam/Desktop/ahill
	writable = yes
	valid users = ahill
	admin users = adam
	create mask = 0775
	directory mask = 0775

[Adams CD Drive].
	writable = yes
	locking = no
	path = /cdrom
	public = yes
	preexec = /bin/mount /cdrom
	postexec = /bin/umount /cdrom

[test]
	path = /home/adam/Desktop/test
	writeable = yes
	valid users = adam
	create mask = 0775
	directory mask = 0775

I have tried writing things like domain+user or @user and things like that but it still won't let me login to the folders.The wbinfo and getent tests do work perfectly so I don't know, any ideas?
Thanks Adam

---

