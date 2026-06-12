---
title: "not a valid block device?"
date: 2006-06-21
forum: Server Platforms
---

### Post by tronica on 2006-06-21
Ok. i'm runngin dapper, and i use this command to connect to my windows servers

> sudo mount -t cifs //192.168.1.65/server /mnt/server -o user=Administrator,pass=monster

and it works great. So i set up a server with debian and i installed samba. And i'm using this config in my smb.conf.

> 
[share]
path = /home/lyle/Desktop/share
public = yes
writable = yes
valid users = lyle


then when i try to mount it from my ubuntu box i get

> lyle@ubuntu:/mnt$ sudo mount -t cifs //192.168.1.68/share/ /mnt/debserv -o user=lyle,pass=monster
mount: //192.168.1.68/share/ is not a valid block device


can anyone help me get this going. Thanks

---

### Post by cyracks on 2006-06-21
[quote=tronica]
path = /home/lyle/Desktop/share
[/quote]

Does folder **/home/lyle/Desktop/share** exists ?
Do you have **smbfs** package installed ?

---

### Post by tronica on 2006-06-21
doh! i forgot to install smbfs. Thanks a million.

---

### Post by tronica on 2006-06-21
when i try writing to it,  its says i dont have premissions to write to it. but in the smb.conf i have "writable = yes"? any ideas

---

### Post by cyracks on 2006-06-21
Check the linux file system permissions. It will probably work if you write
```

chmod 777 /home/lyle/Desktop/share 

``` but that is very unsecure !

---

### Post by tronica on 2006-06-21
when i did mkdir share, i also did chmod 777 share to start off with. so its got to be in the smb.conf.

edit: i got it thanks for the help.

---

### Post by cyracks on 2006-06-22
[quote=tronica]
edit: i got it thanks for the help.[/quote]

Could you write what was the problem so that others who browse this topic will also know.

---

