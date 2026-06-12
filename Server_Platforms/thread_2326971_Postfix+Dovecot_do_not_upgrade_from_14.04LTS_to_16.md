---
title: "Postfix+Dovecot do not upgrade from 14.04LTS to 16.04LTS"
date: 2016-06-06
forum: Server Platforms
---

### Post by pcouderc on 2016-06-06
I have removed apparmor but I am blocked on :

```
Jun  6 17:05:12 tolsupport dovecot: lda(tol): Error: userdb lookup: connect(/var/run/dovecot/auth-userdb) failed:
      Permission denied (euid=60000(messagerie) egid=60000(messagerie) UNIX perms appear ok (ACL/MAC wrong?), dir owned by 0:0 mode=0755)

```
It worked fine in 14.04LTS.
As it is written, UNIX perms are OK, and as I have removed apparmor, what could be the offending ACL/MAC ?

Thanks.
PC

---

