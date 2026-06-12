---
title: "samba read+execute permission"
date: 2010-02-20
forum: Server Platforms
---

### Post by salim.madni on 2010-02-20
samba read+execute permission
dear gurus can someone give me practical example of this, i need 2 king of permission 1 is full access and other is read+exceute. it can be by ip by userid or by group. as i am beginner try to find such example cant find it so far

see below my smb.conf file

[global]
workgroup = test
server string = sa1
hosts allow = 192.168.0.1 192.168.0.2 192.168.0.3
log file = /var/log/samba/%m.log
security = user
encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

[test_share]
comment = test_share
path = /var/opt/test_share
browseable = yes
writable = yes
public = yes
read only = no

---

