---
title: "minimal build for a DHCP server?"
date: 2009-12-06
forum: Server Platforms
---

### Post by Andrew Buchinger on 2009-12-06
can someone please point me torwards a minimal build for a DHCP server? 

I will need one that is capable of doing PXE boots. I am looking at useing ISC DHCP but I don't know what platform to base it off of. I would prefer the platform be minimal.

(and now a word from my 3 year old who wants to click the "M&M's")

:p:KS:KS:D:P:P

---

### Post by Lars Noodén on 2009-12-06
> **Andrew Buchinger said:**
> can someone please point me torwards a minimal build for a DHCP server? 

I will need one that is capable of doing PXE boots. I am looking at useing ISC DHCP but I don't know what platform to base it off of. I would prefer the platform be minimal.


The either of the packages [dhcp3-server](http://linux.die.net/man/5/dhcpd.conf) or [dnsmasq](http://www.thekelleys.org.uk/dnsmasq/doc.html) will do dhcp and pxe boot.  

They're both powerful and flexible in slightly different ways.  dnsmasq has a built-in tftp server, so in some ways it's easiest to set up.

---

