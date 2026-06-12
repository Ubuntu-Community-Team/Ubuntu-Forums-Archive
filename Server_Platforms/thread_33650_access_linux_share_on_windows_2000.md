---
title: "access linux share on windows 2000"
date: 2005-05-11
forum: Server Platforms
---

### Post by Rule on 2005-05-11
Hey people :D

on windows 2000 I can see my ubuntu shares, but when it gies me a pop up asking for my username and password I enter my Ubuntu user/pass and it doesnt work. My Ubuntu box can access windows just fine :D

---

### Post by LordHunter317 on 2005-05-11
You need to run:```
smbpasswd -a [user]
``` and put in a password to be used for Samba access.  This doesn't have to be the same password, but it can be.

Samba uses it's own password files because of the way SMB/CIFS works.

---

### Post by Rule on 2005-05-11
Hi

I keep getting this error

```
xquizit@faith:~ $ sudo smbpasswd -a win
Can't load /etc/samba/smb.conf - run testparm to debug it
xquizit@faith:~ $
``` 

so then when I run testparm as root I get this

```
xquizit@faith:~ $ sudo testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
params.c:Section() - Empty section name in configuration file.
params.c:pm_process() - Failed.  Error returned from params.c:parse().
Error loading services.
xquizit@faith:~ $
```

---

