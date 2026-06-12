---
title: "Samba creates huge tmp, prf files on XP client and doesnt load profile."
date: 2008-10-22
forum: Server Platforms
---

### Post by Avinash.Rao on 2008-10-22
Hi all,

I have configured samba in Ubuntu 8.04 as a PDC and roaming profiles are enabled. Here's what is happening, whenever users log off, it creates huge tmp and prf files on the desktop of each user. The files size is about 3GB!!! So, the user takes atleast 15mins to login again.

I have deleted these files as root, but i don't know how these files are created again!
Below is my smb.conf file. I have created a profiles share for the users.

# Global parameters
[global]
workgroup = sscms
netbios name = studio-server
;interfaces = eth1, lo
;bind interfaces only = Yes
passdb backend = tdbsam
logon path = \\%L\profiles\%U
logon drive = p:
logon home = \\%L\%U
;logon script = logon.bat
domain logons = Yes
preferred master = Yes
domain master = Yes
wins support = Yes
os level = 65

#username map = /etc/samba/smbusers
log level = 1
syslog = 0
log file = /var/log/samba/%m
max log size = 50
smb ports = 139
name resolve order = wins bcast hosts
time server = NO
printcap name = CUPS
show add printer wizard = No

;shutdown script = /var/lib/samba/scripts/shutdown.sh
;abort shutdown script = /sbin/shutdown -c
utmp = Yes
map acl inherit = Yes
printing = cups

#veto files = /*.eml/*.nws/*.{*}/
#veto oplock files = /*.doc/*.xls/*.mdb/

hosts allow = 10.10.10.0/24
security = user
smb ports = 139
add user script = /usr/sbin/useradd -m '%u'
delete user script = /usr/sbin/userdel -r '%u'
add group script = /usr/sbin/groupadd '%g'
delete group script = /usr/sbin/groupdel '%g'
add user to group script = /usr/sbin/usermod -G '%g' '%u'
add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody '%u'
include = /etc/samba/dc-common.conf
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

[homes]
comment = Home Directory
valid users = %S
read only = No
browseable = No
path = /home/%u

# Share and Service Definitions are common to all servers

[share]
comment = Student common Share Directory
browsable =yes
path = /home/export/
read only = No
writable = yes

[profiles]
comment = Profile Share
path = /var/lib/samba/profiles
read only = No
profile acls = Yes
writable = yes
browsable = no

;shutdown script = /var/lib/samba/scripts/shutdown.sh
;abort shutdown script = /sbin/shutdown -c

;[netlogon]
;comment = Network Logon Service
;path = /var/lib/samba/netlogon
;logon script = %U.bat
;guest ok = Yes
;locking = No
;read only = no
;root preexec = /var/lib/samba/bin/make_logon_script '%U'

;[printers]
;comment = SMB Print Spool
;path = /var/spool/samba
;guest ok = Yes
;printable = Yes
;use client driver = Yes
;default devmode = Yes
;browseable = No
;[apps]
;comment = Application Files
;path = /apps
;admin users = sambauser
;read only = No

---

### Post by Avinash.Rao on 2008-10-30
Has anybody faced this problem...

---

### Post by dmizer on 2008-10-30
AD controllers are beyond my knowledge, so I'm affraid I'll be of little help. I did move your thread to the servers section of the forum with hope that the server experts will be able to provide you with some ideas.

---

### Post by Avinash.Rao on 2008-11-01
Ok, thank you

But, does samba create any temp files for user profiles or when users are logged in. I don't see this mentioned in the samba documentation.

Avinash

---

