---
title: "Local mail delivery broken"
date: 2006-12-18
forum: Server Platforms
---

### Post by kozimodo on 2006-12-18
I recently had a hard drive crash on my Dapper server (fortunately I have automatic backups).  I restored it and everything is working fine except I no longer get local mail.  I have a postfix/dovecot pop server (set up according to Joe Topjian's HowTo) that works fine but local stuff just disappears.

Can someone help me?

---

### Post by MJN on 2006-12-18
How did you reinstall the server? Fresh install with new config? Or a complete image restore?
 
What do your mail logs say?
 
Mathew

---

### Post by kozimodo on 2006-12-18
Ah, thank you!  I thought I had looked at the logs and found nothing but upon checking again, it seems that procmail was not installed.  Funny, I don't recall having to install procmail before...  :-k

---

### Post by MJN on 2006-12-18
Glad you're sorted - it was sounding potentially tricky!

I trust from now on you'll check your logs before posting..? ;)

Mathew

---

