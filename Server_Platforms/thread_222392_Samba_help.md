---
title: "Samba help"
date: 2006-07-24
forum: Server Platforms
---

### Post by ragdemai on 2006-07-24
I having some problem on my samba setup, actually I would like to work my samba as every one can accese but only same user can be write on my samba server, other user can read & execute only.

below is my configuration in smb.conf
================================================== ===============
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
================================================== ===============
I can't see any problem on this setup, when I use the account in group user.

but it wont work, I can copy anything in the samba folder(i'm using the group account to log in).

thankx

---

### Post by dtfinch on 2006-07-25
I'm not completely sure what you're trying to say, but I'll give it a try.

writable = no
That might override the "write list = @group", though I'm not sure.

create mask = 0765
directory mask = 0765
The 6 says that anyone in the group can modify any files created by anyone else in the group. 

invalid users = root
I think that gives everyone who fails to log in successfully root access, so that permissions are meaningless. invalid users=nobody should let them view any files that are accessible to anyone, without letting them write.

The !'s in the share name also seem a little odd.

---

### Post by ragdemai on 2006-07-25
> **dtfinch said:**
> I'm not completely sure what you're trying to say, but I'll give it a try.

writable = no
That might override the "write list = @group", though I'm not sure.

create mask = 0765
directory mask = 0765
The 6 says that anyone in the group can modify any files created by anyone else in the group. 

invalid users = root
I think that gives everyone who fails to log in successfully root access, so that permissions are meaningless. invalid users=nobody should let them view any files that are accessible to anyone, without letting them write.

The !'s in the share name also seem a little odd.


Thankx for your reply, actually what I want is I 2 kind of users, 1 is the users is the group can be read & write anythink is the samba server, & another 1 is user not in the list but they no need to type password to accece this samba server but they can only read in this samba server.  
Maybe you are right. I should chang change writable = yes.

---

