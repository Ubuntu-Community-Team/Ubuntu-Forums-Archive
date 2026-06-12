---
title: "LDAP support for PHP 5.3.2"
date: 2010-07-27
forum: Server Platforms
---

### Post by fred2028 on 2010-07-27
I'm wondering how I can enable LDAP support for my Ubuntu 10.04 LTS server running Apache 2 and PHP 5.3.2? What I'm trying to do is allow users on my existing company's LDAP system to login to my Elgg site automatically (and possibly have their details filled automatically).

---

### Post by ruffEdgz on 2010-07-27
Do you have the LDAP module installed for PHP?

Do the command:
```

aptitude search php5-ldap

```
If you don't know, the command above should have an 'i' next to the search result.

It is possible but I know you will need this module to make that work.

---

