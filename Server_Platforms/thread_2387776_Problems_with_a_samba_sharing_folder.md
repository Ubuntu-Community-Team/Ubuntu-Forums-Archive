---
title: "Problems with a samba sharing folder"
date: 2018-03-23
forum: Server Platforms
---

### Post by dam034 on 2018-03-23
Dear users,

in my LAN server I have samba to share in LAN the files.

All folders/sharings created until yesterday are working correctly. Today I created a new folder in my filesystem and a new sharing in samba:
```
root@myserver:/srv/samba# ls -ahl
totale 64K
drwxrwxr-x  8 peter  admin 4,0K mar 22 12:31 .
drwxr-xr-x 11 root     root  4,0K mar 22 17:28 ..
drwxrwx--- 30 retropie admin 4,0K mar 23 17:17 retropie
drwxrwxrwx  2 peter  admin 4,0K mar 23 17:19 scrittura
drwxrwxr-x  3 peter  admin 4,0K feb  1 17:00 servizio
drwxrwxr-x  7 peter  admin 4,0K mar 23 17:21 temporanea

```
I want to specify the user peter is member of admin group.
This is smb.conf:
```
[retropie]
available = yes
browseable = yes
path = /srv/samba/retropie
read only = no
public = yes
create mask = 0770
directory mask = 0770

[scrittura]
available = yes
browseable = yes
path = /srv/samba/scrittura
read only = no
public = yes
create mask = 0777
directory mask = 0777

[servizio]
available = yes
browseable = yes
path = /srv/samba/servizio
read only = no
public = yes
create mask = 0775
directory mask = 0775

[temporanea]
available = yes
browseable = yes
path = /srv/samba/temporanea
read only = no
public = yes
create mask = 0775
directory mask = 0775

```
As you can see, "temporanea" and "servizio" are read-only folders, in "scrittura" any user can write, but the problems there are in "retropie".

I want to restrict the access in that folder according with the 770 permissions, then the user "retropie" and the member users of "admin" can login with their password and read/write.

When on a client in LAN I try to mount the folder, I get this error:
```
root@retropie:/tmp# mount -t cifs //192.168.1.2/retropie giochi -o username=retropie,password=mypw,dir_mode=0777,file_mode=0777,iocharset=utf8
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

Where did I wrong?

Please help!

---

