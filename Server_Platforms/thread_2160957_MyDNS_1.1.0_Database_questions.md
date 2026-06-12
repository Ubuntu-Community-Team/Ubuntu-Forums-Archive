---
title: "MyDNS 1.1.0 Database questions"
date: 2013-07-08
forum: Server Platforms
---

### Post by basicfreak on 2013-07-08
Ok, I don't know how to set up an entry it seems.
I tried following the datasheet for MyDNS to no avail.

my entry is:

```
Table rr


id    =    1
zone    =    1373306471
name    =    example.com
type    =    A
data    =    10.0.0.1
aux    =    0
ttl    =    86400


Table soa


id    =    1
origin    =    example.com
ns    =    example.com
mbox    =    example.com
serial    =    1373306471
refresh    =    28800
retry    =    7200
expire    =    604800
minimum    =    86400
ttl    =    86400

```

and the output of the debug screen:
```
mydns[31896]: optional 'active' column found in 'dns_soa' table
mydns[31896]: optional 'xfer' column found in 'dns_soa' table
mydns[31896]: optional 'active' column found in 'dns_rr' table
mydns[31896]: mydns 1.1.0 started Mon Jul  8 21:10:10 2013 (listening on 5 addresses)
mydns[31896]: 08-Jul-2013 21:10:30+391593 #0 43879 UDP 127.0.0.1 IN A example.com. REFUSED Zone_not_found 1 0 0 0 LOG N QUERY ""
mydns[31896]: 08-Jul-2013 21:10:30+392749 #1 19364 UDP 127.0.0.1 IN A example.com. REFUSED Zone_not_found 1 0 0 0 LOG Y QUERY ""

```

and the output of host example.com localhost:
```
Using domain server:
Name: 127.0.0.1
Address: 127.0.0.1#53
Aliases: 


Host example.com not found: 5(REFUSED)

```

Anyone have an example for an entry I can use, all I want is any entry pointing to 10.0.0.1.

---

### Post by basicfreak on 2013-07-09
Ok, I figured out some of this - now I'm stuck at:
```
UDP 127.0.0.1 IN A example.com. NXDOMAIN No_matching_resource_records 1 0 1 0 LOG Y QUERY ""
```

anyways the first issue was a period after the domain name that was missing, what do I need to set now for a NXDOMAIN record

---

