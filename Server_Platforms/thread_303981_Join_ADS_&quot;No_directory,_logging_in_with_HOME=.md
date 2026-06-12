---
title: "Join ADS: &quot;No directory, logging in with HOME=/ &quot;"
date: 2006-11-21
forum: Server Platforms
---

### Post by emil.s on 2006-11-21
Hello!
I am trying to connect a Ubuntu client to my schools ADS server (Win2k).

But when i try to login i get this:
```
root@schoolinject: /home/emil $ login
hostname login: domain-user
Password:
Linux schoolinject 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686

No directory, logging in with HOME=/
domain-user@hostname:/$
```

But if i create "/home/*DOMAIN*/*user*" it works perfect. :S
I want it be made automatic! 

Here is my config files:
```
root@schoolinject: /etc/pam.d $ cat common-session
session         sufficient      pam_winbind.so
session         required        pam_mkhomedir.so umask=0022 skel=/etc/skel/
session         sufficient      pam_unix.so
session         optional        pam_foreground.so
root@schoolinject: /etc/pam.d $ cat /etc/samba/smb.conf
[global]

workgroup = MY_DOMAIN
server string = KUbuntu i GAMMA
;   wins support = no
;   wins server = w.x.y.z
dns proxy = no
;   name resolve order = lmhosts host wins bcast
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = true
log file = /var/log/samba/log.%m
max log size = 1000
;   syslog only = no
syslog = 0
panic action = /usr/share/samba/panic-action %d
;   security = user
encrypt passwords = yes
passdb backend = tdbsam
obey pam restrictions = yes
;   guest account = nobody
invalid users = root
;   unix password sync = no
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
;   pam password change = no
;   domain logons = yes
;   logon path = \\%N\profiles\%U
;   logon path = \\%N\%U\profile
;   logon drive = H:
;   logon home = \\%N\%U
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
;   load printers = yes
;   printing = bsd
;   printcap name = /etc/printcap
;   printing = cups
;   printcap name = cups
;   printer admin = @lpadmin
;   include = /home/samba/etc/smb.conf.%m


socket options = TCP_NODELAY
map to guest = Bad User
restrict anonymous = no
guest ok = yes
domain master = no
preferred master = no
max protocol = NT
ldap ssl = No
server signing = Auto
security = ads
winbind uid = user
winbind gid = users
winbind enum users = yes
winbind enum groups = yes
winbind cache time = 10
winbind separator = +
template shell = /bin/bash
realm = DET.HÄR.ÄR.RÄTT
winbind use default domain = yes

template homedir = /home/%D/%U
password server = *

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
idmap uid = 10000-20000
idmap gid = 10000-20000


#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
comment = Home Direcotries
valid users = %S
read only = No
browseable = No

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
comment = All Printers
browseable = no
path = /tmp
printable = yes
create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers

```

What is wrong?

---

