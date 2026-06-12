---
title: "Best way to set up permissions w/ samba"
date: 2009-04-01
forum: Server Platforms
---

### Post by rbriggin on 2009-04-01
Im currently running Ubuntu Server 8.10

I have an external drive mounted automatically in the /etc/fstab file with the following line

```

/dev/sdc1 /media/share vfat user,exec,rw,auto,sync 0 0

```

This is my /etc/samba/smb.conf file

```

[global]
        workgroup = Workgroup
	server string = Welcome to Hell
	passdb backend = tdbsam
	username map = /etc/samba/smbusers
	log file = /var/log/samba/log.%m
	max log size = 50
	wins support = Yes
	cups options = raw

;[homes]
;	comment = Home Directories
;	read only = No

;[printers]
;	comment = All Printers
;	path = /var/spool/samba
;	printable = Yes
;	browseable = No

[share]
	path = /media/share
	read only = No
	guest ok = Yes


```

What i want is to allow people to logon and write to this drive.  and otherwise be read only access.

the problem for me is between linux users/permissions and sambas permissions im getting a little lost.  What is the correct way to go about this?

Thanks
Brandon

---

