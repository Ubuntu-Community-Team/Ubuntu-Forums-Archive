---
title: "postfix, user quota, bounce email - is it possible"
date: 2006-12-14
forum: Server Platforms
---

### Post by awgan on 2006-12-14
There is a simple question.
Is it possible to configure postfix in the way that it wil bounce emails when user mailbox is over quota ? I've been searching quite lot and can't find any answers/sample config.

Thanks for any replay

---

### Post by MJN on 2006-12-14
Sure, use the **mailbox_size_limit = <limit in bytes>** directive in /etc/postfix/main.cf.
 
Check out [http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html) for further details.
 
Mathew

---

