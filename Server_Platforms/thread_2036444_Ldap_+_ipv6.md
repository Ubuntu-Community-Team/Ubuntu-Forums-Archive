---
title: "Ldap + ipv6"
date: 2012-08-01
forum: Server Platforms
---

### Post by paco699 on 2012-08-01
Hello all!


I have 2 OpenLDAP servers. One with ubuntu-10.04 (package openldap-2.4.21) and the other with ubuntu-12.04 (package openldap-2.4.28 ). 
I have the project to configure a IPv6 network.

My question is:
How can i say if i have the IPv6 support enable or disable on OpenLDAP?


Thank you very much!

---

### Post by paco699 on 2012-08-03
Hello everybody,


There is the -h option in man 8 slapd.
Or I found an another way to see it:
```
# netstat -pantu
tcp6    :::389   :::*   LISTEN   687/slapd
```Just for information for people who pass by this post:
There is nothing to do with ipv6 in openldap.
Like you say it anomie, "By default, it listens on all addresses.".
What means that the type of connection (ipv4 or ipv6) to search the information in the database depends of the consumer.
If the consumer speaks ipv4, the server will answer it ipv4.
If the consumer speaks ipv6, the server will answer it ipv6.
Don't look farther.
If you want to slapd listen specifically on a type of network (man 8 slapd):
-4 Listen on ipv4 addresses only
-6 Listen on ipv6 addresses only
It's important to read the "schemas" to understand the format and how to implement/integrate informations into the database of openldap.
And, if there is no way to implement ipv6 informations, contact the author of the schema.

Have a nice day :cool:

---

### Post by bachawiss on 2013-03-11
Can you help me to configure my openldap server in ipv6 network
it works in ipv4
but when i replace the host address to ipv6 address in ldap.conf address,
and the ldap://example.com
it don't works,and don't find users

---

