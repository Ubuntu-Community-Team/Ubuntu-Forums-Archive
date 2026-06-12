---
title: "Dovecot authentication no go"
date: 2009-11-26
forum: Server Platforms
---

### Post by boothefoxx on 2009-11-26
Ubuntu 8.04.3
Dovecot 1.0.10
Virtualmin GPL 3.75

Some users can't login after password has been changed. User and password entered correctly. 

All i get in logs as a response is :
Nov 26 13:09:19 melnais dovecot: imap-login: Aborted login (1 authentication attempts): user=<ingusli>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured

other users at the same time can login without a problem. 

The only way to fix this is to create a new user copying all the mail to the new mailbox and deleting old one. The newly created mailbox works just fine.

any ideas ?

---

