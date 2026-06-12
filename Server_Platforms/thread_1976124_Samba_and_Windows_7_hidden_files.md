---
title: "Samba and Windows 7 hidden files"
date: 2012-05-08
forum: Server Platforms
---

### Post by Gantlett on 2012-05-08
Hello,

I'm using Ubuntu Server 10.04 x64 with all the latest updates.
It's running Samba and acts as my file, DNS and DHCP server.

I have configured offline files for one Windows 7 machine to point to the Homes share and am experiencing an issue with hidden files: whatever I do, I cannot get hidden files to be hidden - they are all visible. I have googled and read articles and activated the **hidden** and **system **flags to the best of my knowledge but the issue persists. When I tick the **hidden** checkbox on a file's properties, the checkbox is unticked the next time I open the file's properties.

Here is my Samba config:
```
[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	map to guest = bad user
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	server string = %h server (Samba, Ubuntu)
	unix password sync = yes
	workgroup = home
	os level = 20
	syslog = 0
	usershare allow guests = yes
	preferred master = yes
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	pam password change = yes


[Danit Work]
	writeable = yes
	map hidden = yes
	path = /home/danit/Danit's Work

[Music]
	writeable = yes
	path = /home/erez/Music

[Movies]
	writeable = yes
	path = /media/BEHEMOTH/Movies

[Kids Movies]
	writeable = yes
	path = /media/BEHEMOTH/Kids Movies

[Downloads]
	guest account = 
	writeable = yes
	create mode = 777
	public = yes
	path = /home/erez/Downloads
	directory mode = 777

[BEHEMOTH]
	writeable = yes
	valid users = erez,danit
	path = /media/BEHEMOTH



[homes]
	writeable = yes
	map hidden = yes
	map archive = yes
	map system = yes

[bt]
	writeable = yes
	public = yes
	create mode = 777
	path = /home/bt/Bittorrent
	directory mode = 777

```

Any help will be greatly appreciated!

Thanks in advance.

---

### Post by Gantlett on 2012-05-15
If anyone could help that would be great!
Thanks

---

