---
title: "strange error on ubuntu 10.04 with samba as a PDC and openLdap"
date: 2011-02-28
forum: Server Platforms
---

### Post by gjergj.sheldija on 2011-02-28
hi everybody,

i'm having a strange error on ubuntu 10.04. i configured samba as a pdc, configured openldap so i could store samba users on ldap.
they communicate perfectly together, when i try to add a machine to the domain i got a message from winxp like the user name cannot be found, when i check ldap the machine is there..
on the logs i can't see nothing except authentication succeed..so no errors there..
after a week working on this thing i'm really stuck..
any idea of what could i do ?

smb.conf
```

[global]
   workgroup = BUSH
   server string = %h server (Samba, Ubuntu)
   wins support = yes
   dns proxy = no
   interfaces = eth1, lo
   bind interfaces only = yes
   log file = /var/log/samba/log.%m
   log level = 2
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   passdb backend = ldapsam:ldap://127.0.0.1/
   obey pam restrictions = yes
   pam password change = yes
   map to guest = bad user
   domain logons = yes
   preferred master = yes
   os level = 255
   local master = yes 
   domain master = yes
   login path = \\%N\%U\profile
   logon drive = H:
   logon home = \\%N\%U
   logon script = logon.cmd
	add user script = /usr/sbin/smbldap-useradd -m '%u'
	delete user script = /usr/sbin/smbldap-userdel %u
	add group script = /usr/sbin/smbldap-groupadd -p '%g'
	delete group script = /usr/sbin/smbldap-groupdel '%g'
	add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
	delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
	set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'
    add machine script = smbldap-useradd -w -d /dev/null -c 'Machine Account' -s /bin/false '%u'

	ldap admin dn = cn=admin,dc=bush,dc=lan
	ldap group suffix = ou=Groups
	ldap idmap suffix = ou=Idmap
	ldap machine suffix = ou=Computers
	ldap passwd sync = yes
	ldap suffix = dc=bush,dc=lan
	ldap ssl = no
	ldap user suffix = ou=Users

   idmap uid = 10000-20000
   idmap gid = 10000-20000
   template shell = /bin/bash

   usershare allow guests = yes

[homes]
   comment = Home Directories
   browseable = no
   read only = yes
   create mask = 0700
   directory mask = 0700
   valid users = %S

[netlogon]
   comment = Network Logon Service
   path = /samba/home/netlogon
   guest ok = yes
   read only = yes
   share modes = no

[profiles]
   comment = Users profiles
   path = /samba/home/profiles
   guest ok = no
   browseable = no
   create mask = 0600
   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700


[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
```

---

