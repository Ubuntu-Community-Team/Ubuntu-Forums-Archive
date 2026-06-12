---
title: "Samba File Permissions"
date: 2006-12-26
forum: Server Platforms
---

### Post by galeron on 2006-12-26
Hi guys,

I've a couple of shares that I want to allow access only to specific users and all other users are to be locked out.

I've used the write list = $username option in my smb.conf file, but the other users still have read only access.

Hence, I'd like to know how I can prevent the read only access?

Thanks!

---

### Post by Brazen on 2006-12-26
you'll need to use the "valid users" option.  You can also use file level permissions - if the user does not have x permission on the shared directory, they can not access it.  I would suggest using "valid users" though.

---

### Post by galeron on 2006-12-26
Hm...On Webmin, I restricted the share to a handful of valid users, but in the Security column, it shows: Read only to all known users

Any ideas?

---

### Post by Brazen on 2006-12-26
> **galeron said:**
> Hm...On Webmin, I restricted the share to a handful of valid users, but in the Security column, it shows: Read only to all known users

Any ideas?

I use Webmin a lot, but for Samba, I prefer to edit the config by hand.

You can post your smb.conf (under /etc/samba) and I or someone else can have a look at it and see what it going on.

---

### Post by galeron on 2006-12-27
My Samba configuration:

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	socket options = TCP_NODELAY
	encrypt passwords = yes
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	netbios name = Server
	server string = %h
	invalid users = root
	workgroup = TEST
	os level = 20
	syslog = 0
	security = user
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000



#======================= Share Definitions =======================

[ADMIN]
	path = /server/ADMIN
	write list = user1,user3,user4

[DIRECTOR]
	path = /server/DIRECTORS
	write list = user1,user2

---

### Post by Brazen on 2006-12-27
change "write list" under each of your shares to "valid users".  By default, valid users equals anybody, but if you put in a valid users directive with a list of users, then only those users will be valid.

So your lines will look like this: "valid users = user1,user3,user4"

You will also need to add the "read only" directive (because the default is "yes" to "read only").  If you want it writeable, add this under each share: "read only = no".

Ok, just to clarify, here is how your shares section will look:

[ADMIN]
path = /server/ADMIN
valid users = user1,user3,user4
read only = no

[DIRECTOR]
path = /server/DIRECTORS
valid users = user1,user2
read only = no

---

