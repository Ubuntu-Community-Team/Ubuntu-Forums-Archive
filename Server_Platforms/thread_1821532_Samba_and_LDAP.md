---
title: "Samba and LDAP"
date: 2011-08-09
forum: Server Platforms
---

### Post by asai on 2011-08-09
Hi,
I have set up an 10.04 server with Samba and LDAP.
Followed this tread: [http://ubuntuforums.org/showthread.php?t=1683595](http://ubuntuforums.org/showthread.php?t=1683595)

Samba is running.

From a Win7 computer I can browse the network shares when I type in a username and password, not a Samba user however.

When I try to set up the windows workstation to use my new PDC, it refuses with an error: An Active Directory Domain Controller (AD DC) for the domain "HALVORSEN" could not be contacted.

Here is my smb.conf:
```
[global]

#  Customize these entries as needed
#  Replace with your domain name
	workgroup = HALVORSEN

#  Replace with your server name
	netbios name = server1

#  Replace "mydomain" with the workgroup name you're using
	ldap suffix = dc=HALVORSEN
	ldap admin dn = cn=admin,dc=HALVORSEN

#  Roaming profiles enabled. Replace "myserver" to match your netbios name
	logon path = \\server1\profiles\%U\%a
#  No roaming profiles, uncomment
;	logon path =

	
#  Server Information
	server string = SMB Server


#  Specify global admin user, will have root in all shares
;	admin users = 


#  PW Backend
	obey pam restrictions = Yes
	unix password sync = no
	ldap passwd sync = yes
	passdb backend = ldapsam:ldap://localhost
	pam password change = Yes


#  SMBLDAP Scripts
	add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
	add user script = /usr/sbin/smbldap-useradd -m '%u'
	add machine script = /usr/sbin/smbldap-useradd -w '%u'
	add group script = /usr/sbin/smbldap-groupadd -p '%g'
	delete group script = /usr/sbin/smbldap-groupdel '%g'
	delete user script = /usr/sbin/smbldap-userdel %u
	delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
	set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'


#  LDAP Configuration
	ldap ssl = no
	ldap user suffix = ou=Users
	ldap machine suffix = ou=Computers
	ldap group suffix = ou=Groups
	ldap idmap suffix = ou=Idmap


#  Logon script located in netlogon share. Individual logon scripts uncomment
	;logon script = %U.bat
	logon script = allusers.bat


#  Logging
	max log size = 1000
	syslog = 0
	log file = /var/log/samba/log.%m


#  Printing
	printing = cups
	printcap name = cups
	load printers = yes


# Domain Controller
	domain master = Yes
	domain logons = Yes
	wins support = true
	os level = 35
	server signing = auto
	server schannel = Auto
	panic action = /usr/share/samba/panic-action %d
	dns proxy = No
;	logon drive = H:
;	logon home = \\%N\%U


# Allow file permissions change to group members
	acl group control = yes


# Inherit permissions from parent
; 	inherit acls = yes
; 	inherit owner = yes
;	map acl inherit = yes
; 	inherit permissions = yes


# Do NOT inherit permissions from parent
	inherit acls = no
	inherit owner = no
	map acl inherit = no
	inherit permissions = no


# Do not show files that are unreadable
	hide unreadable = yes

[printers]
   comment = All Printers
   path = /var/spool/samba
   browseable = no
# to allow user 'guest account' to print.
   guest ok = yes
   writable = no
   printable = yes
   create mode = 0700

[Home]
	security mask = 0770
	writeable = yes
	path = /home/userhome
	force security mode = 0
	force directory security mode = 0
	directory security mask = 0770

[netlogon]
	comment = Network Logon Service
	writeable = yes
	public = yes
	path = /home/netlogon

[profiles]
	browseable = no
	printable = no
	writable = yes
	path = /home/profiles
	store dos attributes = no
	guest ok = no
	comment = Users Profiles
# fixes everyone having read
	create mode = 0700
	directory mode = 0700
```
Any suggestions?

---

