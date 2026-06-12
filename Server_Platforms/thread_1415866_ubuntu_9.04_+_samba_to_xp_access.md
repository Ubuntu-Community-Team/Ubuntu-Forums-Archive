---
title: "ubuntu 9.04 + samba to xp access"
date: 2010-02-25
forum: Server Platforms
---

### Post by t_virus on 2010-02-25
hello all,
i seem to have this problem that i cant connect xp to my samba server at my ubuntu machine.
i&#7743; using SWAT. if anyone could see the output and help me would be a nice help.

thankx

# Samba config file created using SWAT
# from UNKNOWN (&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;q&#65533;&#65533;&#1279;&#65533;i&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1279;)
# Date: 2010/02/25 16:19:59

[global]
	netbios name = SAMBA_SERVER
	server string = Samba
	interfaces = 127.0.0.1/8, 192.168.1.0/24
	bind interfaces only = Yes
	security = SERVER
	update encrypted = Yes
	client schannel = No
	server schannel = No
	allow trusted domains = No
	obey pam restrictions = Yes
	root directory = /
	guest account = no
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	passwd chat timeout = 120
	username map = /etc/samba/smbusers
	password level = 6
	username level = 6
	unix password sync = Yes
	log file = /var/log/samba/samba.log
	max log size = 1000
	name resolve order = wins lmhosts bcast
	client signing = No
	client use spnego = No
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = cups
	machine password timeout = 120
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	delete user script = /usr/sbin/userdel '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	logon script = %G.bat
	logon path = \\%L\profiles\%u
	logon drive = m:
	logon home = \\%L\homes\%u
	os level = 33
	local master = No
	domain master = No
	dns proxy = No
	wins support = Yes
	remote announce = 192.168.1.255
	remote browse sync = 192.168.1.255
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template shell = /dev/null
	winbind separator = @
	winbind cache time = 360
	winbind use default domain = Yes
	winbind trusted domains only = Yes
	winbind nested groups = No
	winbind nss info = no
	valid users = teste, t_virus, nome-4cca87a7b4, tvirus
	hosts allow = 127., 192.168.1.
	cups options = raw
	follow symlinks = No

[musicas]
	comment = musicas t_virus
	path = /home/t_virus/Música
	read only = No
	create mask = 0765

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon
	locking = No
	share modes = No

[profiles]
	comment = User Profiles
	path = /var/samba/profiles
	read only = No
	create mask = 0600
	directory mask = 0700
	browseable = No
	locking = No

[pdf-documents]
	comment = Converted PDF Documents
	path = /home/pdf-documents
	read only = No
	guest ok = Yes

[/home/tvirus]
	comment = partilha pasta pessoal
	path = /home/tvirus
	invalid users = guest
	force user = t_virus
	force group = t_virus
	read only = No

---

