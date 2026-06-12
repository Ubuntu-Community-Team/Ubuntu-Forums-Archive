---
title: "Problems with groups.conf on LDAP authorized logins"
date: 2010-08-25
forum: Security
---

### Post by kangarooks on 2010-08-25
Hi

I'm having problems with LDAP login and enforcing additional groups

I added 

*; *; *; Al0000-2400;audio,cdrom,floppy,plugdev,video,fuse,scanner,dip

to /etc/security/group.conf 

and juggled in /etc/pam.d/login with placing pam_group.so before ldap as [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication) suggests, but still for some reason my additional groups are not added

Any idea on whats going on would be awesome

---

### Post by kangarooks on 2010-08-26
So, any ideas? Even the faintest ones will do.

---

### Post by kangarooks on 2010-09-16
problem solved itself, no idea what happened :)

one day it just started to work as it was described in that article :)

---

