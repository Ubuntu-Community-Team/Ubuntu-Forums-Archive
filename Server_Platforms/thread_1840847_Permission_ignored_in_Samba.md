---
title: "Permission ignored in Samba"
date: 2011-09-08
forum: Server Platforms
---

### Post by marcomy on 2011-09-08
Hello I have this problem : I can mount successfully a filesystem using this line in my fstab:

//172.17.**.**/procsys3 /procsys3          cifs       username=***,password=***,user,noauto,rw,iocharset=utf8,uid=***,gid=4311,dir_mode=0775,file_mode=0777   0 0

but when I create a new file its permissions are always the same regardless of what I put as file_mode.

I tried various combinations of options...

Can someone understand what could be failing?

Thanks a lot!

---

### Post by Doug S on 2011-09-08
Samba file and directory creation permissions are definedi n the smb.conf file. Look for and area similar to this:
```
 
# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
#  create mask = 0744
   create mask = 0644
# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
#  directory mask = 0744
   directory mask = 0755
 

```
And change the permissions to what you want or need for your application.
smb.conf should be in /etc/samba, and you should make a backup copy first.
You will need sudo prefix to edit.
Remember to re-start samba for the changes to take effect.
```
 
sudo restart smbd
sudo restart nmbd

```

---

