---
title: "slapd not working after last apparmor update"
date: 2008-05-24
forum: Server Platforms
---

### Post by teamanx on 2008-05-24
Hello. I have a Hardy Samba+OpenLDAP server, which has worked OK until the last update of apparmor to 2.1+1075-0ubuntu9.1. Then, slapd is killed as soon as a client tries to make a connection. 

Anybody knows how can I debug this problem? The only solution I have found is locking apparmor version, but I would like to have the security update installed.

BTW, my clients connect to the LDAP server using rootbinddn, and I think maybe it breaks some of the rules in the updated apparmor profiles. But I don't know how to check it: I have made a search for "slapd" in the contents of /var/log/*, and found nothing

---

