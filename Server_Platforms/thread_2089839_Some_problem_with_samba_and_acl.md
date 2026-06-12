---
title: "Some problem with samba and acl"
date: 2012-11-30
forum: Server Platforms
---

### Post by ddimitrov on 2012-11-30
Hello,
I have network with Domain Controller using Server 2008 and Ubuntu 12.04 LTS server. I want to use the ubuntu box for file server with AD integration. I make the integration with winbind and setup acl support. Everything here is ok. I have problems with permissions for newly created files and folders on samba shares. Here is the idea: i want to have one shared folder [IT] with some stuff in it. In the AD i have two security groups: IT and FileserverITAdmins. I want to allow all users from IT to read the files in the folder and all users from FileserverItAdmins to write files and folders. Here is my smb.conf:
############################
#GLOBAL PARAMETERS
[global]
   workgroup = MYDOMAIN
   realm = AD.MYDOMAIN.BG
   preferred master = no
   server string = MYDOMAIN File Server
   security = ADS
   encrypt passwords = yes
   log level = 3
   log file = /var/log/samba/%m
   max log size = 50
   printcap name = cups
   printing = cups
   winbind enum users = Yes
   winbind enum groups = Yes
   winbind use default domain = Yes
   winbind nested groups = Yes
   winbind separator = +
   idmap uid = 10000-20000
   idmap gid = 10000-20000
   ;template primary group = "Domain Users"
   template shell = /bin/bash

[IT]
path = /fserv/departments/IT
available = yes
browsable = yes
writeable = yes
nt acl support = yes
##########################

On the filesystem i make:

chown adminuser:it IT/ -R
chmod 750 IT/ -R
 setfacl -Rm g:FileserverItAdmins:rwx,g:IT:rx,o:---,d:g:FileserverItAdmins:rwx,d:g:IT:rx IT/

With these settings now I have:
# file: IT/
# owner: adminuser
# group: it
user::rwx
group::r-x
group:it:r-x
group:fileserveritadmins:rwx
mask::rwx
other::---
default:user::rwx
default:group::r-x
default:group:it:r-x
default:group:fileserveritadmins:rwx
default:mask::rwx
default:other::---

Now I make from my wokstation new folder with user from FileserverItAdmins and the folder is with these permisions:

# file: New folder/
# owner: ddimitrov
# group: domain\040users
user::rwx
group::rwx
group:it:r-x
group:fileserveritadmins:rwx
mask::rwx
other::---
default:user::rwx
default:group::r-x
default:group:it:r-x
default:group:fileserveritadmins:rwx
default:mask::rwx
default:other::---

So users from the limited IT group now can create files in ti.
Where is my mistake? I play around 4 hours with this and I need some help.

---

