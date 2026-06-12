---
title: "Does postfix-ldap works with OpenLDAP?"
date: 2008-05-24
forum: Server Platforms
---

### Post by cviniciusm on 2008-05-24
[FONT=Arial][SIZE=2]Hello,

Does postfix-ldap works with OpenLDAP, please?

I followed the directions at /usr/share/doc/postfix/html/LDAP_README.html, but Squirrelmail doesn't recognize the LDAP users.

Worst, logged with a local user on Squirrelmail I can't send a message to another local user due to a lookup failure.

Any ideas, please?


TIA,
cviniciusm.
[/SIZE][/FONT]

---

### Post by pdwerryhouse on 2008-05-26
It's hard to say what the problem is, without having seen your postfix config files, and an example of your ldap entries, but I can definitely say that Postfix does work with OpenLDAP.

---

### Post by cviniciusm on 2008-05-27
Hello,

I can do anonymous queries to my LDAP server.

As I said, I followed the directions from the postfix-ldap package.

The commands newaliases works with no problem.

But when I try to use Squirrelmail, it fails to authenticate both local users as ldap users, it shows lookup error.

This not happens without postfix-ldap configuration.

Any ideas, please?


Regards,
cviniciusm.

---

