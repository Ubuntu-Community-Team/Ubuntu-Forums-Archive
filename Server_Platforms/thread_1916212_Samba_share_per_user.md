---
title: "Samba share per user"
date: 2012-01-27
forum: Server Platforms
---

### Post by kalosh on 2012-01-27
Hello.
Is it possible to configure samba to automatically create shares for each (system) user (//server/userShare)? Do I have to create custom script which creates share for user and (somehow) inject it into system to listen user creation events (after useradd or adduser)?
Best regards, Dawid.

---

### Post by Morbius1 on 2012-01-27
There already is such a thing in smb.conf - it's just commented out. 

Uncommented it looks something like this:
> [homes]
comment = Home Directories
valid users = %S
read only = No
create mask = 0700
directory mask = 0700
browseable = NoIt doesn't work like a normal samba share though. It's not a browseable share ( you will notice there is no path in the share definition). The Linux client would access the share by name:
```
smb://server/user-name
```When he does it will create a samba share "on-the-fly" of his corresponding home directory on the server.

You can also set this up so that you don't have to have a home directory by setting up a separate directory say .. /home/Samba-Servername. Then have the [homes] share specify that parent directory:
> [homes]
comment = Home Directories
[COLOR=Blue]path = /home/Samba-Servername/%S[/COLOR]
valid users = %S
read only = No
create mask = 0700
directory mask = 0700
browseable = NoYou would then have to create sub-directories named for every remote user ... /home/Samba-Servername/morbius, etc ...
[COLOR=Blue]EDIT[/COLOR]: you would also have to change ownership of the named subdirectory.

---

### Post by kalosh on 2012-01-28
Hey.
Thanks for the replay. It is working like a charm:)
Best regards, Dawid.

---

