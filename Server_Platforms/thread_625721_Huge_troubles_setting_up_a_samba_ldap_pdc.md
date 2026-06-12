---
title: "Huge troubles setting up a samba ldap pdc"
date: 2007-11-28
forum: Server Platforms
---

### Post by mbuti on 2007-11-28
I can't really understand what's wrong with my configuration, I've tried to follow every guide or manual I found, even looked on log for hours but nothing.

The problem is basically that samba can't bind correctly to the ldap server.

If I do this
ldapsearch -x -D"cn=admin,dc=mura" -W
it works correctly, but when I start samba I get this in slapd.log

Nov 28 15:57:33 server slapd[22857]: conn=593 fd=29 ACCEPT from IP=127.0.0.1:42342 (IP=0.0.0.0:389)
Nov 28 15:57:33 server slapd[22857]: conn=593 op=0 BIND dn="cn=admin,dc=mura" method=128
Nov 28 15:57:33 server slapd[22857]: conn=593 op=0 RESULT tag=97 err=49 text=
Nov 28 15:57:33 server slapd[22857]: conn=593 op=1 UNBIND
Nov 28 15:57:33 server slapd[22857]: conn=593 fd=29 closed

I think the problem must be in the ldap server, I'll post the base
dn: dc=mura
objectClass: top
objectClass: dcObject
objectClass: organization
dc: mura
o: mura
description: mura
structuralObjectClass: organization
entryUUID: a6d7292c-2c92-102c-8688-372be852aaab
creatorsName: cn=admin,dc=mura
createTimestamp: 20071121153202Z
entryCSN: 20071121153202Z#000000#00#000000
modifiersName: cn=admin,dc=mura
modifyTimestamp: 20071121153202Z

I did
smbpasswd -w "password"
and this is the samba configuration

[global]
	workgroup = LCALZITEX
	server string = LAN Server %v
	
##### Per permettere un corretto login dei client XP #####
	wins support = yes
	admin users = Administrator
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	dns proxy = no
	unix charset = ISO8859-1

	### Each machina has its own log file ###
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 8

	panic action = /usr/share/samba/panic-action %d
	
	### Authentication ###
	security = user
	encrypt passwords = true
	passdb backend = ldapsam:ldap://127.0.0.1
	obey pam restrictions = yes
	invalid users = root
	
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sLinux\spassword:* %n\n *Retype\snew\sLinux\spassword:* %n\n .

	##### LDAP Configuration #####

	ldap admin dn = cn=admin,dc=mura
	ldap suffix = dc=mura
	ldap group suffix = ou=Groups
	ldap user suffix = ou=Users
	ldap machine suffix = ou=Computers
	ldap idmap suffix = ou=Idmap
	ldap passwd sync = Yes
	
	##### Samba PDC #####

	os level = 255
	domain master = yes
	domain logons = yes
	preferred master = yes
	time server = yes
	logon home =
	logon path =
	
	socket options = TCP_NODELAY


Please help, I'm going crazy...

---

### Post by sciurus on 2007-11-29
You may want to try installing [Ebox]("http://ebox-platform.com/"); it will will give you a Samba PDC storing users in openldap out of the box. You can download it from [here]("http://ebox-platform.com/get/ebox_installer.iso"). If nothing else you can use it to see working samba and ldap configuration

---

### Post by mbuti on 2007-11-29
Thanks for the hint but that's not the solution for me, that server has to do much more than pdc, and everything else is already working fine.

Now I'm trying with another virtual machine with pdc without ldap backend, just to make some experience

---

### Post by honeydew on 2008-01-02
o thanks I have been looking for a good open source solution for our windows network.. one of the guys here has been pushing for a m$ 2003 server box.. but ebox looks like it may be the solution.

---

### Post by andol on 2008-01-02
mbuti: Just saw this thread now when honeydew bumped it. Have you gotten things working or do you still need assistance?

I remembering banging my head against this same combination about six month ago so I can certainly sympathize :-)

---

