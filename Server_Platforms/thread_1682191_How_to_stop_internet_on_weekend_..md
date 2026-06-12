---
title: "How to stop internet on weekend ."
date: 2011-02-05
forum: Server Platforms
---

### Post by honey_bee on 2011-02-05
I am using squid in my ubuntu box. I want to allow my office staff that they may use internet from Monday to Friday.**The IP range that they are using is 192.168.1.20. to 192.168.1.50**
squid.conf file under acl tag

[PHP]acl weekend time A S 00:00-23:59 
acl myoffice src 192.168.1.20 192.168.1.50/24 
http_access deny myoffice 
[/PHP]please guide me that is it correct or I have to add some things more  to stop internet access only on Saturday and Sunday.

thanks in advance for guidance.
honey

---

### Post by SeijiSensei on 2011-02-05
```

acl weekend time A S 00:00-23:59 
acl myoffice src 192.168.1.0/24 
http_access deny myoffice weekend
http_access allow myoffice

```

The first http_access statement creates a rule which is true when both myoffice and weekend are true.  If there are other networks using the proxy, this would only affect machines in 192.168.1.0/24.

If there are no other networks then you can simplify the rules like this:

```

acl weekend time A S 00:00-23:59 
acl myoffice src 192.168.1.0/24 
http_access deny weekend
http_access allow myoffice

```

Note that this will disable access on the weekends even from the machine running squid, unless you have a prior rule that permits access from localhost at all times.

---

### Post by honey_bee on 2011-02-06
Thanks a lot the guidance.well can u suggest me any where i even restrict users through MAC address also.

---

### Post by SeijiSensei on 2011-02-07
Squid won't see the MAC addresses by default, only the connecting IPs.  I suppose you could try and write a custom add-on for squid that would consult the ARP table. That will only work for machines on the same IP subnet, though.  If you have intermediate routers, you won't be able to see the MAC addresses on the other segments behind those routers.

Are you worried about people changing their IP addresses to dodge the proxy?  If you're that paranoid, use fixed IP assignments in DHCP, then write iptables rules that only allow the assigned IP addresses to connect to squid.

---

