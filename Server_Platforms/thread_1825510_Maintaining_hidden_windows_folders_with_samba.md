---
title: "Maintaining hidden windows folders with samba"
date: 2011-08-15
forum: Server Platforms
---

### Post by millsy on 2011-08-15
Hi all.  Hope this is an easy one to solve.  I've set up a ubuntu server at home with the intention of sharing files with windows clients, so I've installed samba.  I have no security issues so I've allowed public access to the shares and I can access them fine from all windows machines.  I also need to preserve the dos attributes for files and folders using 'map hidden', 'map system', 'map archive' which works great for files but not for folders.  I've got a number of folders from my windows box which I would like to keep hidden (for tidiness more than anything) but when I transfer them to the samba share, they become visible again and I can seem to control their visibility at all from windows or from ubuntu.

Do I take it from this that samba can only manage to maintain dos flags on files and not on directories?

This is the relevant part of the samba.conf file

```
[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	map hidden = yes
	obey pam restrictions = yes
	force directory mode = 0000
	force group = nogroup
	map to guest = bad user
	encrypt passwords = true
	public = yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	dns proxy = no
	map system = yes
	netbios name = core
	writeable = yes
	server string = %h Server
	wide links = no
	unix password sync = yes
	force create mode = 0000
	workgroup = HOME
	force user = nobody
	os level = 20
	create mode = 0777
	syslog = 0
	usershare allow guests = yes
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	directory mode = 0777
	pam password change = yes


[media]
	comment = Shared files
	path = /usr/media

```

Any help would be really appreciated.

Mark

---

### Post by dtfinch on 2011-08-15
I haven't used hidden files in Samba, but the "map hidden/system/archive" options use the executes bit of the permissions. Directories need to be marked executable to be fully read, so it wouldn't be able to use the same trick on them.

There's a newer "store dos attributes" option that uses extended attributes rather than execute bits. The filesystem may need to be mounted with the "user_xattr" option for extended attributes to work.

---

### Post by millsy on 2011-08-15
> **dtfinch said:**
> I haven't used hidden files in Samba, but the "map hidden/system/archive" options use the executes bit of the permissions. Directories need to be marked executable to be fully read, so it wouldn't be able to use the same trick on them.

There's a newer "store dos attributes" option that uses extended attributes rather than execute bits. The filesystem may need to be mounted with the "user_xattr" option for extended attributes to work.

Ahh - so hidden directories probably wont work.  Does the "user_xattr" mounting option alter the way the filesystem works?  I don't want to mount it like this if it's going to corrupt it!

---

