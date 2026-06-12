---
title: "Create network samba shares"
date: 2014-05-16
forum: Server Platforms
---

### Post by Jacob_Tennant on 2014-05-16
I am very new to Samba so please be patient with me...

I have setup a Samba file server with 14.04LTS using the Samba install offered during the installation of 14.04LTS.

I have it joined to my Windows 2012R2 AD server and wbinfo -u & wbinfo -g returns the users and groups in my AD.

What I am now trying to get setup is a system where I can tell AD that a users Home storage is on the Samba server as "P" drive.

So when a user logs onto a domain based computer they automatically see the "P" drive without any further actions.

Currently from the AD I can see the samba server (UBUNTU1) in the Networks panel of Folders. I can authenticate to access it with the local samba admin account but not my AD users account. When I authenticate into UBUNTU1 there is no sub-folders to go into or options to create a subfolder.

I believe this is controlled by the smb.conf file but I am a little overwhelmed by the various config options in the basic smb.conf file.

---

### Post by Jacob_Tennant on 2014-05-16
Here is copy of the output from testparm smb.conf...
[global]
	workgroup = PIERPONT
	realm = pierpont.edu
	server string = %h server (Samba, Ubuntu)
	security = ADS
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	logon drive = P:
	domain logons = Yes
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	template shell = /bin/bash
	winbind enum users = Yes
	winbind enum groups = Yes
	winbind use default domain = Yes
	winbind trusted domains only = Yes
	idmap config * : range = 10000-20000
	idmap config * : backend = tdb
	path = /home/local/PIERPONT/
	read only = No


[homes]
	comment = Home Directories
	valid users = %S
	create mask = 0700
	directory mask = 0700
	browseable = No


[netlogon]
	comment = Network Logon Service
	path = /home/samba/netlogon
	read only = Yes
	guest ok = Yes


[profiles]
	comment = Users profiles
	path = /home/samba/profiles
	create mask = 0600
	directory mask = 0700
	browseable = No


[printers]
	comment = All Printers
	path = /var/spool/samba
	read only = Yes
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	read only = Yes

---

### Post by volkswagner on 2014-05-18
You don't have any shares setup other than [homes], which is a special type of share.  If your user does not have a home folder, this is why you don't
see any shares (folders) listed when you navigate to the UBUNTU1 via network places.

I never joined a SAMBA4 machine to AD, but there is some documentation [here]("http://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server").

I also noticed that pierpont.edu is a real internet domain.  I'm not sure if this is a mask of your actual ActiveDirectory domain
of if you have internal DNS settings to point pierpont.edu at your server.

---

