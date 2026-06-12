---
title: "Samba Active Directory permissions"
date: 2009-07-14
forum: Server Platforms
---

### Post by anyone21 on 2009-07-14
Im sorry if I'm gonna open another topic about samba and AD..

I'll try to be brief and explain my problem very quick..

I've managed to setup samba + kerberos + winbind and joined my machine to the domain...

Currently my SMb.conf is like this

[global]
workgroup = REALM_NAME_IN_CAPS except the .local string
netbios name = MACHINE_NAME
log file = /var/log/samba/%m.log
max log size = 50
security = ADS
realm = REALM_NAME_IN_CAPS
dns proxy = no

encrypt passwords = yes
server signing = yes
smb passwd file = /etc/samba/smbpasswd
allow trusted domains = no
unix password sync = yes
passwd program = /usr/bin/passwd %u
pam password change = yes
obey pam restrictions = yes
idmap uid = 10000-20000
idmap gid = 10000-20000
idmap backend = idmap_rid:2POR2=10000-20000
winbind use default domain = yes
winbind separator = +
winbind enum users = yes
winbind enum groups = yes
template shell = /bin/bash
template homedir = /home%u


[dat2a]
comment = Share Data
path = /home/data
read only = No
create mask = 0775
directory mask = 0775
#browsable = Yes
public = Yes
writeable = Yes
force create mode = 0777
force directory mode = 0777
force security mode = 0777
guest ok = no
inherit permissions = yes
nt acl support = yes
valid users=@"DomainUsers"
write list=@"DomainUsers"
read list =@"DomainUsers"
browseable = yes


I've also chmod 777 /home/data as I've read on some posts around here
well my problem now is that I want to be able to setup permissions in Windows, i mean I access the share and setup the permissions there..

My problem is that I can log in with my AD account but cant change the permissions on it...

All help / sugestions would be appreciated

Thanks in advance

---

