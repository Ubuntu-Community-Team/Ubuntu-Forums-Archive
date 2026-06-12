---
title: "squid_ldap_group problem"
date: 2008-10-01
forum: Server Platforms
---

### Post by xyrer on 2008-10-01
Hi, I've been using squid with ldap authentication and it works pretty good, but now I need to separate access in groups, I've been searching and this is all I've found:

```
/usr/lib/squid/squid_ldap_group -R -b dc=proxy2 -f (&(objectclass=person) (sAMAccountName=%v) (memberof=cn%a,ou=employees,dc=proxy)) -h localhost
```

but gives me ERR with every user I input.

this one works: ```
/usr/lib/squid/ldap_auth -b ou=employees,dc=proxy -f uid=%s -h localhost
```

My ldap server is: cn=internet,ou=employees,dc=proxy

and there's a couple of groups more, cn=chief and cn=whitelist

I've seen people writing about %u and stuff but I don't fully undestand.

I appreciate any help, thanks.

---

