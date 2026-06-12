---
title: "chkrootkit result...anything to worry about?"
date: 2007-03-11
forum: Server Platforms
---

### Post by darkeale on 2007-03-11
i ran chkrootkit and it displayed this:-

Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[3669])

can someone tell me what this means? 

thanks

---

### Post by hda on 2007-03-11
```

man dhclient
DESCRIPTION
       The Internet Systems Consortium DHCP Client, dhclient, provides a means
       for  configuring  one or more network interfaces using the Dynamic Host
       Configuration Protocol, BOOTP protocol, or if these protocols fail,  by
       statically assigning an address.
```This listens for a DHCP server for dynamically allocated IP address configurations. It's harmless...

*hda*

---

