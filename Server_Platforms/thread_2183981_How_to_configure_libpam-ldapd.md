---
title: "How to configure libpam-ldapd"
date: 2013-10-27
forum: Server Platforms
---

### Post by mbnoimi on 2013-10-27
Howdy,

I want to know how can I configure libpam-ldapd to enable Unix authentication, LDAP Authentication?

P.S. I tried to use the following but it didn't ask me anything!
```
dpkg-reconfigure libpam-ldapd
```

I'm using Ubuntu 13.04 x64

---

### Post by sandyd on 2013-10-27
> **mbnoimi said:**
> Howdy,

I want to know how can I configure libpam-ldapd to enable Unix authentication, LDAP Authentication?

P.S. I tried to use the following but it didn't ask me anything!
```
dpkg-reconfigure libpam-ldapd
```

I'm using Ubuntu 13.04 x64

```

dpkg-reconfigure nslcd
```

fyi - configuration files are located at
/etc/nslcd.conf
/etc/nscd.conf
/etc/nsswitch.conf

If you want to configure pam/ldap, run
```
pam-auth-update
```

---

### Post by mbnoimi on 2013-10-29
Thanks a lot this fixed my issue.

---

