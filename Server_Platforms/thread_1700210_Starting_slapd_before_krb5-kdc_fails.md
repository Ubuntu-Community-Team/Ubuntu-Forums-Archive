---
title: "Starting slapd before krb5-kdc fails"
date: 2011-03-04
forum: Server Platforms
---

### Post by atpa8a on 2011-03-04
Hello,

I'm trying to start slapd before krb5-kdc on boot for LDAP backend for KDC.

It all works if i manually start first slapd and then krb5-kdc using *service* command. However, if i change the order using either update-rc.d or insserv slapd fails to start and hence krb5-kdc fails to start.

The only error I see in the logs is 
> slapd[2794]: daemon: bind(9) failed errno=99 (Cannot assign requested address)While slapd is configured to bind to an IP alias, I don't understand why that IP alias would not be available when slapd starts.

Any clues?

On the side note... when i was experimenting with insserv, it screwed up the default SNN links for all services altho it preserved the correct order.
Any way to return that to the default?

Thank you in advance.

AT.

---

### Post by headvampyre@hotmail.co.uk on 2011-03-06
Hi, is there any reason to start OpenLDAP before the KDC? If your using kerberos with LDAP, the Kerberos is gonna need to be started.

---

