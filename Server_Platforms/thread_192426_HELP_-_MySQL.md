---
title: "HELP - MySQL"
date: 2006-06-08
forum: Server Platforms
---

### Post by mangus580 on 2006-06-08
oh man, I really messed up...

I have been trying to gain network access to MySQL on my ubuntu server.  I edited the mysql users table directly (I know, BAD idea)  I changed on my root user the host field from localhost to *.* (another BAD idea) and now I cant get in :-(  

Any suggests?  I cant lose any of the db's I have in there.  I need help BADLY.

---

### Post by TriggerHappyChewie on 2006-06-08
Ouch.  Can't you do an sql backup?

---

### Post by mangus580 on 2006-06-08
No, I couldnt do a backup....

but... I GOT BACK IN!!!

basically, I dug up the files, deleted the mysql table files, reinstalled mysql, and I got back in....

emergency averted....

---

