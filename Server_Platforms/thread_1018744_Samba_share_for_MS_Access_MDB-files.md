---
title: "Samba share for MS Access MDB-files"
date: 2008-12-22
forum: Server Platforms
---

### Post by gjosef on 2008-12-22
I've set up a Samba share of an NTFS-formatted USB-disk on Ubuntu 8.04. Have clients working against MS Access database files (.mdb files) over this share, but when they are accessing the same mdb-database simultaneously, I quickly get file locking error messages. Was running this on a Windows 2000 share previously, and multi-user access worked fine there. Am I doing something wrong in my smb.conf file?

Here is the main section of smb.conf:

```
[global]
	server string = 
	workgroup = workgroup
	security = user
	hosts allow = 127. 192.168.2.
	interfaces = 127.0.0.1/8 192.168.2.0/24
	remote announce = 192.168.2.255
	remote browse sync = 192.168.2.255
	printcap name = /etc/printcap
	cups options = raw
	log file = /var/log/samba/samba.log
	max log size = 1000
	username level = 8
	password level = 8
	unix password sync = yes
	# socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=32768 SO_SNDBUF=32768
	local master = no
	domain master = no
	preferred master = no
	os level = 33
	logon drive = m:
	logon home = \\%L\homes\%u
	logon path = \\%L\profiles\%u
	logon script = %G.bat
	name resolve order = wins lmhosts bcast
	wins server = 
	dns proxy = no
	client use spnego = no
	client signing = no
	client schannel = no
	server schannel = no
	allow trusted domains = no
	obey pam restrictions = yes
	follow symlinks = no
	update encrypted = yes
	passwd chat timeout = 120
	username map = /etc/samba/smbusers
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete user script = /usr/sbin/userdel '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	machine password timeout = 120
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template shell = /dev/null
	winbind use default domain = yes
	winbind separator = @
	winbind cache time = 360
	winbind trusted domains only = yes
	winbind nested groups = no
	winbind nss info = no

```

Anything here that affects multiuser simultaneous file access negatively?

TIA.

---

### Post by cariboo on 2008-12-22
I have run into the same problem, it was several years ago, but if I remember correctly, it had something to do with workgroup admin in MS Access.

You don't say wether the users are just accessing the .mdb file, or changing/designing applications, the only time I have seen the files locked is during design.

Jim

---

### Post by gjosef on 2008-12-23
Hi Jim,

I am talking about locking problems when doing normal db access to the file (entering records, running queries, etc). I am aware of the problems with mdb files getting locked when designing forms and reports (since version 2000 onwards - worked much more intelligently in earlier versions), but that's another issue (and one that Ubunutu/Samba can't affect). My question here is why 'normal' database use causes locking issues. Some searching on the net indicates that it has to do with Samba's setup parameters, but as I'm new to using it, I'm still a bit lost, and I also have trouble filtering out what tricks are obsolete (were needed for older versions of Samba but might not be of value anymore), and which ones are still relevant.

---

