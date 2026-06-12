---
title: "user login via ldap only accepts crypt hash password"
date: 2010-02-08
forum: Server Platforms
---

### Post by veNom_bz on 2010-02-08
i have two ubuntu servers setup. one hosts an ldap database, the seconds connects to the ldap host via an ldaps connection.

the host is a 9.04 server running openldap (slapd   2.4.15-1ubuntu3)

the client is a 8.04.3 lts server

getent works, ldapsearch works, authentication works ONLY if user's password was set and hashed using CRYPT. using any other hash results in the password being reported as invalid when logging onto the client.

does anyone have some input?

someone using debian lenny reported a similar problem however they didn't post a fix.

thanks

---

### Post by veNom_bz on 2010-02-12
no ideas?

---

