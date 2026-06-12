---
title: "DNS tunnel server"
date: 2009-11-27
forum: Server Platforms
---

### Post by famer on 2009-11-27
Hi everyone. I want to set up DNS server in my local network that just a proxy for public DNS server for second level domains. But returns ip of himself for some special domains(exactly for first level).
The idea is: if some one who use this DNS go to [http://images/](http://images/) or [http://radio/](http://radio/) it have to go to my web server, otherwise to the normal DNS.
Hope for help.
P.S. Sorry for bad english.

---

### Post by Lars Noodén on 2009-11-27
Then one of the tools worth looking at would be [dnsmasq](http://www.thekelleys.org.uk/dnsmasq/doc.html)

---

### Post by famer on 2009-11-27
Thanx alot Lars Noodén!
For those who will use forum search:
you just need edit /etc/hosts and start dnsmasq. It will use resolving using hosts file first.

---

### Post by Lars Noodén on 2009-11-29
Another way, which keeps all your changes in a single place, specifically the dnsmasq configuration file, is to use the *address* configuration directive to assign addresses.  

```

address=/images/192.168.0.198
address=/radio/192.168.0.199

```

It also works for IPv6 addresses, which would be advantageous to start using.

---

