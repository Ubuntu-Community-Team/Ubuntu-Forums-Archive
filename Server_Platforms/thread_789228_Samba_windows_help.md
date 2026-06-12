---
title: "Samba/ windows help"
date: 2008-05-10
forum: Server Platforms
---

### Post by LewisA on 2008-05-10
hello 

I'm quite new to linux and I have been trying to set up a samba file server. 

The shared folders all appear in the workgroup in windows but when I try to copy a file over to one of the folders i get this error message 

> 
Error copying to file or folder

cannot copy from: Access to denied

make sure disk is not full or write protected
and that the file is not currently in use  


I know I have enough disk space and Ive tried several different files. I can even map the drive on windows?

here is a copy of my smb.conf file

> #global parameter
workgroup = workgroup
netbois name = Server 
encrypt passwords = yes
map to guest = bad user
log file = /var/log/samba/log.%m
max
log size = 50
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
preferred master = no 
dns proxy = no 
security = share

[Homes]
read only = no 
browseable = yes 
create mask = 0777
directory mask = 0777

[Music]
Path = /music
read only = no
browseable = yes
writable = yes
public = yes 
create mask = 0777
directory mask = 0777

[General Share]
path = /data/general
read only = no
browseable = yes
writable = yes
public = yes
create mask = 0777
directory mask = 0777

i've tried everthing,
Please Help

---

### Post by loix on 2008-05-12
hi

```

[global]
	log file = /var/log/samba/log.%m
	netbios name = PUNDIT
	server string = Samba
	workgroup = MAIZON
	os level = 30
	security = SHARE
	public = yes

[share]
	force user = loix
	force group = loix
	read only = no
	path = /DATA


```
there is absolute no security but it works on my network with windows xp / vista and ubuntu

---

### Post by mdr on 2008-05-12
Looks ok so far.
You have setup the users and the permissions on the shares ?
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

---

