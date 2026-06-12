---
title: "Postfix"
date: 2011-03-14
forum: Server Platforms
---

### Post by jmacgowan on 2011-03-14
I have been searching around for some time, but I just can't seem to find the answer I'm looking for.  I'm hoping some postifx experts can point me in the right direction.
 
I have a virtual mail setup with Postfix, Dovecot, and MySQL and around 50 e-mail addresses.
 
Let's say 20 of them belong to Group A, 30 of them belong to Group B.  How would I configure postfix to deliver a message to all of group A when an email is sent to, say, [EMAIL="groupA@mydomain.com"]groupA@mydomain.com[/EMAIL]?
 
I don't need a step-by-step or anything, but anything that can point me in the right direction would be great.  Thank you.

---

### Post by Demented ZA on 2011-03-14
> **jmacgowan said:**
> I have been searching around for some time, but I just can't seem to find the answer I'm looking for.  I'm hoping some postifx experts can point me in the right direction.
 
I have a virtual mail setup with Postfix, Dovecot, and MySQL and around 50 e-mail addresses.
 
Let's say 20 of them belong to Group A, 30 of them belong to Group B.  How would I configure postfix to deliver a message to all of group A when an email is sent to, say, [EMAIL="groupA@mydomain.com"]groupA@mydomain.com[/EMAIL]?
 
I don't need a step-by-step or anything, but anything that can point me in the right direction would be great.  Thank you.

I assume you want to set up a mailing list?
You could try [this guide]("http://tldp.org/LDP/LGNET/issue72/teo.html"). It might not be exactly what you need, but hopefully it points you in the right direction.

Also, I don't know if that is the most correct way to do it. Maybe someone else could help shed some light on this?

---

### Post by jmacgowan on 2011-03-14
Thank you for the reply!
 
I tried doing it this way, but it doesn't seem to work.  I believe the reason it can't work that way is because I am using virtual users, but I will continue to try.

---

### Post by Demented ZA on 2011-03-14
Oh, I thought you are running virtual servers, not virtual mail users. Any particular reason you are running virtual users instead of unix user accounts?

---

### Post by jmacgowan on 2011-03-14
While the server is running around 50 users now, it will need to expand to handle ~800 (all on the same domain for now, but that might change), which is the reason I'm using a MySQL backend.
 
Ideally, what I really want to do is give all virual users access to [EMAIL="groupA@mydomain's"]groupA@mydomain's[/EMAIL] mailbox so in the future we don't have 800 copies of the same message sent to those users --but I don't know if this is possible without giving them the username and password which I'd rather not do.

---

### Post by Demented ZA on 2011-03-14
There was a forum post about a week or two ago that covered this exact topic. I'm trying to recall the exact title for you.

---

### Post by jmacgowan on 2011-03-14
Are you refering to this?
[http://ubuntuforums.org/showthread.php?t=1704247&highlight=jmacgowan](http://ubuntuforums.org/showthread.php?t=1704247&highlight=jmacgowan)
 
I looked into citadel, and it really is a great program, but I'd like to find a way to do it without it.

---

### Post by jmacgowan on 2011-03-14
I got it working after re-reading some postfix documentation.

I had to specify virtual_alias_maps in my /etc/postfix/main.cf file

I was even able to put the mailing list in MySQL instead of naming all of it in a file  --awesome.

---

