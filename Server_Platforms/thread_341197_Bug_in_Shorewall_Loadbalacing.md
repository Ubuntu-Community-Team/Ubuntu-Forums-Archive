---
title: "Bug in Shorewall Loadbalacing"
date: 2007-01-18
forum: Server Platforms
---

### Post by Phulerock on 2007-01-18
I configure load balancing on Edgy Eft server using this document 
[http://shorewall.net/2.0/Shorewall_and_Routing.html#id2460526](http://shorewall.net/2.0/Shorewall_and_Routing.html#id2460526)
and shorewall version is 3.0.7 that installed using apt-get.

After configured, I received this bug, so shorewall can not start when issued command shorewall start. 

iptables: Unknown error 4294967295
   ERROR: Command "/sbin/iptables -t mangle -A PREROUTING -m connmark ! --mark 0 -j CONNMARK --restore-mark" Failed

But everything is ok when I issued command #shorewall check

I see in this document that had talk about this bug at WARNING item, but I don't know how to do exactly with my iptables :

**Warning**

*iptables 1.3.1 is broken with respect to CONNMARK and iptables-save/iptables-restore. This means that if you configure multiple ISPs, shorewall restore may fail. If it does, you may patch your iptables using the patch at [http://shorewall.net/pub/shorewall/contrib/iptables/CONNMARK.diff](http://shorewall.net/pub/shorewall/contrib/iptables/CONNMARK.diff).*

Everybody known how to do exactly ?

---

### Post by nboom on 2007-04-02
shorewall show capabilities will show that you probably are missing connmark support.  I'm am currently trying to include connmark support by no luck so far...

---

