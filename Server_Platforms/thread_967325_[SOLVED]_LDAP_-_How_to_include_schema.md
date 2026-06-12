---
title: "[SOLVED] LDAP - How to include schema?"
date: 2008-11-01
forum: Server Platforms
---

### Post by druhboruch on 2008-11-01
Just installed LDAP server on Intrepid.  New install.
I would like to include autofs schema, but I have no clue how.

It used to be one line in slapd.conf...

I would be much grateful for any suggestion.

---

### Post by ivarss on 2008-11-14
Did you figure it out? 
Just installed servr and now I am stuck with the same question :confused:
br,
Ivars

---

### Post by druhboruch on 2008-11-14
There is not exactly abundance of documentation and samples.
So far I have converted my schema to ldif and tried to load it with ldapadd.

No success so far.:confused:
As soon as I have something I will share it here.

I think that you can use old slapd.conf with new openldap if you are desperate.  Just modify /etc/default/slapd, the first line.

Good luck

---

### Post by druhboruch on 2008-12-06
This is the solution:
[https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html#openldap-configuration](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html#openldap-configuration)

---

