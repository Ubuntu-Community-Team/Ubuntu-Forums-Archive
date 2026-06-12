---
title: "Call script on password fail"
date: 2009-08-14
forum: Security
---

### Post by bear24rw on 2009-08-14
Is there anyway to call a script when a password fails at login/unlock? I know i can poll /var/log/auth.log but is there a way to have it interrupt driven?

---

### Post by HermanAB on 2009-08-14
Hmm, login is handled by PAM and it is usually configured in /etc/pam.d.  You may be able to do what you want by modifying something there.  However, first make a backup of the whole pam.d directory, since any syntax error will lock you out of your machine, so then you need to be able to boot in single user mode and fix it from the backup.

---

