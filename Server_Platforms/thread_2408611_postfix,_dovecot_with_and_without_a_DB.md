---
title: "postfix, dovecot with and without a DB"
date: 2018-12-20
forum: Server Platforms
---

### Post by lister171254 on 2018-12-20
There are many excellent Howtos on how to setup a mail server, but I can't find an explanation as to why you would or wouldn't use a DB to store users, domains, etc.
Thanks.

---

### Post by TheFu on 2018-12-21
When you have 50,000 mailboxes, management is easier with a DB.
If you have 25 mailboxes, a DB is overkill.

---

