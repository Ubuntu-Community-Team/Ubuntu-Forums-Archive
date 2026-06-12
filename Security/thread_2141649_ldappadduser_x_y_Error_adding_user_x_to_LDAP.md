---
title: "ldappadduser x y Error adding user x to LDAP"
date: 2013-05-03
forum: Security
---

### Post by morphyrichards1 on 2013-05-03
Using 12.04
I'm new to LDAP. I'm trying to make a simple network login authenticator.

I have used this guide [https://help.ubuntu.com/12.04/serverguide/openldap-server.html](https://help.ubuntu.com/12.04/serverguide/openldap-server.html) but did not follow the part on replication as I dont have enough hardware.

I can...
$ sudo ldapaddgroup test
Successfully added group test to LDAP

However ...
$ sudo ldapadduser bob test
Error adding user bob to LDAP

---

