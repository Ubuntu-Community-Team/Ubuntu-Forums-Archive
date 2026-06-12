---
title: "Trouble mounting a Windows 7 share on Ubuntu Server 16.04 with no password using cifs"
date: 2017-02-22
forum: Server Platforms
---

### Post by jason3755 on 2017-02-22
I am trying to mount a Windows 7 share on Ubuntu Server 16.04 with no password using cifs.
```

sudo mount.cifs //win/share /media/win -o username=,passsword=,sec=ntlm 0 0
```

I get a permission denied error:
```

sudo mount.cifs //win/share /media/win -o username=win/user,passsword=,sec=ntlm 0 0
```

Also gives me a permission denied error.

```
sudo mount -v -t cifs //win/share /media/win -o username=win/user,passsword=,domain=win,ver=2.1,iocharset=uft8,rw,file_mode=0777,dir_mode=0777,sec=ntlm 0 0
```

Gives me the following...
```

mount.cifs kernel mount options: ip=192.168.x.x,unc=\\win\share,vers=2.1,iocharset=utf8,file_mode=0777,dir_mode=0777,sec=ntlm,user=win/user,,domain=win,pass=********
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

In Windows 7, I have given permission to "Everyone" and have given share access to "Everyone". Both have full control.

If I try username=guest, I get a mount error 127 - key has expired. And if I exclude the password=, mount asks for a password and I again get mount error 13 - permission denied. 

If anyone has any idea what I am doing wrong, I would appreciate the help. Thanks!

---

### Post by wildmanne39 on 2017-02-22
*Thread moved to **Server Platforms**.*

---

### Post by volkswagner on 2017-02-22
Two things to try.

1. Why not simply create a user and password on the Windos 7 machine and use those credentials?
2. I've seen cases with wide open shares any username and password combo will work, try (I think with SAMBA it's like map guest to bad user)
```
sudo mount -t cifs -o domain=workgroup,username=test,password=test //win/share /media/win
```

---

### Post by jason3755 on 2017-02-22
Thank you for your advice. Yes, that it what I ended up doing. I created a windows account for the server with a password and I was then able to mount the windows share with no issues.

---

### Post by DuckHook on 2017-02-24
> **jason3755 said:**
> 
```
…passsword=…
```
```
…passsword=…
```
```
…passsword=…
```
…If anyone has any idea what I am doing wrong, I would appreciate the help.Perhaps it's just a typo made when posting to this thread, but in all instances, you have misspelled "password". Could it be something as simple as that?

---

