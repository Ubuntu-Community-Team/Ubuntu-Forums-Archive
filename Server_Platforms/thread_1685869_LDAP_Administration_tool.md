---
title: "LDAP Administration tool"
date: 2011-02-11
forum: Server Platforms
---

### Post by WitchCraft on 2011-02-11
Is there any good LDAP-Administration tool ?

I need to setup test accounts and groups.
For that I can test a LDAP-to-DataBase synchronization tool.

Anything with which I can quickly add users /Groups in the directory structure.

I don't care which LDAP-server, as long as it is stable enough to run for 10 minutes.

---

### Post by rudelgurke on 2011-02-11
JXplorer does the job here. :)

---

### Post by elico on 2011-02-11
phpldapadmin

---

### Post by WitchCraft on 2011-02-13
> **rudelgurke said:**
> JXplorer does the job here. :)

Nope, JXplorer doesn't even connect. 
PHP works, however.
Creating ldifs manually however was not at all the thing I had in mind when I said **quickly** add users and groups.

---

### Post by luvshines on 2011-02-13
LDAPSoft has some pretty good tools, but they are not free and really expensive :(
You can use only a 30 days trial

[http://www.ldapsoft.com/ldapadmintoolprofessional.html](http://www.ldapsoft.com/ldapadmintoolprofessional.html)

I love the 'LDAP plus AD help desk tool', helps me manage both my LDAP and AD servers from same tool

Maybe someday, someone else comes up with similar tools
Or maybe LDAPSoft tools are available for free

You can also try "Luma", it is easy to use too

---

### Post by WitchCraft on 2011-02-14
I found some.

Apart from WebMin, I found LAM:
[http://www.ldap-account-manager.org/](http://www.ldap-account-manager.org/)

And there's a decent browser, too:
[http://ldaptool.sourceforge.net/](http://ldaptool.sourceforge.net/)

It's basically cross-platform (wxWidgets), but the Linux binary doesn't run because it misses symbols in the shared libraries libraries (dynamically linked, I installed wxWidgets), and the source doesn't compile...

However, the statically linked windows executable works just fine under wine.

---

