---
title: "LDAP randomly disabling samba users"
date: 2012-08-03
forum: Server Platforms
---

### Post by sdmike6 on 2012-08-03
I'm running Ubuntu 11.10 amd64

I have a fileshare setup running samba and users are authenticated with LDAP.

The server externally authenticates with a master LDAP server.

I'm having a weird issue where some users are not able to login, it's as if they have been disabled. If I go on the master LDAP server and create a new user, the user is able to log into the samba server.

I checked /var/log/ and looked at auth, syslog, and in /var/log/samba/

It's not clear to me why other users can get in but others can not.

Any help is appreciated.

Thank you

---

### Post by luvshines on 2012-08-05
Increase the log level in smb.conf, that will definitely tell you what's wrong.
Some quick checks can be, make sure sambaSID is having correct values, sambaNTpassword is valid, accountFlags is valid

---

