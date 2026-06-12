---
title: "Unable to access location Failed to retrieve share list from server: No such file or"
date: 2013-08-17
forum: Ubuntu Development Version
---

### Post by tad1073 on 2013-08-17
The title says it all. Anyone else experiencing this problem?

---

### Post by tad1073 on 2013-08-18
bump

---

### Post by cariboo on 2013-08-18
There isn't any information in your post, what have you done to create this problem? Are you trying to access a system running Saucy when you get the message, are you trying to access another system running a different version? Are you trying to access a Windows system?

---

### Post by tad1073 on 2013-08-19
> **cariboo907 said:**
> There isn't any information in your post, what have you done to create this problem? Are you trying to access a system running Saucy when you get the message, are you trying to access another system running a different version? Are you trying to access a Windows system?

Yes, I am on 13.10. I have created shares, setup smb.config with the appropriate workgroup. The shares are on ntfs formatted drives which I have set up to to automount in fstab with group plugdev, created a samba user so I could make the shared folders a little more secure. I am also running a LAMP server and a DNS server both of which run just fine.

This happens when I try to open via browse network>windows network and it happens in both directions.

An added note, I have XBMC installed and am using the yatse app on my phone for a remote control and that doesn't even connect.

```
[global]
	workgroup = THOMPSONFAMILY
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	guest account = sambaguest
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	socket options = TCP_NODELAY IPTOS_LOWDELAY IPTOS_THROUGHPUT SO_SNDBUF=65536 SO_RCVBUF=65536
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb
	guest ok = Yes


[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[My Movies]
	path = /media/shares/Media1/My Movies
	read only = No


[My Music]
	path = /media/shares/Media0/My Music
	read only = No


[My Pictures]
	path = /media/shares/Media0/My Pictures
	read only = No


[My Documents]
	path = /media/shares/Media0/My Documents
	read only = No
```

---

### Post by tad1073 on 2013-08-21
bump

---

### Post by cariboo on 2013-08-21
What's the output of:

```
smbtree
```

do you see a list of shares similar to this?

```
smbtree
Enter cariboo's password: 
APLUS
	\\WILLY          		willy server (Samba, Ubuntu)
		\\WILLY\print$         	Printer Drivers
		\\WILLY\Dad           	
		\\WILLY\Mom          	
		\\WILLY\me            	
		\\WILLY\data           	
		\\WILLY\IPC$           	IPC Service (willy server (Samba, Ubuntu))

	\\Dad-PC        		

	\\ALEXIS         		alexis server (Samba, Ubuntu)
		\\ALEXIS\Public         	
		\\ALEXIS\Brother-HL-5250DN-series	Brother HL-5250DN series
		\\ALEXIS\print$         	Printer Drivers
		\\ALEXIS\IPC$           	IPC Service (alexis server (Samba, Ubuntu))

```

**Note:** Willy is running 12.04, Dad-PC is running Windows 7, and Alexis is running Saucy, I used Nautilus to set the share on Alexis, which installed Samba, and set smb.conf as needed, the only thing I did was change the workgroup.

---

### Post by tad1073 on 2013-08-21
nothing

---

### Post by cariboo on 2013-08-22
> **tad1073 said:**
> nothing

Are you sure samba is running? What is the output of:

```
ps ax | grep nmbd
```

and

```
ps ax | grep smbd
```

on the system I'm running right now, alexis in post [#6]("http://ubuntuforums.org/showthread.php?t=2168405&p=12764628&viewfull=1#post12764628") the out put of the above commands looks like this:

```
cariboo@alexis:~$ ps ax | grep nmbd
  992 ?        Ss     0:00 nmbd -D
 4059 pts/1    S+     0:00 grep --color=auto nmbd
cariboo@alexis:~$ ps ax | grep smbd
  609 ?        Ss     0:00 smbd -F
  826 ?        S      0:00 smbd -F
 4061 pts/1    S+     0:00 grep --color=auto smbd
```

---

### Post by tad1073 on 2013-08-22
> **cariboo907 said:**
> Are you sure samba is running? What is the output of:

```
ps ax | grep nmbd
```

and

```
ps ax | grep smbd
```

on the system I'm running right now, alexis in post [#6]("http://ubuntuforums.org/showthread.php?t=2168405&p=12764628&viewfull=1#post12764628") the out put of the above commands looks like this:

```
cariboo@alexis:~$ ps ax | grep nmbd
  992 ?        Ss     0:00 nmbd -D
 4059 pts/1    S+     0:00 grep --color=auto nmbd
cariboo@alexis:~$ ps ax | grep smbd
  609 ?        Ss     0:00 smbd -F
  826 ?        S      0:00 smbd -F
 4061 pts/1    S+     0:00 grep --color=auto smbd
```

```

:~$ ps ax | grep nmbd
 1665 ?        Ss     0:00 nmbd -D
22565 pts/0    S+     0:00 grep --color=auto nmbd
thomas@thomthom:~$ ps ax | grep smbd
  649 ?        Ss     0:00 smbd -F
  726 ?        S      0:00 smbd -F
22661 pts/0    S+     0:00 grep --color=auto smbd

```

---

### Post by cariboo on 2013-08-22
Do you get any errors while running:

```
testparm
```

---

### Post by tad1073 on 2013-08-23
[http://ubuntuforums.org/showthread.php?t=2168405&p=12761751#post12761751](http://ubuntuforums.org/showthread.php?t=2168405&p=12761751#post12761751)

---

