---
title: "Change computer name field property to the mounted computer name"
date: 2012-01-09
forum: Server Platforms
---

### Post by jessguynn on 2012-01-09
My setup: Ubuntu box that shares to windows machines using samba. I integrated and made the Ubuntu box member of the windows 2008 domain using winbind and PAM so when I connect with a windows computer the domain users takes the ownership instead of Linux users. But what i want to do is also change the computer name property/attribute to the computer name that mounted the shared directory and created the sub-directories and files. For example, if windows computer named winpc created a file in the ubuntu box, the computer name field should not be named under the ubuntu box but winpc.  Can this be done through smb.conf parameters, scripts in the Ubuntu side, or Windows registry?  By smb.conf is below

#GLOBAL PARAMETERS
[GLOBAL]
 
   workgroup = ARCH
   realm = ARCH.LOCAL
   netbios name = ARCHPROJ
   password server = 192.168.1.40
   preferred master = no
   server string = %h server (Samba %v, Ubuntu)
   encrypt passwords = true
   enable privileges = Yes
   dns proxy = no
   log level = 3
   log file = /var/log/samba/%m
   max log size = 50
   security = ADS
   printcap name = cups
   printing = cups
   winbind enum users = Yes
   winbind enum groups = Yes
   #winbind nested groups = Yes
   winbind separator = +
   idmap uid = 600-20000
   idmap gid = 600-20000
   ;template primary group = "Domain Users"
   template homedir = /home/%D/%U
   template shell = /bin/bash

[WORKSPACE]
   comment = Home Direcotries
   path = /home/ARCH/administrator/Workspace
   valid users = @"ARCH+domain users"
   read only = No
   browseable = yes
   writable = yes

---

