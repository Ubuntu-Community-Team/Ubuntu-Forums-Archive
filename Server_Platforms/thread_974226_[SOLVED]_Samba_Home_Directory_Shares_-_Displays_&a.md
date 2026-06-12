---
title: "[SOLVED] Samba Home Directory Shares - Displays &amp;quot;homes&amp;quot; AND user's home directory."
date: 2008-11-07
forum: Server Platforms
---

### Post by chris.zeman on 2008-11-07
I just installed and configured Samba, and it was a painless process. :) Users are able to login from their XP workstations and see their home directories, but they also see a directory called "homes" which also allows them to access their home directory. Is it possible to configure Samba to only show one or the other?

Thank you,
Chris

---

### Post by bab1 on 2008-11-07
> Is it possible to configure Samba to only show one or the other?

Sure.  Show us your [homes] section of /etc/samba/smb.conf.

---

### Post by chris.zeman on 2008-11-07
I MEANT to do that! :lolflag:

I used Webmin to make some final tweaks, and just noticed it moved some stuff into the global options. I'll include that section as well. The "homes" section is a lot shorter than it was before I used Webmin.

```

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	socket options = TCP_NODELAY
	map to guest = bad user
	username map = /etc/samba/smbusers
	encrypt passwords = true
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	wins support = true
	dns proxy = no
	writeable = yes
	server string = %h (Samba, Ubuntu)
	invalid users = root
	unix password sync = yes
	revalidate = yes
	workgroup = CYBER
	os level = 20
	syslog = 0
	security = user
	panic action = /usr/share/samba/panic-action %d
	usershare allow guests = yes
	max log size = 1000
	pam password change = yes

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
	comment = Home Directories
	valid users = %S

```

---

### Post by bab1 on 2008-11-07
Here is my [homes] section:
```
[homes]
        comment = Home Directories
        path = /smb/home/%S

        valid users = %S

        browseable = no 
        guest ok = no

        writable = yes
        create mask = 770
        directory mask = 770

```

I put the spaces in so you could read it easier.  Note the browse and guest lines.

This effectively means only the logged in user sees his home dir.

Edit: I just noticed you have no path directive.  I force my shares to the partition /smb

---

### Post by chris.zeman on 2008-11-07
Thank you very much, BAB1! That did it! :)

Chris

---

### Post by bab1 on 2008-11-07
Glad I could help.  Mark this solved please.

---

### Post by chris.zeman on 2008-11-07
lol, I just marked it Solved and saw your post.

Have a great day! :)
Chris

---

