---
title: "How do I make Postfix require Authorization?"
date: 2009-11-13
forum: Server Platforms
---

### Post by andyxl987 on 2009-11-13
I've follwed the postfix, courier, saslauthd and mysql tutorials at slicehost to setup my virtual mail server and nearly everything is working as it should except for one problem. Anyone may telnet into my server and send mail to my domain without authorization, e.g.

MAIL FROM:made_up_address@domain.tld
RCPT TO:valid_user@mydomain.tld


This only works when sending mail to local domains (relay access is denied). How can I secure postfix so that a valid login is required or no mail may be sent at all?

---

