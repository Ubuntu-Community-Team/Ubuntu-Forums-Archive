---
title: "Cyrus - move emails to another server"
date: 2007-09-13
forum: Server Platforms
---

### Post by dexter2 on 2007-09-13
Hi,
I'm going to move Cyrus/Imap emails from one server to another. I already did it once like this (when i was moving to backup server, now i need to move from backup server back to main server):

-setup cyrus for LDAP autentification
-stop cyrus
-export mailboxes list from source server:
     su - cyrus -c '/usr/sbin/ctl_mboxlist -d' > mboxlist.txt
-importe mailboxes list to target server:
     su - cyrus -c '/usr/sbin/ctl_mboxlist -u < mboxlist.txt'
-copy email files from source server to target server.
-adjust email files ownership on target server.
-set users quotas on Cyrus on target server through webmin

This procedure works fine with one problem: I loose email attributes (seen,...). 
Do somebody know, how to keep email attributes?

Thanks. Dexter2

---

### Post by dexter2 on 2007-09-13
I found the way:
directory: /var/lib/cyrus/user contain files username.seen  username.sub for each user. In this files are needed atributes. So this directory tree must also by copied.

---

