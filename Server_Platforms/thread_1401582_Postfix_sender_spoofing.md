---
title: "Postfix sender spoofing"
date: 2010-02-08
forum: Server Platforms
---

### Post by jonnytabpni on 2010-02-08
Hi Folks,

I've set up an email server as per this howto:

[http://workaround.org/ispmail/etch](http://workaround.org/ispmail/etch)

In a nutshell, it uses a combinatio of postfix, dovecot, amavis (ClamAV and SpamAssisan) and mysql.

However, with this setup, authenticated users are able to spoof outgoing message by simple changing the "from" tag.

Does anyone have any ideas on how I could implement some address mapping to users?

Note: In this setup, postfix users are NOT system users, by are stored in the database

Thanks

Jonny

---

### Post by BobVila on 2010-02-08
Here's the postfix access control page:

[http://www.postfix.org/RESTRICTION_CLASS_README.html](http://www.postfix.org/RESTRICTION_CLASS_README.html)

Should help you get where you're going.

---

