---
title: "Samba Authentication"
date: 2008-09-29
forum: Server Platforms
---

### Post by chrispottrell on 2008-09-29
Hi guys,

I have a domain controller with approx 200~ users, on this box runs Samba with 30~ shares.

Samba after 5 years, is playing silly games so I have decided to move it to a Ubuntu server.

This is relatively simple, the problem I have however is authenticating users. the users are on the DC, is there a way I can have the new Samba box authenticate against the old server? Adding new years/copying old ones across isn't really an option, I get too many new starters!!

I guess I could design the Samba config to be a non-dc and 'join' the domain so users can be authenticated against the old samba server (which is a dc).

Any suggestions are greatly appreciated!!

---

### Post by chrispottrell on 2008-09-29
I'm assuming I could bind the new one to the current domain, so it would recognise username and passwords.

I get the following :

[root@nas samba]# net join -W DOMAIN -U USER
Connection failed: NT_STATUS_UNSUCCESSFUL

I can't really find anything useful on Google :\

---

### Post by jamesrfla on 2008-09-29
Take a look at this. [http://ubuntuforums.org/showthread.php?t=923404](http://ubuntuforums.org/showthread.php?t=923404)

---

