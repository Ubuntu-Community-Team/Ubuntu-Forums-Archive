---
title: "Ubuntu 9.10 Samba+Roaming+Win7"
date: 2009-12-07
forum: Server Platforms
---

### Post by LarsEriksson on 2009-12-07
Ive got a samba 3.4.0 running on a Ubuntu server, with roaming profiles.
Windows XP and Vista clients can connect and use their domain account and profile without any problems.

But one laptop with Windows 7 gets the profile reset some times.
For example, i can log in and out a couple of times, but the next day when i log in the account is reset.

The really wierd thing is that i have Windows 7 running as a test, through Virtualbox, without any problems.

(ive applied the 2 registry fixes to the Win7 computers to be able to join the domain)

I cant find anything in the samba logs that can explain this behaviour, and ive been searching on the internet without any luck.


Configuration:
```
[global]
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	write list = @domainuser,@sysadmin
	passwd program = /usr/bin/passwd %u
	dns proxy = no
	netbios name = WINTECH
	delete readonly = yes
	logon script = logon.bat
	workgroup = WINTECH
	security = user
	usershare allow guests = yes
	add machine script = sudo /usr/sbin/useradd -N -g machines -c Machine -d /var/lib/samba -s /bin/false %u
	max log size = 1000
	log file = /var/log/samba/log.%m
	smb ports = 139
	include = /etc/samba/dhcp.conf
	logon drive = Z:
	map to guest = bad user
	domain master = yes
	winbind trusted domains only = yes
	encrypt passwords = yes
	passdb backend = tdbsam
	logon home = \\%N\%U
	wins support = yes
	server string = %h
	unix password sync = yes
	logon path = \\%N\%U\profile
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	pam password change = yes
	domain logons = yes

;   wins server = w.x.y.z
;   name resolve order = lmhosts host wins bcast
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = yes
;logon path = \\%N\profiles\%U

; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   winbind enum groups = yes
;   winbind enum users = yes
;   usershare max shares = 100
[homes]
   comment = Home Directories
   browseable = no
   read only = no
   create mask = 0700
   directory mask = 0700
   valid users = %S
   csc policy = disable
oplocks = 0
level2 oplocks = 0

[netlogon]
   comment = Network Logon Service
   path = /srv/samba/netlogon
   guest ok = yes
   read only = yes
   csc policy = disable


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
;   write list = root, @ntadmin

;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom




```

---

