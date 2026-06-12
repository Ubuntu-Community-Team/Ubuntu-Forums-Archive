---
title: "How to make samba to be browseable using login and password?"
date: 2008-04-21
forum: Server Platforms
---

### Post by rado3105 on 2008-04-21
Hi I have samba configured to be browseable by every user without password, but now I want to make some folders to be browseable only using login and password for every user. Could you help. 
Here is my smb.conf:
```
[global]
	name resolve order = hosts wins bcast
	announce version = 5.0
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	force group = r-c
	guest ok = yes
	null passwords = true
	username map = /etc/samba/smbusers
	passdb backend = tdbsam
	wins support = no
	netbios name = rclr-sbmserver
	browseable = yes
	writable = no 
	printing = CUPS
	server string = rclr-smbserver
	path = /media/usbdisk
	workgroup = rclr
	force user = r-c
	syslog only = yes
	comment = USBdisk
	printcap name = CUPS
	create mode = 0644
	syslog = 1
	security = share
	directory mode = 0755
    ; General server settings
```

---

