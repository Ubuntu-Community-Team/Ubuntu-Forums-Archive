---
title: "ldap client auth problem"
date: 2007-09-20
forum: Server Platforms
---

### Post by brenth on 2007-09-20
Hey all, I have followed [this]("https://help.ubuntu.com/community/LDAPClientAuthentication"), and when I run "id user" or "getent passwd", everything works perfect. But, When I try to log in as a ldap user, I get nowhere. When I try to su, I get "su: Authentication failure" and in auth.log I get 

Sep 20 12:56:30 ws-047 su[8401]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Sep 20 12:56:30 ws-047 su[8401]: (pam_unix) authentication failure; logname= uid=1000 euid=0 tty=pts/2 ruser=administrator rhost=  user=brent
Sep 20 12:56:32 ws-047 su[8401]: pam_authenticate: Authentication failure
Sep 20 12:56:32 ws-047 su[8401]: FAILED su for brent by administrator
Sep 20 12:56:32 ws-047 su[8401]: - pts/2 administrator:brent

I also am having an issue where administrator will not sudo anymore, when I sudo command, I type in the passwd and it just returns to the shell.

Any ideas?
thanks,
Brent

---

