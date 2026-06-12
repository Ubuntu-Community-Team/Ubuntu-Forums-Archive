---
title: "Samba problem on multiple interfaces. Lucid Lynx"
date: 2010-05-09
forum: Server Platforms
---

### Post by sikander3786 on 2010-05-09
Hi i am using samba on ubuntu lucid.

The problem is that samba shares files easily on eth0 while on eth1, every file gives a read error.

My config file is attached.

Any help is appreciated.

```

[global]
	workgroup = WORKGROUP
	server string = %h server (Samba, Ubuntu)
	dns proxy = no
	usershare owner only = false
	read size = 65536
	read prediction = true
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

#### Networking ####
	bind interfaces only = no

#### Debugging/Accounting ####
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action %d

####### Authentication #######
	#   security = user
	encrypt passwords = true
	passdb backend = tdbsam
	obey pam restrictions = yes
	unix password sync = yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	pam password change = yes
	map to guest = bad user

########## Printing ##########
	load printers = yes
	printing = cups
	printcap name = cups

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

```

---

### Post by sikander3786 on 2010-05-09
I have found that anything going through the non-default interface gets corrupted and read errors arise in it.

Not a problem with samba. It is a problem with Ubuntu Lucid. Now how will it be fixed?

Any hints?

---

