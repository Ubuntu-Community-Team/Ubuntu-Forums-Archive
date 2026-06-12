---
title: "Lock down SAMBA share"
date: 2007-02-07
forum: Server Platforms
---

### Post by Tamerz on 2007-02-07
Hello, I am using a Ubuntu Server 6.06 for a file server. All the file server needs to do is have a SAMBA share for three Windows servers to backup to. The Ubuntu server is on the Windows domain using winbind (I can log in as domain users) but I can't figure out how to set a SAMBA share to only be accessed by specific domain users. I only want domain admins to be able to access the share. Any help would be appreciated.

EDIT: I have gotten further. I forgot the equal sign in "valid users = username" 

The main question I have now is UNIX permissions on the directory in question. Right now I just have it chmod 755 since I have no idea who should own it.

SOLVED: I realized you could do a:
```
chown "DOMAIN\username" /directory 
```

---

