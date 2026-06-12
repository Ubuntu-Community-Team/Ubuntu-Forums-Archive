---
title: "OpenLdap 2.4.28 accesslogs"
date: 2013-09-17
forum: Server Platforms
---

### Post by sherrera on 2013-09-17
Hello,

I have 2 openldap servers running on Ubuntu 12.04. One is the primary and the other is a slave. The slave is setup to read from /var/lib/ldap/accesslog. My problem is that ldap keeps dumping files into that directory log.00000000001 then log.000000002 and so on. Can i remove these logs? How do i know which ones it is still using and which are safe to remove. Ideally it would be great for the server to automatically remove the log once it was done using it. 

Any ideas?  

Thanks

---

