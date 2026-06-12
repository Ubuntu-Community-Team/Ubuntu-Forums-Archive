---
title: "Windows printer driver for networked printer"
date: 2010-10-23
forum: Server Platforms
---

### Post by BarryDocks on 2010-10-23
I have set up a PDC with Zentyl but I am having problems with the widndows XP printer drivers

I am trying to upload windows printer drivers files to samba print$ share as per these instructions:
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/classicalprinting.html#id2627627](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/classicalprinting.html#id2627627)

This is successful in that the files are in /var/libs/samba/printers

the problem is that when I install the printer on the XP client it does not automatically install the drivers from the server, instead I offered the default list of printers to choose from.

Any suggestion would be warmly welcome!

Here are the salient parts of the smb.config:

```
[global]
 workgroup = test.lan
 netbios name = ubuntu
 server string = Zentyal File Server
 enable privileges = yes
 interfaces = lo,bond0
 bind interfaces only = Yes
 passdb backend = ldapsam:ldapi://%2fvar%2frun%2fslapd%2fldapi
 ldap ssl = Off
 log level = 1
 syslog = 0
 log file = /var/log/samba/%m
 max log size = 50
 vfs objects = full_audit
 full_audit:success = connect opendir open disconnect unlink mkdir rmdir rename
 full_audit:failure = none
 smb ports = 137 138 139 445
 name resolve order = wins bcast hosts
 time server = Yes
 printcap name = CUPS
 wins support = Yes
 dns proxy = Yes
 ldap suffix = dc=ubuntu,dc=cable,dc=virginmedia,dc=net
 ldap machine suffix = ou=Computers
 ldap user suffix =  ou=Users
 ldap group suffix =  ou=Groups
 ldap idmap suffix = ou=Idmap
 ldap admin dn = cn=ebox,dc=ubuntu,dc=cable,dc=virginmedia,dc=net
 map acl inherit = Yes
 printing = cups

 encrypt passwords = Yes
 obey pam restrictions = No
 ldap passwd sync = Yes
 mangling method = hash2

 logon script = logon.bat
 logon drive = H:
 logon home =
 logon path =

 domain logons = Yes
 os level = 65
 preferred master = Yes
 domain master = Yes
 add user script = /usr/sbin/smbldap-useradd -m "%u"
 ldap delete dn = Yes
 add machine script = /usr/sbin/smbldap-useradd -w "%u"
 add group script = /usr/sbin/smbldap-groupadd -p "%g"
 add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
 delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
 set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"

[netlogon]
 path = /home/samba/netlogon/
 browseable = No
 read only = yes

[profiles]
 path = /home/samba/profiles
 read only = no
 create mask = 0600
 directory mask = 0700
 browseable = No
 guest ok = Yes
 profile acls = yes
 csc policy = disable
 valid users = %U
 admin users = @"Domain Admins"
 hide files = /desktop.ini/outlook*.lnk/*Briefcase*/


[homes]
 comment = Home Directories
 valid users = %S
 read only = No
 browseable = No
 vfs objects = full_audit vscan-clamav recycle
 vscan-clamav: config-file = /etc/samba/vscan-clamav.conf
 recycle: versions = Yes
 recycle: repository = RecycleBin
 recycle: keeptree = Yes
 recycle: excludedir = /tmp|/var/tmp
 recycle: directory_mode = 0700


[Brother_HL-2030_series]
 path  = /var/spool/samba
 read   only   =    yes
 printable     =    yes
 valid users   = "smbadmin" "testuser" 
# guest ok = yes

[sambatest]
 comment = sambatest
 path = /home/samba/shares/sambatest
 guest only = yes
 guest ok = yes
 read only = No
 browseable = Yes
 force create mode = 0660
 force directory mode = 0660
 vfs objects = full_audit vscan-clamav recycle
 vscan-clamav: config-file = /etc/samba/vscan-clamav.conf
 recycle: versions = Yes
 recycle: repository = RecycleBin
 recycle: keeptree = Yes
 recycle: excludedir = /tmp|/var/tmp
 recycle: directory_mode = 0700


[ebox-internal-backups]
 path = /var/lib/ebox/conf//backups
 read only = No
 valid users = @"Domain Admins"
 admin users = @"Domain Admins"
 force group = ebox
 force user = ebox
 browseable = Yes

[ebox-quarantine]
 path = /var//lib/ebox/quarantine
 read only = No
 valid users = @"Domain Admins"
 admin users = @"Domain Admins"
 browseable = Yes

[print$]
 comment = Printer Drivers
 path = /var/lib/samba/printers
 browseable = yes
 read only = yes
 guest ok = no
 write list = @"Domain Admins"
 use client driver = no
 valid users = "@Domain Users"

 @"Domain Admins"
 use client driver = no
 valid users = "@Domain Users"

```

---

### Post by HermanAB on 2010-10-23
Howdy,

Your printer is on a Linux server?

CUPS make ALL printers look like postscript printers.  Therefore, when you install the printer on XP, simply select an Apple Laser Writer II as the printer type.  That will give you basic printer functionality, without having to search for a fancy driver.

---

### Post by sourchier on 2010-10-23
Are the permissions for the share OK? Did you use the rpcclient command-line utility once with the adddriver command--then used the rpcclint command with the subcommand setdriver?

---

### Post by BarryDocks on 2010-10-24
Thanks for the fast replies.

> **HermanAB said:**
> Howdy,

Your printer is on a Linux server?

CUPS make ALL printers look like postscript printers.  Therefore, when you install the printer on XP, simply select an Apple Laser Writer II as the printer type.  That will give you basic printer functionality, without having to search for a fancy driver.
Yes the printer is on the ubuntu 10.04 server.  I have tried the cuppsaddsmb command and the postscript drivers in the past but I allways fing there is a page layout issue when printing from windows. - this might be due to to the post script drivers being set up for US Letter size paper and I want A4?

> **sourchier said:**
> Are the permissions for the share OK? Did you use the rpcclient command-line utility once with the adddriver command--then used the rpcclint command with the subcommand setdriver?

No I used the windows add printer system.  I think there is something in my smb.conf that is the problem - this is automatically produced by zentyl?

---

### Post by sourchier on 2010-10-29
What does /etc/cups/cupsd.conf look like on your box? Can you pull up a browser on Zentyl and type in [http://localhost:631](http://localhost:631)

Are you blocking your samba shares and netbios with a firewall.

---

