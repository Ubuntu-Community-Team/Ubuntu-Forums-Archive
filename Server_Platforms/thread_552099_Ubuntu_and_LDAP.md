---
title: "Ubuntu and LDAP"
date: 2007-09-16
forum: Server Platforms
---

### Post by dc.manage.service on 2007-09-16
Hi there

I've managed to configure OpenLDAP into 6.06 LTS version after couple days playing around with it.

Now ... in the client machine, how do authenticate on the client machine? (like domain controller in Windows)

Thanks

---

### Post by Koybe on 2007-09-16
You need to use nsswitch to indicate you're using ldap, then modify your pam so it can check account and password in your ldap db.

I think everything is in there : [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

---

### Post by blackjackchik on 2007-10-14
:confused:Hello
I try it but it is do not work.
Any ideas??

---

