---
title: "smb.conf"
date: 2010-01-20
forum: Server Platforms
---

### Post by OYY on 2010-01-20
This my smb.conf file..! I only use for normal file sharing, got any problem or not of this smb.conf? hope you all can give me some suggestion to me to improve mine samba server performance..thank.

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	socket options = TCP_NODELAY
	obey pam restrictions = yes
	null passwords = yes
	map to guest = bad user
	encrypt passwords = yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	wins support = true
	dns proxy = no
	netbios name = Bcs_Server
	server string = fileserver
	unix password sync = yes
	workgroup = MSHOME
	os level = 65
	debug level = 1
	syslog = 0
	security = user
	usershare allow guests = yes
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	pam password change = yes

---

### Post by Vegan on 2010-01-20
I suggest visiting samba.org and read the manual.

---

### Post by OYY on 2010-01-20
> **Vegan said:**
> I suggest visiting samba.org and read the manual.

thank o....:popcorn:

---

