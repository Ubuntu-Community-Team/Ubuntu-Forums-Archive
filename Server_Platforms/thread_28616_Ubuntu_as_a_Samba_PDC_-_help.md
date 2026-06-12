---
title: "Ubuntu as a Samba PDC - help"
date: 2005-04-21
forum: Server Platforms
---

### Post by salmo on 2005-04-21
Hey, I'm trying to set up my Ubuntu machine as a PDC with Samba for Windows networking.

My problem is this: I can't authenticate as root, or as a user mapped to root in /etc/smbusers (ie administrator).  Didn't realize it until I tried to join my XP machine to the domain and can't seem to get it working. 

And, yes, I have set up a password for root.  Even if I just try to 
```
smbclient -U administrator -L localhost
```
from the machine and enter my password I am rejected.

Here's a slightly abbreviated version of my smb.conf

```

[global]

## Browsing/Identification ###
workgroup = Salmosoft
server string = Lila
passdb backend = tdbsam
os level = 33
preferred master = yes
local master = yes
security = user
domain logons = yes
dns proxy = no

log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d

encrypt passwords = true
obey pam restrictions = yes
invalid users = root
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
add user script = /usr/sbin/useradd -m %u
delete user script = /usr/sbin/userdel -r %u
add group script = /usr/sbin/groupadd %g
delete group script = /usr/sbin/groupdel %g
add user to group script = /usr/sbin/groupmod -A %u %g
delete user from group script = /usr/sbin/groupmod -R %u %g
add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody %u
username map = /etc/samba/smbusers

printing = cups
printcap name = cups

socket options = TCP_NODELAY

wins support = no

[netlogon]
   path = /var/lib/samba/netlogon
   read only = yes

```

and my smbusers:
```

root = administrator admin
;nobody = guest pcguest smbguest
```


Any suggestions?  Am I doing something dumb?

---

### Post by Vache on 2005-04-21
[QUOTE=salmo]Hey, I'm trying to set up my Ubuntu machine as a PDC with Samba for Windows networking.

My problem is this: I can't authenticate as root, or as a user mapped to root in /etc/smbusers (ie administrator).  Didn't realize it until I tried to join my XP machine to the domain and can't seem to get it working. 

And, yes, I have set up a password for root.  Even if I just try to 
```
smbclient -U administrator -L localhost
```
from the machine and enter my password I am rejected.

Here's a slightly abbreviated version of my smb.conf

```

[global]

## Browsing/Identification ###
workgroup = Salmosoft
server string = Lila
passdb backend = tdbsam
os level = 33
preferred master = yes
local master = yes
security = user
domain logons = yes
dns proxy = no

log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d

encrypt passwords = true
obey pam restrictions = yes
invalid users = root
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
add user script = /usr/sbin/useradd -m %u
delete user script = /usr/sbin/userdel -r %u
add group script = /usr/sbin/groupadd %g
delete group script = /usr/sbin/groupdel %g
add user to group script = /usr/sbin/groupmod -A %u %g
delete user from group script = /usr/sbin/groupmod -R %u %g
add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody %u
username map = /etc/samba/smbusers

printing = cups
printcap name = cups

socket options = TCP_NODELAY

wins support = no

[netlogon]
   path = /var/lib/samba/netlogon
   read only = yes

```

and my smbusers:
```

root = administrator admin
;nobody = guest pcguest smbguest
```


Any suggestions?  Am I doing something dumb?[/QUOTE]
 Do your log files reveal any errors? *scratches his head because everything looks ok*

---

### Post by Vache on 2005-04-21
[QUOTE=Vache]Do your log files reveal any errors? *scratches his head because everything looks ok*[/QUOTE]
 Can you log in as a non-root/non-administrator account? 

Also, I noticed you have invalid users = root, then you map root to admin and administrator, therefore making admin/administrator invalid (I think)

---

### Post by segrewb on 2005-04-21
[QUOTE=Vache]Can you log in as a non-root/non-administrator account? 

Also, I noticed you have invalid users = root, then you map root to admin and administrator, therefore making admin/administrator invalid (I think)[/QUOTE]

I agree.  You need to remove/modify this.  See attached excerpt from the[ Samba How-to Collection ](http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2561423) 

> 14.2 User and Group Based Controls

The following file and directory permission-based controls, if misused, can result in considerable
difficulty to diagnose causes of misconfiguration. Use them sparingly and carefully.

admin users > List of users who will be granted administrative privileges on the
share. They will do all file operations as the super-user (root).
Any user in this list will be able to do anything they like on the
share, irrespective of file permissions.

invalid users > List of users that should not be allowed to login to this service.

---

### Post by Vache on 2005-04-21
[QUOTE=segrewb]I agree.  You need to remove/modify this.  See attached excerpt from the[ Samba How-to Collection ](http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2561423)[/QUOTE]
 Salmo, did my/segrewb's input help you any? Don't leave us hanging :)

---

