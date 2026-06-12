---
title: "pam_winbind returns password"
date: 2010-05-26
forum: Security
---

### Post by infecticide on 2010-05-26
I'm getting these entries in my auth.log file.   

What is it and why it is returning passwords?

```
May 26 12:57:50 infecticide dovecot-auth: pam_unix(dovecot:auth): authentication failure; logname= uid=0 euid=0 tty=dovecot ruser=david rhost=88.148.51.170
May 26 12:57:50 infecticide dovecot-auth: pam_winbind(dovecot:auth): getting password (0x00000388)
May 26 12:57:50 infecticide dovecot-auth: pam_winbind(dovecot:auth): pam_get_item returned a password

```

---

### Post by cariboo on 2010-05-26
Unless you are david from 88.148.51.170, it is probably someone trying to break into your system, and failing.

---

