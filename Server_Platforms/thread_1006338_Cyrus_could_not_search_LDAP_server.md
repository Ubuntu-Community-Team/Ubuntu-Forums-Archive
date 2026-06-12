---
title: "Cyrus: could not search LDAP server"
date: 2008-12-09
forum: Server Platforms
---

### Post by cbrunet on 2008-12-09
Hi!

I have my log files populated with those messages:

cyrus/imap: nss_ldap: could not search LDAP server - Server is unavailable
cyrus/lmtpunix: nss_ldap: could not search LDAP server - Server is unavailable

The problem is that I have no idea where to look to solve this. 
In /etc/imapd.conf, sals_pwcheck_method is set to salsauthd
In /etc/default/salsauthd, MECHANISMS="pam"

Since my LDAP config for pam are actually working (I can login using a user in the LDAP base), what could be causing the error message?

Thank you,

Charles.

---

### Post by cbrunet on 2009-02-23
It seems installing nscd package solved my problem.

Charles.

---

