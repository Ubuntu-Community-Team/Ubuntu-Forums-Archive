---
title: "ldap shadowLastChange attribute not allowed"
date: 2018-08-17
forum: Server Platforms
---

### Post by kladizkov on 2018-08-17
I have setup a openldap server. I have configured password aging feature using ppolicy. All works pretty well, expect the password aging. When I use ldappasswd command and set the password, the password aging is working. But when the user changes the password using the passwd command from bash shell, it gives an error in ldap logs like below

> Entry (uid=bob,ou=People,dc=example,dc=com), attribute 'shadowLastChange' not allowed
entry failed schema check: attribute 'shadowLastChange' not allowed
conn=1167 op=1 RESULT tag=103 err=65 text=attribute 'shadowLastChange' not allowed


attribute 'shadowLastChange' not allowed. Is it provided by passwd command to the ldapserver? How can I prevent this?

---

