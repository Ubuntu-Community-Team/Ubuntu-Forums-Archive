---
title: "Samba: Password restricted shares with Security = Share don't work"
date: 2008-03-21
forum: Server Platforms
---

### Post by Jonamb on 2008-03-21
Hello again,
I'm atm trying to get Samba server running (in Security = Share because I want my friends to have easy access to the Shares), this works flawlessy.
 I also want a write access to the directory where all the shares are stored (eg /jmb/Videos /jmb/Musik and I want to have write access to /jmb/)
I have a User Netjmb:jmb with which I want to acces she shares
ls -l of the directory is
drwxrwxr-x 8 jmb  jmb   4096 2008-03-21 18:22 jmb
and in it
drwxrwxr-x 25 jmb jmb 4096 2005-10-08 17:56 Musik
drwxrwxr-x 22 jmb jmb 4096 2008-03-21 00:58 Videos

Part of my smb.conf:

```
[global]
        log file = /var/log/samba/log.%m
        smb passwd file = /etc/samba/smbpasswd
        obey pam restrictions = yes
        #socket options = TCP_NODELAY
        dns proxy = no
        netbios name = Jerver
        winbind enum users = no
        invalid users = root
        default = global
        workgroup = jam-net
        os level = 20
        security = share
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        encrypt passwords = yes
        max log size = 1000

[Musik]
        guest only = yes
        public = yes
        path = /jdd/jmb/Musik/MP3

[jmb]
        valid users = netjmb,netjmbres
        writeable = yes
        path = /jdd/jmb
        only user = yes
        #revalidate = yes



[Videos]
        guest only = yes
        public = yes
        path = /jdd/jmb/Videos
```


if y try to access the share with smbclient I get this:
```
jmb@Jerver:/etc/samba$ smbclient //jerver/jmb
Password:
Domain=[JAM-NET] OS=[Unix] Server=[Samba 3.0.26a]
Server not using user level security and no password supplied.
tree connect failed: NT_STATUS_WRONG_PASSWORD

```

Smbusers:
```
nobody = guest smbguest pcguest
netjmb = Network User for jmb

```
Smbpasswd
```
netjmb:1001:-------------:[U          ]:LCT-47E3DD99:

```

So any help would be greatly apreciated :)
JJ

---

### Post by InvIsiBlekID on 2008-03-21
Hello JJ, first off I would change your writable user's name to jmb. Since I believe you need to use a valid user from the linux box to create a samba password. After that run:
```
sudo smbpasswd -a jmb
```
to create a password for him, it should work just fine after restarting samba:
```
sudo /etc/init.d/samba restart
```

---

### Post by Jonamb on 2008-03-21
Up to now for security reasons I used netjmb for network accessing and jmb for local access, or is this useless?
Btw, netjmb is also in passwd:
netjmb:x:1001:1000:JMB Net Access,,,:/jdd/jmb:/bin/bash

---

### Post by Jonamb on 2008-03-26
Ok, I tried to put jmb also in valid users, and using smbclient I can connect when using the smbpasswd password. The bit creepy part is that I can access the share with write rights using no password whatsoever, which is a bit beside the point of a almost root access to a directory...

---

