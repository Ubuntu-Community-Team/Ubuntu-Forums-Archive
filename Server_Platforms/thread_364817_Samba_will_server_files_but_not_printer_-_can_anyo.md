---
title: "Samba will server files but not printer - can anyone spot the error?"
date: 2007-02-18
forum: Server Platforms
---

### Post by polc1410 on 2007-02-18
Hi,

I have a *little* experience of samba from a previous FC3 build.  Just rebuilding the serer on Ubuntu and hitting a problem:

[LIST]
[*]Samba installed and running (OK - ish)
[*]Samba seems to be file serving OK
[*]Samba point blank refuses to serve the printers?
[-]Samba was printing to a shared PDF printer fine (cups-pdf)
[-]Samba wasn't printing to a shared laser printer though - see note about cups spooler.. ..however now **neither** works
[/LIST]

I did have this nearer working - the print job was passed to cups, then dropped I think because I set the print spooler to the cups path (and now have read thats bad!).  But then I messed up my config - so I'm hoping someone with a fresh pair of eyes can spot my error...

Here's my config file:

```

[global]
	log file = /var/log/samba/log.%m
	load printers = yes
	smb passwd file = /etc/samba/smbpasswd
	lpq command = %p
	socket options = TCP_NODELAY
	write list = cpolwart,jenn1604
	username map = /etc/samba/smbusers
	interfaces = 127.0.0.0/8, eth0
	allow hosts = 192.168.1. 127.
	dns proxy = No
	netbios name = Linux-server
	writeable = yes
	printing = cups
	server string = %h server (Samba, Ubuntu)
	invalid users = root
	default = global
	unix password sync = Yes
	workgroup = MSHOME
	os level = 20
	auto services = global homes printers print$ home
	printcap name = /etc/printcap
	valid users = cpolwart,jenn1604
	security = user
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
        browsable = yes
        path = /home/cpolwart 
[homes]
	comment = Home Directories
	path = /home
	username = cpolwart,jenn1604
	valid users = cpolwart,jenn1604
	read only = No
	guest ok = Yes

[printers]
        printer = mfp_usbport_0  ## THIS is the printer which never worked !
	printable = yes
	writable = yes
	path = /var/spool/samba  ## I created this with 777 properties
	guest ok = Yes
	create mask = 0777
	comment = All Printers
	valid users = cpolwart,jenn1604

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	valid users = cpolwart,jenn1604
	write list = cpolwart,jenn1604
	read only = No
	guest ok = Yes
        printable = Yes


[home]
	comment = 
	writable = yes
	public = yes
	path = /home
	available = yes


```

At the moment I'm not too fussed about it being secure (its behind an internet firewall) but there are windows machines involved so some security would be nice ;-)

Any thoughts / suggestions / pointers very welcome...

Calum

---

