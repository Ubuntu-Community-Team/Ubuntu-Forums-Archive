---
title: "Freeradius filter-ID"
date: 2019-02-15
forum: Security
---

### Post by abdelkader-1 on 2019-02-15
Hello,

We have a FreeIPA as domain controller and we are planing to use  Freeradius as authentication for the Wireless, i configured freeradius  with LDAP and i can do authentication with a domain user, now the  network team asked me to configure freeradius to return a filter-i of  the user group assigned ID, example we have user1:

  [HTML]dn: uid=user1,cn=users,cn=accounts,dc=subdmain,dc=domain,dc=com
with the group ID:gid=1471600000

[/HTML]  I did some research on google and i found that i have to modify the  file /etc/raddb/sites-enabled/default like in the link bellow but not  exactly the same thing and which command i have to use get this value: [FreeIPA_Freeeradius]("https://stackoverflow.com/questions/43913834/freeradius-filter-id")

  Any suggestion please ?

  Thanks

---

