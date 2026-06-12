---
title: "Samba questions and help"
date: 2009-03-28
forum: Server Platforms
---

### Post by quietas on 2009-03-28
I need some assistance writing a working smb.conf.

I want to be able to create a linux user, probably in Webmin, then have samba authenticate against that user.

I need 3 types of shares though, this I can't get to work. This is why I want to start fresh with a clean smb.conf. Also, my wife does not use a password, but we need one on the protected files

1. Public, User read/write, guest no access
2. Public, Everyone read/write, temp storage
3. Hidden, User read/write, guest no access

Anyone out there got a decent smb.conf I can snag?

---

### Post by lykwydchykyn on 2009-03-28
> **quietas said:**
> I need some assistance writing a working smb.conf.

I want to be able to create a linux user, probably in Webmin, then have samba authenticate against that user.

Samba has it's own database of users, and cannot directly use the linux user database (/etc/passwd).  You can set up synchronization between the two, which is pretty easy to do in Webmin.
> 
I need 3 types of shares though, this I can't get to work. This is why I want to start fresh with a clean smb.conf. Also, my wife does not use a password, but we need one on the protected files

1. Public, User read/write, guest no access
2. Public, Everyone read/write, temp storage
3. Hidden, User read/write, guest no access

Anyone out there got a decent smb.conf I can snag?

If you want a default smb.conf, you should have one saved at /usr/share/samba/smb.conf.  Just copy this to /etc/samba/ and you should be at default settings.

Since you've already got webmin, why not use it to set up Samba?  Where are you getting hung up?

---

### Post by quietas on 2009-03-28
Via webmin I set up the linux user sync. It even seems to work, thus the home dirs work. I can read/write in my home dir and the comics dir.

The other dump dir I can't access and the xxx I can't write.

EDIT: I added 4 lines to xxx to match comics and now I can write. Imagine that ... =)

I'll post my smb.conf below.
```

#======================= Global Settings =======================
[global]
   log file = /var/log/samba/log.%m
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supda$
   obey pam restrictions = yes
   map to guest = bad user
   encrypt passwords = true
   public = yes
   passwd program = /usr/bin/passwd %u
   passdb backend = tdbsam
   dns proxy = no
   netbios name = server
   server string = %h (Ubuntu 9.04)
   unix password sync = yes
   workgroup = AKM
   os level = 40
   syslog = 0
   security = user
   usershare allow guests = yes
   panic action = /usr/share/samba/panic-action %d
   max log size = 1000
   pam password change = yes
   guest account = nobody

#===================== Home Shares ===================================
[homes]
   create mask = 0700
   comment = Home Directories
   directory mask = 0700
   browseable = No
   writeable = yes
   valid users = %S

#===================== User Only Shares ==============================
[comics]
   comment =
   path = /home/1tb-1/comics
   browseable = yes
   admin users = culley
   write list = @sambashare
   create mask = 0774
   directory mask = 0775

#========================== Read/Write All Share =================
[dump]
   comment =
   path = /home/500gb-1/dump
   writeable = yes
   browseable = yes
   create mask = 777
   directory mask = 777

#========================== Hidden Share ==========================
[xxx]
   comment = Because what else would you put in a hidden folder called xxx
   path = /home/samba/1tb-2/xxx
   writeable = yes
   browseable = no
   admin users = culley
   write list = @sambashare
   create mask = 0774
   directory mask = 0775


```

---

### Post by quietas on 2009-03-28
I got it so I can get in to [dump], but I can't write.

```
[dump]
   comment =
   path = /home/samba/500gb-1/dump
   writeable = yes
   browseable = yes
   create mask = 777
   directory mask = 777
   guest ok = yes

```

---

### Post by quietas on 2009-03-28
Got it fixed.

I had to add the "nobody" account to the /etc/group under sambashare along with the culley user.

I then added "write list = @sambashare"

Below is the full smb.conf, working it seems atm.
```
#======================= Global Settings =======================
[global]
   log file = /var/log/samba/log.%m
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supda$
   obey pam restrictions = yes
   map to guest = bad user
   encrypt passwords = true
   public = yes
   passwd program = /usr/bin/passwd %u
   passdb backend = tdbsam
   dns proxy = no
   netbios name = server
   server string = %h (Ubuntu 9.04)
   unix password sync = yes
   workgroup = AKM
   os level = 40
   syslog = 0
   security = user
   usershare allow guests = yes
   panic action = /usr/share/samba/panic-action %d
   max log size = 1000
   pam password change = yes
   guest account = nobody

#===================== Home Shares ===================================
[homes]
   create mask = 0700
   comment = Home Directories
   directory mask = 0700
   browseable = No
   writeable = yes
   valid users = %S

#===================== User Only Shares ==============================
[comics]
   comment =
   path = /home/samba/1tb-1/comics
   browseable = yes
   admin users = culley
   write list = @sambashare
   create mask = 0774
   directory mask = 0775

#========================== Read/Write All Share =================
[dump]
   comment =
   path = /home/samba/500gb-1/dump
   writeable = yes
   browseable = yes
   write list @sambashare
   create mask = 777
   directory mask = 777
   public = yes


#========================== Hidden Share ==========================
[xxx]
   comment = Because what else would you put in a hidden folder called xxx
   path = /home/samba/1tb-2/xxx
   writeable = yes
   browseable = no
   admin users = culley
   write list = @sambashare
   create mask = 0774
   directory mask = 0775
```

---

