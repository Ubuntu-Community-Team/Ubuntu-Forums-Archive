---
title: "Some net rpc commands dont work"
date: 2006-11-20
forum: Server Platforms
---

### Post by peter@kkvs on 2006-11-20
Have Ubuntu 6.06.01 with samba, smbclient smbfs, openssh, swat, netkit-inetd installed.

It is run as a standalone server for a network of xp machines.

I want to give some rights to a technician to add/remove users, do backups and a few other things.
The only way I can see to do this is by giving this guy domain privileges as per net rpc rights grant etc.
I have mapped linux admin group to nt domain admins group and linux users to domain users but cannot grant the indiviual rights to the domain admins group. 

relevant items from smb.conf
enable privileges = yes
obey pam restrictions = yes
passwd backend = tdbsam
pam passwd change = yes
unix passwd sync = yes
wins support = yes
dns proxy = no

When the command:
sudo net rpc rights grant "Domain Admins" \ SeMachineAcountPrivilege \ etc \ etc -S *fileserver* -Uroot%not24get
is issued then the response varies depending on the final segment 
-U% produces error message:
failed to grant privileges (NT_STATUS_ACCESS_DENIED)

-Uroot%not24get gives error username or passwd not correct
-Uroot%*rootpasswd* (actual - even though it is is very bad leaving password in command history, it will dissappear when I add in another 100 users) but I had to try it. 
this gave: 
failed to grant privileges for domain admins (NT_STATUS_NO_SUCH_PRIVILEGE)

So does this mean it has to be a domain server to grant these rights and if so how do you give limited admin rights on a standalone server ?

---

### Post by ingo on 2006-11-22
you might be better off asking in a samba specific forum since this is distro independent stuff.

just a suggestion seeing there are no answers as yet...

---

### Post by peter@kkvs on 2006-11-22
That would certainly seem logical. Unfortunately samba on ubuntu is not the ssame as samba on redhat or any other distro so there is always the chance that the problem lies in modifications made by ubuntu.
Things that obviously work on most distros dont always work on ubuntu - hence this post

---

