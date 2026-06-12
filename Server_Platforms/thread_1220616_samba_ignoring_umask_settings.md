---
title: "samba ignoring umask settings"
date: 2009-07-23
forum: Server Platforms
---

### Post by sadris on 2009-07-23
The samba server seems to be ignoring my mode settings in smb.conf.  I have two shares, priv and pub. I want priv to be **600** for all files created in it, with group=john. I want pub to be **660** for all files in it, with group=users.

I got it to force the group properly, but it is still ignoring umask settings--**it appears to be using my terminal mask, rather than the /etc/fstab settings or the smb.conf settings**.

Has anyone experienced this?

See below for file creation on both priv and pub:
```
[john@silvernight /media/priv ]
-> umask && touch test && ll test
0022
-rw-r--r-- 1 john john 0 2009-07-23 00:44 test

[john@silvernight /media/pub ]
-> umask && touch test && ll test 
0022
-rw-r--r-- 1 john users 0 2009-07-23 00:46 test
```

Now with a new umask:
```
[john@silvernight /media/pub ]
-> umask 002 && touch test && ll test
-rw-rw-r-- 1 john users 0 2009-07-23 00:53 test

```

**My fstab file:**
```
[john@silvernight /media/pub_skynet ]
-> cat /etc/fstab | grep skynet
//skynet/pub  /media/pub  smbfs noauto,rw,noatime,username=john,password=my_pass,file_mode=0660 0 0
//skynet/john /media/priv  smbfs noauto,rw,noatime,username=john,password=my_pass,file_mode=0600 0 0
```


**smb.conf:**
```
root@skynet:/etc/samba# cat smb.conf
[global]
   workgroup = WORKGROUP
   server string = Skynet
   wins support = yes
   dns proxy = no
   name resolve order = wins host lmhosts bcast
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   domain master = yes
   local master = yes
   preferred master = yes
   os level = 65
   usershare allow guests = no
[pub]
   comment = pub
   path = /gib/pub
   read only = No
   create mode = 0660
   force create mode = 0660
   directory mode = 0770
   force group = users
   username = john
[john]
   comment = priv
   path = /gib/priv/john
   read only = No
   create mode = 0600
   directory mode = 0700
   force group = john
   username = john
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
```

---

### Post by Iowan on 2009-07-24
Probably not related to your problem, but **smbfs** has been deprecated in favor of **cifs**. [Here]("http://ubuntuforums.org/showthread.php?t=288534") is a good How-To.

---

### Post by jolig on 2012-01-11
I have a related issue since yesterday :-(
OS: Ubuntu server 11.10

Can anyone give me a hint ?

---

### Post by howefield on 2012-01-11
Please post a fresh thread rather than tagging on to an old thread.

Closed.

---

