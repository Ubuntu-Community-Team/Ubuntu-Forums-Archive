---
title: "Postfix User List"
date: 2007-04-09
forum: Server Platforms
---

### Post by kooseefoo on 2007-04-09
Okay, I have a server set up running postfix and dovecot.

Basically, is there a way to change the file postfix and dovecot get their user lists and passwords from? A chroot would do it, but it seems like there should be a simipler way.


Thanks,
Chris

---

### Post by shufla on 2007-04-24
Hello,

By "default" every application on unix system is authenticating users against /etc/passwd and /etc/shadow files (to be exact - they are using PAM modules as higher abstraction layer).

If you want to change authentication system - it depends on your needs. By changing users do you mean aliases? They can be configured by /etc/aliases file. If you'd like to have some external user database - provided by LDAP or SQL database - it is possible to configure postfix and dovecot for this.

Bye,
Shufla

---

