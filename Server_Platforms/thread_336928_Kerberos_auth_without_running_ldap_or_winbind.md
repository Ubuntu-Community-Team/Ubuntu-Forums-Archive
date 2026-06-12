---
title: "Kerberos auth without running ldap or winbind"
date: 2007-01-12
forum: Server Platforms
---

### Post by wrdlogin on 2007-01-12
Is there a way to do kerberos authentication on a Ubuntu 6.06 server without also using ldap and/or winbind?   What I want to do is use my Win2003 server running AD to authenticate users against.  I don't need any other services from the domain other than authentication so I'm hoping I don't have mess with any further configuration than kerberos.  I believe I've got kerberos up and working (ie kinit works for domain users) but domain users are not able to login at the console (ssh login for domain users work fine).

---

### Post by wrdlogin on 2007-01-18
I found the solution to my problem...  I was missing the kerberos keytab file.  Once I generated that on my AD server and copied it my Ubuntu system domain authentication for all logins worked

---

