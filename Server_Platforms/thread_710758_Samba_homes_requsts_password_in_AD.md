---
title: "Samba homes requsts password in AD"
date: 2008-02-28
forum: Server Platforms
---

### Post by sokraski on 2008-02-28
I have been working on this for weeks.  I have an Ubuntu 7.10 file/print server.  This is in a W2K3 AD environment.  I have followed many guides, samples, etc...  I receive a ticket using kinit, wbinfo and getent all return DOMAIN+....  I can also join the domain.  Windows XP users can use the shares just fine.  The problem is with the homes.  When they browse to the Ubuntu server through network neighborhood, they can see and use shares and also see their home folder (username).  But when they try to open their home folder, it prompts them for a password.  No combination of password will allow access.  I would like for them to not have to enter a password since they are already in the AD.  This is the last hurdle in finally getting linux at the office.  Thanks in advance.

smb.conf:
[global]
	log file = /var/log/samba/%m
	idmap uid = 10000-20000
        idmap gid = 10000-20000
	realm = DOMAIN.COM
	template shell = /bin/bash
	printing = cups
	server string = %h

	workgroup = DOMAIN
	printcap name = CUPS
	security = ads
	winbind separator = +
	max log size = 50
	log level = 1
        winbind enum groups = yes
        winbind enum users = yes 

[homes]
	comment = Home Directories
	browseable = no
	valid users = %S
	writeable = yes
	available = yes
[printers]
	guest ok = Yes
	comment = SMB Print Spool
	printable = yes
	path = /var/spool/samba
[print$]
	comment = Printer Drivers
	admin users = root, Administrator
	path = /var/lib/samba/drivers
	write list = root

[Documents]
	comment = 
	writeable = yes
	path = /home/DOMAIN/Documents
	available = yes

[quickXchange]
	writeable = yes
	path = /home/DOMAIN/QuickShare
	available = yes

[Software]
	comment = 
	writeable = yes
	path = /home/DOMAIN/Software
	available = yes

I have made the directory /home/DOMAIN with permissions 0777


# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.
passwd:         compat winbind
group:          compat winbind
shadow:         compat
hosts:          files dns
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis

---

### Post by k_grdn on 2008-02-29
Hi,

Have used smbpasswd to set the users pasword?

Regards,

k_grdn

---

### Post by sokraski on 2008-02-29
I have not.  I thought that AD would handle everything.  Do I need to enter everyone's password using smbpasswd?  Since they are alrady logged into/authenticated against the AD, do they still have to enter a password?  Thank you very much for replying.

---

