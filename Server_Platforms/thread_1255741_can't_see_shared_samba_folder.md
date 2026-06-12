---
title: "can't see shared samba folder"
date: 2009-09-01
forum: Server Platforms
---

### Post by Kyroswolf on 2009-09-01
I have Ubuntu Server 9.04 install and setup.  I am using it as a backup for my wife's and mother's photos.  Once it has some larger hard drives I'll use it as a backup server.  

I have FTP working for my mom to upload her photos as she is off site.  For my wife I would prefer a simple shared folder.

I have samba installed.  All computers are members of the same workgroup.  All computers can see each other, except the server.  

How can I make it visible to the network?

I have the below in /etc/samba/smb.conf file but I can't see the /media/store/<user> folder.   I changed the name of the final directory for my wife's privacy.

```
[<user> share]
comment = <user>'s Folder
path = media/store/<user>
browsable = yes
public = yes
writeable = yes
create mask = 0777
```

Anyone see anything obviously wrong?

---

