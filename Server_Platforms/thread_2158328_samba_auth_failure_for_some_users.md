---
title: "samba auth failure for some users"
date: 2013-06-28
forum: Server Platforms
---

### Post by urug on 2013-06-28
I have done some searching and haven't found the answer to this issue that has cropped up. Everything was working fine yesterday but today we're having issues. We're using Ubuntu 10.04.2 LTS and Samba 3.4.7. We are authenticating to ADS. 

When using smbclient to test authentication some users work and some don't.

```
root@10.0.0.1:/etc/samba# smbclient -L 10.0.0.1 -W EXAMPLE -U user1
Enter user1's password: 
Domain=[EXAMPLE.COM] OS=[Unix] Server=[Samba 3.4.7]

	Sharename       Type      Comment
	---------       ----      -------
	homes           Disk      Linux  Home
	share           Disk      Fast drive attached to compilation server
	share_tmp_home  Disk      tmp_home
	IPC$            IPC       IPC Service (Compilation server)
	user1        Disk      Linux  Home
Domain=[EXAMPLE.COM] OS=[Unix] Server=[Samba 3.4.7]

...

root@10.0.0.1:/etc/samba# smbclient -L 10.0.0.1 -W EXAMPLE -U user2
Enter user2's password: 
Domain=[EXAMPLE.COM] OS=[Unix] Server=[Samba 3.4.7]
tree connect failed: NT_STATUS_ACCESS_DENIED

```

Here is my <scrubbed> smb.conf

```
[global]
	workgroup = EXAMPLE
	realm = example.com
	server string = Compilation server
	security = ADS
	map to guest = Bad User
	obey pam restrictions = Yes
	password server = dc01.example.com dc02.example.com
	algorithmic rid base = 500000
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	restrict anonymous = 2
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 100
	load printers = No
	printcap name = /etc/printcap
	local master = No
	domain master = No
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap backend = nss
	template homedir = /%N
	template shell = /bin/bash
	winbind enum users = Yes
	winbind enum groups = Yes
	idmap config EXAMPLE:range = 100-999999
	idmap config EXAMPLE:readonly = yes
	idmap config EXAMPLE:backend = nss
	idmap config EXAMPLE:default = yes
	map acl inherit = Yes
	printing = bsd
	print command = lpr -r -P'%p' %s
	lpq command = lpq -P'%p'
	lprm command = lprm -P'%p' %j
	map archive = No
	map readonly = permissions

[homes]
	comment = Linux  Home
	username = %S
	read only = No
	create mask = 0600

[share]
	comment = Fast drive attached to compilation server
	path = /srv/share
	read only = No
	create mask = 0644

[share_tmp_home]
	comment = tmp_home
	path = /fs_mixte_rhome
	read only = No
	create mask = 0644

```

I haven't found anything useful in my samba logs. Any ideas of what to check next?

---

