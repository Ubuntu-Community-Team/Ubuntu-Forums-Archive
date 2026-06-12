---
title: "Fetchmail and Postfix error"
date: 2009-05-24
forum: Server Platforms
---

### Post by kilowattradio on 2009-05-24
**When I run fetchmail I get this output:**

[I][B]....fetchmail: reading message [email]username@mail.g.comcast.net[/email]:18 of 109 (5359 octets) (log message incomplete)fetchmail: SMTP error: 451 4.3.0 Temporary system failure. Please try again later.
.fetchmail:  not flushed[/B][/I]


**In /var/log/mail.err I get this:**

***May 24 17:38:47 ubuntu9-desktop sm-mta[15786]: NOQUEUE: SYSERR(root): hash map "access": missing map file /etc/mail/access.db: No such file or directory***

[B]What do I need to do to set up the access.db file(s)?? 

Thanks[/B]

---

