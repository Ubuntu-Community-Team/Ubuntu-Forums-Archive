---
title: "pam-mysql and mysql boot"
date: 2007-10-25
forum: Server Platforms
---

### Post by lee_connell on 2007-10-25
Hi all,

I finally have pam-mysql, libnss-mysql and mysql all working well for authenticating and authorizing users.

One problem I have which is not really a big deal but it is cluttering my logs on bootup is libnss-mysql is complaining it can't connect to mysql through either localhost or mysql.sock.

Once I log into the machine everything works just fine, so it seems as if mysql isn't starting early enough?

Can anyone assist in how to determine if this is the case, and how to make sure mysql is starting before libnss-mysql attempts to query the database.

Thanks!

---

### Post by lee_connell on 2007-10-25
I notice in mysql.log that debian maintenance occurs and then i see queries from nss-mysql come in.  Would this block connections until it was finished?

---

