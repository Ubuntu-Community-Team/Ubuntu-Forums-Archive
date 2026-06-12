---
title: "Problem with nssldap-update-ignore-users"
date: 2010-09-20
forum: Server Platforms
---

### Post by jkugler on 2010-09-20
I'm having a problem with nssldap-update-ignore-users.  It bases its config on a minimum user ID, so will add, say, www-priv to the ignore list every time nssldap-ignore-users is run. BUT: www-priv is in a group in LDAP, so LDAP will then not be asked about this group, breaking privs.  Is there a way to tell it to exclude adding certain users to this list?

---

