---
title: "Samba and mounting permissions confusion."
date: 2011-05-18
forum: Server Platforms
---

### Post by abadr on 2011-05-18
Hi,

I'm having a hard time figuring out how to set permissions on my samba server and on mounting the share. I would appreciate help figuring things out.

What I need to achieve is have a server share mounted on a computer and give read write access to the users of that client computer. Also permissions should be respected is a user limits access to a directory or file he creates.

What I did was replicate the users on both server and client computers and create an extra user on the server that has full access to the share both in linux and in samba, and I'm mounting the share on the client computer using that extra user from fstab. (Is this the best way to set things up or is there a better way?)

Now the issues I'm having;

- Whenever a user A creates a directory or file it's listed as created by user B. It turns out that the UID does not match on both computers. How do I fix that short or deleting and recreating the users in the proper order. 

- Backup scripts running as root get lot permission denied errors writing to the share especially when using chown and chgroup.

Could someone explain, or point me to an explanation of the logic behind permissions and mounting?

Thanks.

fstab
```

//history/backup	/mnt/backup	cifs	credentials=/etc/samba/user_backup,iocharset=utf8,noexec	0	0

```

smb.conf
```

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	socket options = TCP_NODELAY
	obey pam restrictions = yes
	deadtime = 360
	map to guest = bad user
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	allow hosts = 10.0.0.
	dns proxy = no
	wide links = no
	server string = %h server (Samba, Ubuntu)
	writeable = yes
	unix password sync = yes
	workgroup = WORKGROUP
	create mode = 777
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	usershare allow guests = yes
	max log size = 1000
	pam password change = yes
	directory mode = 777

[backup]
	comment = Backup repository
	wide links = no
	writeable = yes
	create mode = 777
	path = /mnt/backup
	directory mode = 777

```

---

### Post by abadr on 2011-05-20
anybody?

---

