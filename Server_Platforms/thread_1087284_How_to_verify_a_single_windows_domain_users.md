---
title: "How to verify a single windows domain users?"
date: 2009-03-04
forum: Server Platforms
---

### Post by ballatong on 2009-03-04
I can already achieve squid authentication with windows domain group ,but how to verify a single windows domain users?

squid.conf

external_acl_type NT_global_group %LOGIN /usr/lib/squid/wbinfo_group.pl
acl ProxyUsers external NT_global_group NTusers
acl AuthenticatedUsers proxy_auth REQUIRED
http_access allow AuthenticatedUsers ProxyUsers

I used debian 4.0

---

### Post by HermanAB on 2009-03-05
Authenticating against Active Directory is a non-trivial problem.  It can be done with Likewise or Samba Winbind:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

Cheers,

Herman

---

### Post by ballatong on 2009-03-05
yes I already join windows domain
and I can already achieve squid authentication with windows domain group,that's pass,like above, now I want to verify a single windows user,but how to do....

---

