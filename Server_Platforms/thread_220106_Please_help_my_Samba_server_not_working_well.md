---
title: "Please help my Samba server not working well"
date: 2006-07-21
forum: Server Platforms
---

### Post by ragdemai on 2006-07-21
I having some problem on my samba setup, actually I would like to work my samba as every one can accese but only same user can be write on my samba server, other user can read & execute only.

below is my configuration in smb.conf
=================================================================
[global]
   workgroup = workgroup
   browseable = true
   server string = %h Files Server 2
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   security = share
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   socket options = TCP_NODELAY

[Go!Go!Go!]
   comment = Home Directories
   browseable = yes
   path = /home/Shared
   writable = no
   write list = @group
   guest ok = yes
   create mask = 0765
   directory mask = 0765
=================================================================
I can't see any problem on this setup, when I use the account in group user.

but it wont work, I can copy anything in the samba folder(i'm using the group account to log in).

thankx

---

