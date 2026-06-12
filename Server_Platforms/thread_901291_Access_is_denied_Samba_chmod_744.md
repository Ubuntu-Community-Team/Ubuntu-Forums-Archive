---
title: "Access is denied Samba chmod 744"
date: 2008-08-26
forum: Server Platforms
---

### Post by Raymond Day on 2008-08-26
I copied files from naslite server to my ubuntu server with ```
rsync -av 192.168.2.80::Disk-0 .
``` command so it is just like it was with the time, date, Owner, Group, and permissions of 744. Owner and Group are 98.

I have my /ect/samba/smb.conf set to:

> [Disk-0]
	browseable = yes
	writable = yes
	path = /usr/share/Disk-0
	force directory mode = 
	force create mode = 
	comment = Share Disk-0 (Read/Write)
	public = yes
	available = yes
	create mask = 0744
	guest ok = yes
	guest only = yes
	read only = no
	force user = nobody
	force group = nogroup

Global Settings are:

> [global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	socket options = TCP_NODELAY
	null passwords = yes
	map to guest = bad user
	encrypt passwords = true
	public = yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	dns proxy = no
	writeable = yes
	server string = %h server (Samba, Ubuntu)
	invalid users = root
	path = /usr/share/disk-0
	unix password sync = no
	workgroup = RDAY
	os level = 20
	comment = Share Disk-0 (Read/Write)
	security = share
	syslog = 0
	create mode = 744
	panic action = /usr/share/samba/panic-action %d
	usershare allow guests = yes
	max log size = 1000
	pam password change = no
	directory mode = 744

But all the time when I make a change and restart samba with ```
/etc/init.d/samba restart
``` and then test with make new folder it comes back with > Access is denide. I don't want to change the chmod number of the files they worked on the NASLite with chmod 744. I don't know why I can't get them to work the same on ubuntu server. So I can save files to it with samba like I did on NASLite.

Any one know how to fix this?

I can do a chmod -R 777 /usr/share/disk-0 and that works. But I want the chmod to stay the same as it was on NASLite.

-Raymond Day

---

