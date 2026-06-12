---
title: "Active Directory, Samba &amp; Likewise"
date: 2008-08-22
forum: Server Platforms
---

### Post by RandomJon on 2008-08-22
First of all I'd like to thank the posters of this thread -> [http://ubuntuforums.org/showthread.php?t=761464](http://ubuntuforums.org/showthread.php?t=761464) who's information helped me greatly.

However I still have an issue with my samba, likewise & active directory configuration.

The server in question is sharing filestores with a windows based network and in particular a 2003 domain controller. 

I have succesfully gotten likewise running for ssh login and for connecting to the samba shares BUT I cannot make it respect the permissions for writing. 

So my domain user can connect to the share, see the files, but it cannot see the permissions (reporting S-1-0-0 and Everyone as having special permissions but noone else) and cannot write files.

If I add an "admin user" directive to the smb.conf it allows me to do everything but i'd like to be able to control which folders can be written to by certain domain groups.

The client is Windows Vista and this is with Ubuntu 8.04.01.

I think this is an issue with likewise as my simple samba share (using user security mode) on another server works fine, can read permissions, write etc. But it doesnt need to be domain authenticated.

smb.conf shown below
========================
[global]

#likewise config
security  = ADS
workgroup = OURDOMAIN
realm     = OURDOMAIN.LOCAL

idmap backend = lwopen
idmap uid     = 50-9999999999
idmap gid     = 50-9999999999

#config
server string = %h server (Samba, Ubuntu)
wins server = genesys1.genesys.local
dns proxy = no

interfaces = eth0 lo
bind interfaces only = true

log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0

panic action = /usr/share/samba/panic-action %d

encrypt passwords = true

passdb backend = tdbsam
obey pam restrctions = yes
invalid users = root
unix password sync = no
pam password change = no

[srv]
path = /srv/
comment = Test
browseable = no

valid users = @OURDOMAIN\systems
#admin users = @OURDOMAIN\systems

writable = yes
create mask = 0775
directory mask = 0775

---

### Post by RandomJon on 2008-08-28
As per my later post my problem is actually the fact that samba isn't respecting a users secondary groups when it comes to checking permissions.

Anyone got any idea whats wrong?

---

### Post by likeWiseGuy on 2008-10-02
> **RandomJon said:**
> As per my later post my problem is actually the fact that samba isn't respecting a users secondary groups when it comes to checking permissions.

Anyone got any idea whats wrong?

Hi, RandomJon.

Let me see if I can assist with your Samba & Active Directory integration on your Ubuntu box here... 

Likewise actually has a guide for Samba 3 integration that may be very helpful for you: [http://likewisesoftware.com/resources/user_documentation/Likewise-Samba-Guide.pdf](http://likewisesoftware.com/resources/user_documentation/Likewise-Samba-Guide.pdf)

First, you'll probably need to make some edits to your smb.conf file. Also note that lwicompat_vXX plugins are not built by default in the native ubuntu packages.

Let me know how things are going and if you need more info.

Thanks.

---

