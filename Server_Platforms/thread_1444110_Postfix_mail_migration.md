---
title: "Postfix mail migration"
date: 2010-03-31
forum: Server Platforms
---

### Post by DanielGarzon on 2010-03-31
Hello, i am just starting to play with ubuntu ](*,)and part of my new job is research and learn about technologies and this place is MESSY nobody knows anything so my problem goes with postfix. How can i copy/migrate/append/etc.. the current mails to another server which has already postfix installed with different accounts. This remote server is ubuntu and have 2 domains and it is already in production. i have tried to look on the internet but cannot find the solution. any ideas, links or something would be highly appreciated..

BTW The Server version is Jaunty (9.04)

---

### Post by Nicolas.Perrault on 2010-03-31
Sorry can't help you, I'm quite new too, but I'd like to wish you a warm welcome to Ubuntu!

---

### Post by volkswagner on 2010-04-01
Here is an excellent [list of tools]("http://www.athensfbc.com/imap_tools/") for migrating mail server info.

I have used the imap.copy with great success.

---

### Post by KB1JWQ on 2010-04-01
Postfix doesn't store messages, the IMAP/POP server will do that.  It may be Dovecot, Courier, etc.

I'd use imapsync to move the data itself if rsyncing the backend data structures isn't a viable option...

---

