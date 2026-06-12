---
title: "pwdAccountLockedTime not honoured by PAM"
date: 2011-12-26
forum: Server Platforms
---

### Post by rajnesh.siwal@gmail.com on 2011-12-26
The LDAP server has been configured properly.
It sets the "pwdAccountLockedTime" after 5 failed login attempts.
ldapsearch fails for the account that is locked.

However, the user is still able to access the account through ssh/console using the LDAP credentials.
Please suggest if I am missing something.

---

