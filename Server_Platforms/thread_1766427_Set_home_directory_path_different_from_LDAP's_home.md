---
title: "Set home directory path different from LDAP's home"
date: 2011-05-24
forum: Server Platforms
---

### Post by hewbert on 2011-05-24
Hi,

I need to specify a different path to home directories on a particular server than what LDAP contains for the users, besides using a symlink.  E.g. "/Users/jdoe" vs "/home/jdoe"  I don't want to change the actual LDAP attributes, just want a particular server to point them in the right direction (Ubuntu 10.04).

Any ideas on this?  I'm assuming it's something I could probably set in pam configurations?

Thanks

---

### Post by hewbert on 2011-05-24
> **hewbert said:**
> Hi,

I need to specify a different path to home directories on a particular server than what LDAP contains for the users, besides using a symlink.  E.g. "/Users/jdoe" vs "/home/jdoe"  I don't want to change the actual LDAP attributes, just want a particular server to point them in the right direction (Ubuntu 10.04).

Any ideas on this?  I'm assuming it's something I could probably set in pam configurations?

Thanks

Nevermind.  We're using nslcd and specified:

```
map passwd  homeDirectory "/home/$uid"
```

in /etc/nslcd.conf

---

