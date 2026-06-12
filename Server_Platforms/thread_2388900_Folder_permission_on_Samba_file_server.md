---
title: "Folder permission on Samba file server"
date: 2018-04-09
forum: Server Platforms
---

### Post by alvinguo on 2018-04-09
Hey guys,

I prepared Samba file server on ubuntu server, but I just got an issue with private share folder permission. The following points are my goal.
Private share place has been created in both conf and linux folder, that private folder is invisible to other user, but if other Samba user logged his account to his private folder, he can just change the \\IP\userA address to check the file inside. I don't want to allow them to do that. I tried to modify the folder with 700 role, but that private folder owner also couldn't login that place. 

[LIST]
[*]Samba share place for only one user A
[*]Only this user can see this folder and make file operation
[*]Other Samba user couldn't see and read this share folder even they know the path.
[/LIST]

Here is my parameters
smb.conf
comment = user a's space
path = /home/share/private/username
valid user = user a
writeable = yes
guest ok = no
browsable = no

---

### Post by Morbius1 on 2018-04-09
> valid user = user a
It's not "valid user" it's "valid users" with an s at the end.

If you run this command on the server it will tell you what happened:
```
testparm -s
```
It should come back with something like:
> Unknown parameter encountered: "valid user"
Ignoring unknown parameter "valid user"
Without that parameter present your share will be accessible to anyone with credentials.,

---

