---
title: "BIND Quirks"
date: 2007-12-09
forum: Server Platforms
---

### Post by joehack on 2007-12-09
Hello

I've recently setup my private DNS server for my network. It works really fine, as long as I am connected to the wired network. As soon as I switch to WLAN, I get strange responses with nslookup.

Wired LAN is 192.168.1.0
Wireless LAN is 192.168.2.0
DNS server is 192.168.1.10

When I make a lookup for e.g. [www.panasonic.com](www.panasonic.com) I get 
```
> 
www.panasonic.com
Server:		192.168.1.10
Address:	192.168.1.10#53

** server can't find www.panasonic.com.home.mydomain.com: NXDOMAIN

```

The same request, with the wired LAN:
```

> www.panasonic.com
Server:		192.168.1.10
Address:	192.168.1.10#53

Non-authoritative answer:
Name:	www.panasonic.com
Address: 140.212.202.244

```

The 2 networks are linked with WRAP board running m0n0wall with 3 LAN ports.  The routing itself seems to work.

Please help!

Regards,
Jochen

---

### Post by bnuytten on 2007-12-15
What happens: nslookup tries to resolve the FQDN [www.panasonic.com](www.panasonic.com), which probably fails, it then looks at /etc/resolv.conf which suggests adding home.mydomain.com to the FQDN, which off course will fail too. Resulting in the error message:
```
** server can't find www.panasonic.com.home.mydomain.com: NXDOMAIN
```

Can you post the output of another resolving tool like nslookup:
```
dig @192.168.1.10 ubuntuforums.com
```

---

### Post by joehack on 2007-12-15
After reading further, I am convinced, it is a Mac OSX issue. 

UBUNTU just flies :-)

Thanks for your help!

Regards,
Jochen

---

