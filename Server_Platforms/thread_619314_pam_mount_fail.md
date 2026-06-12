---
title: "pam_mount fail"
date: 2007-11-21
forum: Server Platforms
---

### Post by davidegn82 on 2007-11-21
I want utilize the pam_mount  module on client Ubuntu Gusty.

This is my scenario:
Domain name: mydomain.org
Server Name: myserver
Type of server: Active Directory on win2003 Server
Share Name: Sistema_Server

my goal: mount the share "System_server/Domain/Data_User"  in local path "/mnt/Data_User"

My Configuration /etc/security/pam_mount.conf

volume * smbfs myserver System_Server/Domain/Data_User /mnt/Data_User uid=&,gid=&,dmask=0751,workgroup=MYDOMAIN

After the login, the mount don't found.

In log auth, there is the following error:

pam_mount(readconfig.c:155) bad number of args for volume

What is wrong in my configuration?

Thanks

---

### Post by cmdln on 2008-02-18
You might try sticking two "-" on the end of your volume line.
volume * smbfs myserver System_Server/Domain/Data_User /mnt/Data_User uid=&,gid=&,dmask=0751,workgroup=MYDOMAIN - -

---

