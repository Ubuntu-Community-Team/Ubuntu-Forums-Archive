---
title: "using samba to share NTFS partition"
date: 2009-12-02
forum: Server Platforms
---

### Post by roozbeh on 2009-12-02
I am trying to use samba to share my NTFS partitions with writeing enabled with windows xp users.
but there is a wierd problem.
i can copy files into root of shared partition but in some subfolders i can not and i get ...there is not enough disk space... error from windows.

here is my fstab
```

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=afa0c5b6-3b59-41d2-a57e-042a53f6ab43 / ext4 errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=2b5eda05-3ad8-4122-9233-606e34d59a72 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda6 /media/PROGRAMMING ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/MEDIA ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda4 /media/New\040Volume ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda2 /media/Windows\040XP ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb2 /media/Volume ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

and here is my smb.conf file
```

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
	server string = %h Server

	show add printer wizard = no
	null passwords = yes
	map to guest = Bad User

#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
	log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
	max log size = 1000

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
	syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
	panic action = /usr/share/samba/panic-action %d

####### Authentication #######

	security = user
	username map = /etc/samba/smbusers
	encrypt passwords = true
;	passdb backend = tdbsam
	obey pam restrictions = yes

;	guest account = nobody
	invalid users = root

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\successfully* .

############ Misc ############

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
# SO_RCVBUF=8192 SO_SNDBUF=8192
;	socket options = TCP_NODELAY

#======================= Share Definitions =======================

[Public]
	comment = Public Share Directory
	path = /media/MEDIA
	writeable = yes
	browseable = yes
	guest ok = yes
	create mask = 0777
	directory mask = 0777

```

---

### Post by roozbeh on 2009-12-04
anybody?
any hint on anything related to this?
please....

---

