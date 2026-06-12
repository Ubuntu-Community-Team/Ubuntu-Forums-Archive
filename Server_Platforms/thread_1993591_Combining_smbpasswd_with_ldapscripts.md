---
title: "Combining smbpasswd with ldapscripts"
date: 2012-06-02
forum: Server Platforms
---

### Post by natomb on 2012-06-02
Hi there,

during working on integration of samba with ldap, I figured out the following that I find interesting to share for those who might have similar situation.

Using ldap, nscp and samba in combination can lead to situation where every first invocation of smbpasswd -a will fail. It is also described here:

[http://lists.samba.org/archive/samba/2006-May/120798.html](http://lists.samba.org/archive/samba/2006-May/120798.html)


The workaround is to set the negative-time-to-live to 0 (default was 20).


Maybe it helps someone.

---

