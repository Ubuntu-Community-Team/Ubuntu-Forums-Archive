---
title: "Samba folder sharing problem"
date: 2008-03-30
forum: Server Platforms
---

### Post by hmhmhm on 2008-03-30
Hi,
My smb.conf on the server includes:

```
...
[public]
path = /home/public
comment = Shared folders
guest ok = yes
create mode = 2777
create mask = 2777
directory mask = 2777
browseable = yes
public = yes
read only = no
...
```
My client includes in fstab:

```
//192.168.2.10/public /mnt/public cifs rw,domain=workgroup,username=user,passwd=pwd,uid=user,gid=nogroup,dir_mode=777,file_mode=777 0 0
```

My problem is that when I create a new folder on this public drive, the folder permissions are drwxr-xr-x i.e. only I can create subfolders into that folder. I would like to change this so other users can also create/delete subfolders.
Thanks for your help,

hmhmhm

---

