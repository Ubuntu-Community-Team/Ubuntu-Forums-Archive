---
title: "Need help with Samba"
date: 2006-06-13
forum: Server Platforms
---

### Post by MSatterwhite on 2006-06-13
I'm trying to get Samba running on my machine. Note that the share I'm interested in is 'Michael'.

I used apt-get to install the packages. I (thought I) used SWAT to set the share parameters - the share needs to be writeable as well as readable. I have run smbpasswd to add the user. At lease I think I have. Where in heaven's name does it put that file?

My Windows machine can connect to the share and read any file in it. When I try to write to a file, or create a new one, I get an error telling me I don't have permission to access the file. I've attached my smb.conf file to this message. Any help you can give me will be greatly appreciated.

---

### Post by MSatterwhite on 2006-06-13
Sorry, I didn't post the configuration file inline. Here it is (I'm trying to get the share 'Michael' to be writeable as well as readable.
------------------------------
[global]
	workgroup = SATTERWHITE
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam, guest
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	server signing = auto
	preferred master = No
	domain master = No
	dns proxy = No
	ldap ssl = no
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	write list = michael

[homes]
	comment = Home Directories
	read only = No
	create mask = 0775
	directory mask = 0775

[printers]
	comment = All Printers
	path = /tmp
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[michael]
	comment = michaels home
	path = /home/michael
	read only = No
	create mask = 0775
	directory mask = 0775
	guest ok = Yes
	case sensitive = No
	msdfs proxy = no

[remwindows]
	comment = Windows directory
	path = /windows/c
	invalid users = 
	guest ok = Yes
	case sensitive = No
	msdfs proxy = no

[Unnamed3]
	path = /tmp
	printable = Yes
	printer name = C64

---

### Post by linuchsan on 2006-06-13
Try the following:

[michael]
inherit permissions = yes
printable = no
writable = yes
read only = no
path = /home/michael
comment = michaels home
create mode = 0660

---

### Post by MSatterwhite on 2006-06-13
That did it. Thanks much.

What was the main piece of magic? 

---Michael

---

