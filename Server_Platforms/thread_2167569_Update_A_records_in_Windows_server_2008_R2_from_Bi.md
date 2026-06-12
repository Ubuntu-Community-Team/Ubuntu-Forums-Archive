---
title: "Update A records in Windows server 2008 R2 from Bind9"
date: 2013-08-14
forum: Server Platforms
---

### Post by Drenriza on 2013-08-14
Hey guys.

When you have a DHCP and a DNS server on the linux platform you can dynamically update the A record, for the DNS service when a new DHCP address is given out.
By specifying a key for information exchange.

Is their a way that the same thing can be accomplished when using a Windows server 2008 R2 for DNS and Ubuntu for DHCP?

Thanks on advance.
Kind regards.

---

### Post by sandyd on 2013-08-14
> **Drenriza said:**
> Hey guys.

When you have a DHCP and a DNS server on the linux platform you can dynamically update the A record, for the DNS service when a new DHCP address is given out.
By specifying a key for information exchange.

Is their a way that the same thing can be accomplished when using a Windows server 2008 R2 for DNS and Ubuntu for DHCP?

Thanks on advance.
Kind regards.

Try something like [http://blog.michael.kuron-germany.de/2011/02/isc-dhcpd-dynamic-dns-updates-against-secure-microsoft-dns/](http://blog.michael.kuron-germany.de/2011/02/isc-dhcpd-dynamic-dns-updates-against-secure-microsoft-dns/)

Basically, you set the DHCP server to perform dynamic DNS updates against the microsoft DNS server - which you have to enable dynamic DNS on.

If your strapped for time, setup the DNS Zone on Microsoft DNS server to be secondary, and setup bind9 on Ubuntu, and make it primary.
Allow slave updates from the Microsoft DNS server, and off you go!

---

