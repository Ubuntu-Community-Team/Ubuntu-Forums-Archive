---
title: "courier-imap + postfix + postgresql"
date: 2012-02-03
forum: Server Platforms
---

### Post by chinna saaeb on 2012-02-03
I have setup a mail server with virtual users following meticulously the instructions as mentioned in
[http://theclimber.fritalk.com/post/2009/01/27/Tutorial-%3A-Setup-your-mail-server-%28courier-imap-postfix-postgresql%29](http://theclimber.fritalk.com/post/2009/01/27/Tutorial-%3A-Setup-your-mail-server-%28courier-imap-postfix-postgresql%29)

However the users created (test@example.com and [email]grep@example.com[/email]) cannot recieve the mails
Can anybody advise

---

### Post by collisionystm on 2012-02-03
> **chinna saaeb said:**
> I have setup a mail server with virtual users following meticulously the instructions as mentioned in
[http://theclimber.fritalk.com/post/2009/01/27/Tutorial-%3A-Setup-your-mail-server-%28courier-imap-postfix-postgresql%29](http://theclimber.fritalk.com/post/2009/01/27/Tutorial-%3A-Setup-your-mail-server-%28courier-imap-postfix-postgresql%29)

However the users created (test@example.com and [email]grep@example.com[/email]) cannot recieve the mails
Can anybody advise



Are you trying to send from an outside email, or from internally?

If you are sending from an outside account such as gmail, you do need an FQDN and an mx record pointing to your box.

---

### Post by chinna saaeb on 2012-02-09
No not outside. It is within the intranet i.e., on the same computer

---

