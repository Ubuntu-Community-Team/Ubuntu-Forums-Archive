---
title: "DNS Bind across VLAN's"
date: 2010-09-23
forum: Server Platforms
---

### Post by wiz561 on 2010-09-23
Hi,

I have run into a strange problem.  I'm setting up a local network where there's multiple subnets (vlans).  I configured bind and it works fine on the DNS server.  I'm able to resolve any name and it properly forwards names to another dns server.  

However, with machines on other networks, I can only lookup names that I put in.  It does NOT forward other names (ie: google.com).  I get the following error message with nslookup.

** server can't find [www.google.com:](www.google.com:) NXDOMAIN

I was wondering, is there some sort of switch or trick to get bind to be able to forward lookups for everything, and not just the subnet it is running on?

Thanks

---

### Post by wiz561 on 2010-09-23
Added the following to 'options' and it worked....

<add trusted net acl section>


allow-query { trusted; };
        allow-recursion { trusted; };
        allow-query-cache { trusted; };
        version "go away";

---

