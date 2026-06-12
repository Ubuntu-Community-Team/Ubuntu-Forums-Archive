---
title: "Firewall rules for DNS Forwarding"
date: 2011-06-06
forum: Security
---

### Post by doas777 on 2011-06-06
I've been tightening down my firewall lately, and I find I have some questions about the appropriate stateful rules for my gateway. 

I have my own internal bind9 server, for my local domain, and I forward internal requests for public domains to OpenDNS servers. This server is not in a DMZ, but is instead behind an dynamic NAT. I do not accept queries from the public network, only responses.

I understand that DNS is primarilly a UDP protocol, so it can't pass through a stateful/nat. without a firewall allow. 

I've done a little reading and learned that bind9 does not run 53 <-> 53 anymore (is now >1024 <-> 53), and modified my config so it works like bind4 did, but I am concerned that this makes me less secure. additionally, I'd really rather not have a completely open 53 rule, but it seems that if I constrain 53 traffic to my known forwarders, it interfers with some of my network services like transmission.

so, what firewall rules would you guys recommend for recieving forwarded DNS query responses to my server?

---

### Post by doas777 on 2011-06-08
bump.

---

