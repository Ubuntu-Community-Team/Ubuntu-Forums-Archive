---
title: "Samba problems"
date: 2011-08-18
forum: Server Platforms
---

### Post by allegrauser on 2011-08-18
I have been trying off and on for days trying to get my SMB working. I finally can see a home and a share on both my Mac 10.4 and Windows XP, but it can authorize.

**My /etc/samba/smbusers looks like this**

```
username = myusername
```

**My /etc/samba/smb.conf has this in it**
```
[test]
path = /home/myusername/test
available = yes
valid users = allegra
read only = no
browsable = yes
public = yes
writable = yes

[share]
 comment = allegra File Server 
 path = /var/
 force user = samba
 force group = samba
 read only = No

```
**When I testparm it get this**

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:Parameter() - Ignoring badly formed line in configuration file: ?# WINS Server - Tells the NMBD components of Samba to be a WINS Client
params.c:Parameter() - Ignoring badly formed line in configuration file: ?
Unknown parameter encountered: "?; domain logons"
Ignoring unknown parameter "?; domain logons"
Unknown parameter encountered: "?; printcap name"
Ignoring unknown parameter "?; printcap name"
params.c:Parameter() - Ignoring badly formed line in configuration file: ?
Processing section "[homes]"
Processing section "[share]"
params.c:Parameter() - Ignoring badly formed line in configuration file: ?;[netlogon]
Processing section "[printers]"
Processing section "[print$]"
Unknown parameter encountered: "?; locking"
Ignoring unknown parameter "?; locking"
Processing section "[test]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = WORKGROUP
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        username map = /etc/samba/smbusers
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[homes]
        comment = Home Directories
        read only = No
        browseable = No

[share]
        path = /var/
        force user = samba
        force group = samba
        read only = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[test]
        path = /home/mysername/test
        valid users = allegra
        read only = No
        guest ok = Yes
```

When I got login on the Mac it say username or password is not correct. I would really appreciate help.

---

### Post by SeijiSensei on 2011-08-18
Add your password to samba with 

```
sudo smbpasswd -a yourusername
```

You'll be prompted first to enter your password to use sudo, then prompted again to add the password for yourusername.  Your samba password need not match your Linux password.

---

### Post by allegrauser on 2011-08-18
I had already did that, and I did it again just to verify. But still it failed to authenticate.

---

### Post by SeijiSensei on 2011-08-19
Take a look in /var/log/samba and see if the log files give you any ideas.

---

### Post by luvshines on 2011-08-19
Since you are using the username map parameter, I am just curious which username are you trying to connect with, the one on the left or right of '=' sign ?

---

### Post by hrturner on 2012-03-15
I know this is a really old topic. I apologize but I am having the same problem. Did the OP ever get this resolved?
 
luvshines - for my reference, shouldn't I be using the name to the right of the  " = " (ie unix_uname = samba_login_name)?

---

