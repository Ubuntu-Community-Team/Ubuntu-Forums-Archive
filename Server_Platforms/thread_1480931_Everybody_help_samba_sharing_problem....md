---
title: "Everybody help samba sharing problem..."
date: 2010-05-12
forum: Server Platforms
---

### Post by OYY on 2010-05-12
sorry..may i ask a question about why my samba sharing folder always come out a message "You might not have permission to use the network resource. Contact the administrator  to find out if access permission. The network path was not found" 
i need doing refresh a few time and then click again the folder to access. this is what happen? please give me some solution or advise

---

### Post by FiveSidedPoly on 2010-05-12
Could you please give us your samba config, as well as give us more information as to what sort of network you have setup, what version of Ubuntu/Windows you are using.

The more info the better.

---

### Post by OYY on 2010-05-12
this is my smb.conf file

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	socket options = TCP_NODELAY
	obey pam restrictions = yes
	map to guest = bad user
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	wins support = Yes
	dns proxy = no
	netbios name = Server02
	server string = Server02
	wins support = Yes
	unix password sync = yes
	workgroup = WORKGROUP
	os level = 65
	debug level = 3
	syslog = 0
	security = user
	panic action = /usr/share/samba/panic-action %d
	usershare allow guests = yes
	max log size = 1000
	pam password change = yes

Actually i can access the folder but the problem are sometimes the error message i mention before "The network path not found" will come out and then i need being refresh a few time for access..:(

---

