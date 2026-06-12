---
title: "Samba PDC access denied when trying to join machines"
date: 2012-08-01
forum: Server Platforms
---

### Post by X1R1 on 2012-08-01
Hi, I just configured a Samba PDC on my network, but every time I try to add a machine to the domain I am told "Access Denied"

I followed the instructions on the ubuntu help site here: [https://help.ubuntu.com/10.04/serverguide/samba-dc.html](https://help.ubuntu.com/10.04/serverguide/samba-dc.html)

But still I am unable to join machines to the domain.

Here is the output of testparm, hope its usefull:

```
testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[netlogon]"
WARNING: The "share modes" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_DOMAIN_PDC
Press enter to see a dump of your service definitions

[global]
	workgroup = CURRI
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	add user script = /usr/sbin/adduser --quiet --gecos "" %u
	add machine script = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
	logon script = logon.cmd
	logon drive = H:
	domain logons = Yes
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[homes]
	comment = Home Directories
	valid users = %S
	read only = No
	create mask = 0700
	directory mask = 0700
	browseable = No
	browsable = No

[netlogon]
	comment = Network Logon Service
	path = /home/samba/netlogon
	guest ok = Yes
	share modes = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

```

Any more info you need please ask, and thanks for the help!!!

---

