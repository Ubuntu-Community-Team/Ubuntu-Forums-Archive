---
title: "bind9 - RFC4183 - Reverse DNS Subdelegation assistance"
date: 2013-02-13
forum: Server Platforms
---

### Post by louis vitton on 2013-02-13
Hey guys,

I have a VPS and i am setting up RFC4183 - Reverse DNS Subdelegation so that the IPs i have can get their reverse DNS from my server instead of the host companys dns server.

I have read up on this and before i do it just wanted to check the format and ensure i have the detials correct.
first some details
```

IP: 199.71.91.50/24
broadcast 255.255.255.0
domain: test.com
zone file name in named.conf
50-1.91.71.199.in-addr.arpa.
and my PRT record would look like below;
50 IN PTR test.com. 

```
Cheers

---

### Post by louis vitton on 2013-02-14
bump

---

### Post by SeijiSensei on 2013-02-14
You need to discuss this with your ISP.  Ask them how the zone should be specified.  I've only used delegation on octet boundaries, but I do know the name has to match the associated NS record in the ISP's DNS server.  

They should have a template zone file you can use.

---

### Post by louis vitton on 2013-02-14
> **SeijiSensei said:**
> You need to discuss this with your ISP.  Ask them how the zone should be specified.  I've only used delegation on octet boundaries, but I do know the name has to match the associated NS record in the ISP's DNS server.  

They should have a template zone file you can use.

Cheers i will contact the provider.

---

