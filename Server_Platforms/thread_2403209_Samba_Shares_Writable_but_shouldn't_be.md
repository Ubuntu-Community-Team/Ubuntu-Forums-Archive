---
title: "Samba Shares Writable but shouldn't be"
date: 2018-10-08
forum: Server Platforms
---

### Post by analogscott on 2018-10-08
I setup a Ubuntu server running Samba to share files with Windows.    I want a couple uses to have read/write access and the users group to have read only access.    The problem i'm running into is that the share is writable by the whole group.

I'm somewhat new to Linux/Samba but very experienced in Windows.    I could be overlooking something simple.     Any help or hints is very appreciated.


Ubuntu 18 
Samba 4.7.6

#==================== Global Settings =======================


[global]
    dns proxy = no
    log level = 3 passdb:5 auth:5
    server role = standalone server
    disable netbios = yes
    max log size = 10000
    server string = fserver
    smb ports = 445
    unix password sync = yes
    encrypt passwords = yes
    interfaces = lo enp0s3
    bind interfaces only = yes
    log file = /var/log/samba/smb.log
    security = user
    map to guest = Bad User


#=====================shares=================================


[Call Sheets]
    valid users = scott,mariz,@users
    read list = @users
    user = scott,mariz,@users
    write list = scott,mariz
    path = /home/fserver/Call Sheets

[IMG]http://handpickedbyscott.com/1.jpg[/IMG][IMG]http://handpickedbyscott.com/2.jpg[/IMG][IMG]http://handpickedbyscott.com/3.jpg[/IMG]

[IMG]http://analogwebserver.com/1.jpg[/IMG]

---

### Post by wildmanne39 on 2018-10-08
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by TheFu on 2018-10-08
I think you need different shares for the different permissions needed. If scott and mariz are in the *users* group, that would be a conflict.

Saw this on samba.org:
> The write list option cannot override Unix permissions. If you've created the share without giving the write-list user write permission on the Unix system, she will be denied write access regardless of the setting of write list.

Also, does the path not need to be quoted?  Spaces aren't good for share paths or share names, IME.

Use **testparm** to validate the config actually used. *Code tags* for posting text files are appreciate here.

I don't have Ubuntu 18.04. Too new.

Windows knowledge helps about 20% and misleads the other 80%.

---

### Post by Morbius1 on 2018-10-09
I cannot reproduce your symptom - at least not with the share definition you created.

I do have some observations however:

[1] There is no such parameter as **user** as in **user = scott,mariz,@users**. Samba will just ignore it but I'm not sure why you wanted it in there.

[2] Um ... you set **unix password sync = yes** but you didn't specify a password program to use. By default there is none which is why one is added to smb.conf: 
```
passwd program = /usr/bin/passwd %u
```
You should be able to verify these observations yourself by running the following command:
```
testparm -s
```
[3] Oh  .. and ... smb.conf can handle spaces in the shares path. Not crazy about having spaces in the share name but that's just me.

You might consider resetting your smb.conf file to the factory settings then adding your share definition to that. There is a copy of the default smb.conf at [B]/usr/share/samba/smb.conf

[/B][I]Despite its name smb.conf is not the samba configuration file. It's basically a diff file that contains all of the additions and overrides to the default settings of samba which you can not access directly. Ubuntu sets up smb.conf based on its own considerations so you might want to start with that and make surgical changes to it rather than replacing it.
[/I]

---

