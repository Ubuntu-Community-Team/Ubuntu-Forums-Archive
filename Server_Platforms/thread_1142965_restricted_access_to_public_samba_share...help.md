---
title: "restricted access to public samba share...help"
date: 2009-04-29
forum: Server Platforms
---

### Post by hellarough on 2009-04-29
On my network, I can currently see the samba share that I set up from my ubuntu/windows laptop but every time I try to open it I get prompted for a user and password...I have tried entering every user name and pass possible but still I am not granted access. Considering that I have tried to set the configuration file to be public I cant figure out why this is happening.
help is much appreciated. 

here is my smb.conf file --->

```

[global]
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Miguel]
	comment = Home Files
	path = media/server
	valid users = ryan
	force user = nobody
	force group = nogroup
	read only = No
	create mask = 0777
	directory mask = 0777
	guest ok = Yes

```

---

### Post by hellarough on 2009-04-29
for now i will keep trying to edit the config file but I cant really find anything else  in the SAMBA manual that is useful.

let me know if you guys need anything else

---

### Post by hellarough on 2009-04-29
also I forgot to mention that when I access the server through torrentflux (since it is set to write to the same folder) there is an error for the directory path. 

path:/media/server/
"Path is not Writable -- make sure you chmod +w this path"

but I have already executed both of these commands with success

```
sudo chmod 777 -v /media/server/
sudo chmod 777 -v /media/server
```

---

### Post by hellarough on 2009-04-30
nevermind....I figured it out myself. The separate partition I had was causing problems so I reformatted / reinstalled and cut the smb.conf file down to the bare essentials. I'll probably post a link soon so no one else has to go through the pains I did.

---

