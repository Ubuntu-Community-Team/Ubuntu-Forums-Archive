---
title: "Samba configuration issues - share do not work"
date: 2011-03-21
forum: Server Platforms
---

### Post by flycast on 2011-03-21
I am running eBox (aka Zentyal) and am having issues with Samba shares.

1) If I create a user (sl24user) and give the user administrative rights and then log in as that user from an XP machine I can browse and see shares but if I try to open the users home directory (automatically shared) then I get a message telling me I don't have permission to use this network resource.

2) I set up a share in the Zentyal directory and gave the user sl24user full adminstrative rights I can browse and open files read only but I cannot make changes. If I create a brand new text document in that shared folder I can open it and make change the first time but after that If I try to open the document again I get a Access is denied message.

Here is my Samba configuration:
> [global]
 workgroup = Eng
 netbios name = sl24
 server string = SL24 file server
 enable privileges = yes
 interfaces = lo,eth0
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
 ldap suffix = dc=sl24
 ldap machine suffix = ou=Computers
 ldap user suffix =  ou=Users
 ldap group suffix =  ou=Groups
 ldap idmap suffix = ou=Idmap
 ldap admin dn = cn=ebox,dc=sl24
 map acl inherit = Yes
 printing = cups

[homes]
 comment = Home Directories
 valid users = %S
 read only = No
 browseable = No
 vfs objects = full_audit vscan-clamav
 vscan-clamav: config-file = /etc/samba/vscan-clamav.conf



[sl24 files]
 comment = test
 path = /home/samba/shares/sl24fileshare
 valid users = "sl24user"
 read list = 
 write list = 
 admin users = "sl24user"
 read only = No
 browseable = Yes
 force create mode = 0660
 force directory mode = 0660
 vfs objects = full_audit vscan-clamav
 vscan-clamav: config-file = /etc/samba/vscan-clamav.conf


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


It seems that Zentyal is misconfiguring my Samba shares? What is wrong with them
?
I am wondering if this is a folder permissions issue?

---

### Post by flycast on 2011-03-21
permissions:

The share that I can browse and open read only...
> sl24fileshare drw-rwx---

The file I created but cannot edit after first creation:
> New Text Document.txt -rwxrw-r--

---

