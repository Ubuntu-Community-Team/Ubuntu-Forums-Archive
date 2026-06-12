---
title: "LDAP user authentication"
date: 2006-01-03
forum: Server Platforms
---

### Post by chele on 2006-01-03
Hi, I have followed these: [http://people.debian.org/~torsten/ldapnss.html]("http://people.debian.org/%7Etorsten/ldapnss.html") instructions in an attempt to allow users to authenticate via LDAP on this system. However, it does not seem to be working, as the user.log is filled with error messages.> Jan 3 04:28:08 localhost start-stop-daemon: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Jan 3 04:28:08 localhost syslogd: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP serverAnyone have any ideas on what is missing?

---

### Post by bluefrog on 2006-01-03
have you installed/configured libnss-ldap and pam-ldap? nssswitch.conf?

james

---

### Post by chele on 2006-01-03
[quote=bluefrog]have you installed/configured libnss-ldap and pam-ldap? nssswitch.conf?[/quote]Yes, just as the linked howto indicates, those packages and files are installed and configured.

---

### Post by chele on 2006-01-03
> Jan  3 06:26:06 localhost syslogd: nss_ldap: reconnecting to LDAP server...
Jan  3 06:26:06 localhost syslogd: nss_ldap: reconnected to LDAP server after 1 attempt(s)And then it starts working....

Once I created a new user on the system using phpLDAPadmin, it started to work, so I don't know why those 1st error messages came up.

Now I would like to find some ldapadmin gui that creates users the debian way, as phpLDAPadmin does not seem to. But that is a topic for another thread...

---

