---
title: "Multiple Email Servers"
date: 2009-04-10
forum: Server Platforms
---

### Post by AndyXS on 2009-04-10
If I have an single email server with the below setup and the demand for the service was so high it required additional servers. How would these servers be setup?

Current Server 1: Ubuntu + Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail + Postgrey

New Server 1:
New Server 2:
New Server 3:
New Server 4:

Thanks for your advice.

---

### Post by zaicic on 2009-04-11
Move mail storage, MySQL, and IMAP server to another machine and setup the Postfix machines to use the same mail storage and same MySQL database.

Also check this thread

[http://www.irbs.net/internet/postfix/0712/1396.html](http://www.irbs.net/internet/postfix/0712/1396.html)

---

