---
title: "[SOLVED] Samba share - permission denied opening files"
date: 2008-11-07
forum: Server Platforms
---

### Post by Lumme on 2008-11-07
Hi. I'm pretty new to samba. I'm trying to setup a shared folder on my local network (later on trying to access it from VPN). So far I have managed to get a share working and granting access to users from a specific group (drb). My problem now is that when user1 tries to open a file created by user2 he gets "permission denied". Both users are member of "drb".
My setup:
Server: Ubuntu 8.10 Server running samba and openvpn
Clients: Windows XP Professional

I created user1 and user2 as local users on the server, added them to group "drb" and used "smbpasswd" to assign samba-passwords

Here is my smb.conf
```

#======================= Global Settings =====================================
[global]

# workgroup = NT-Domain-Name or Workgroup-Name, eg: MIDEARTH
   workgroup = drb-test

# server string is the equivalent of the NT Description field
   server string = Samba Server

# Security mode. Defines in which mode Samba will operate. Possible 
# values are share, user, server, domain and ads. Most people will want 
# user level security. See the Samba-HOWTO-Collection for details.
   security = user

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = no

# this tells Samba to use a separate log file for each machine
# that connects
   log file = /usr/local/samba/var/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 50

interfaces = tun0 eth1

# DNS Proxy - tells Samba whether or not to try to resolve NetBIOS names
# via DNS nslookups. The default is NO.
   dns proxy = no 

#============================ Share Definitions ==============================
[projekt]
   comment = DRB Projektmappe
   path = /drb
   valid users = @drb
   public = no
   writable = yes
   create mode = 770
   directory mode = 660

```

I have chgrp /drb to group drb and chown /drb to user1.

Hope someone can figure it out.:)

---

### Post by gpsmikey on 2008-11-07
couple of things (from my limited experience with Samba) to check.  Understand that both the regular Linux permissions and the samba permissions apply with the most restrictive controlling -- if Samba says it is writeable, but the Linux permissions don't permit writing by that user, then no write will occur.  You might want to check out a link I have found very helpful -- the "Samba 3 by example" has lots of good information as well as examples of configurations that work.  The book is available from places like Amazon, but you can get the pdf version here:
[http://www.samba.org/samba/docs/Samba3-ByExample.pdf](http://www.samba.org/samba/docs/Samba3-ByExample.pdf)
Grab a copy of it - well worth the disk space :)

One trick I have used for checking things is to create a directory somewhere with 777 permissions on it that is available to the user in question.  Have the user in question "touch" a file there and use ls -l to see who the system thinks that user is and which group they belong to.  Every now and then, it turns up something unexpected !!

mikey


mikey

---

### Post by Lumme on 2008-11-08
> **gpsmikey said:**
> 

One trick I have used for checking things is to create a directory somewhere with 777 permissions on it that is available to the user in question.  Have the user in question "touch" a file there and use ls -l to see who the system thinks that user is and which group they belong to.  Every now and then, it turns up something unexpected !!
mikey

Thanks mikey. one thing I didn't see from my windows machines. when user1 creates af file it is owned by group "user1". Any idea how to force it to be the "drb" group instead.

---

### Post by Lumme on 2008-11-09
okay. managed to solve the problem.
usermod -g drb user1 and usermod -g drb user2 did the trick

---

