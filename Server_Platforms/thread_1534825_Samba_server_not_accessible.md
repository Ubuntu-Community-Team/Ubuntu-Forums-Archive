---
title: "Samba server not accessible"
date: 2010-07-20
forum: Server Platforms
---

### Post by phillies on 2010-07-20
Hi,

I have a problem with the samba server on my ubuntu 10.10 computer. I want to add a samba share which shall be accessed from windows 7. I installed samba and tried to connect to the computer but the connection gets rejected "Bad username and/or password" says Windows but the samba log says:
```
[2010/07/20 09:56:46.495176,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2010/07/20 09:56:46.495261,  0] lib/util_sock.c:1432(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
```
Username and password are correct and I can access samba shares on many other linux machines from the windows computer, so the problem is somewhere on the ubuntu 10.10 machine.

Samba config is the default config, I just tried to access \\servername

edit: I tried the "smp port = 139" workaround some people posted, but it didn't change anything.

edit2: I copied the smb.conf from a different server where I can connect to (but running 10.4 not 10.10) and I still cannot connect. I restarted samba so there seems to be a bug somewhere else.

---

### Post by spynappels on 2010-07-20
Windows 7 automatically tries to use a domain.

If you escape the username, (put a / before the username) it should work.

---

### Post by phillies on 2010-07-20
As I said: Windows works fine with several other linux servers all using the same login. The Ubuntu 10.10 server rejects domain users as well as local users. And since I used the identical smb.conf from a working server I'd say it's not samba or it's because 10.10's samba (3.5.4) has some different default values than 10.04's samba (3.4.7).

---

### Post by spynappels on 2010-07-20
Ubuntu 10.10? That is not due for release until October. Is it a beta you are using?

---

### Post by tr1pl3x on 2010-07-20
Can you please post your smb.conf file. so that we can see whats causing the problem. by the way did you already created a smb user by using the smbpasswd -a username?

---

### Post by phillies on 2010-07-21
> **spynappels said:**
> Ubuntu 10.10? That is not due for release until October. Is it a beta you are using?
Yes, works WAY better than 10.4 - except samba :D

Here's my smb.conf. It's the ubuntu default conf except for the "share" share.
```
[global]
   workgroup = WORKGROUP
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes

[share]
   browsable = no
   path = /somewhere
   read only = no
   guest ok = no
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

Why should I create a samba specific user? On my other server (the 10.4 server) samba used the local user accounts (via PAM?) by default and this should be the case here too.

---

### Post by phillies on 2010-07-27
No idea? Man, this is lame :(

---

### Post by thomas_d_j on 2010-08-08
A couple of things to check / try:

*set ***domain master = yes ***in smb.conf*

make sure your user ID is a member of the group "users":
groups *yourusername*

make sure you have set your samba password:
sudo smbpassw -a *yourusername*

---

