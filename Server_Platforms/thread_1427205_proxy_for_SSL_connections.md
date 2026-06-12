---
title: "proxy for SSL connections?"
date: 2010-03-11
forum: Server Platforms
---

### Post by bertmanphx on 2010-03-11
Hello,
I have a small business that I run Squid and Dansguardian on Ubuntu for network proxy filtering, among other things.  This works great, but does not block SSL connections on Port 443, such as https proxies.  I understand that this is because this type of configuration is a "transparent proxy".  

Is there a way to set one up "non-transparent" and, would that filter https?

I cannot blanket block 443, because some sites need it.

  I have read that one can re-compile Squid to work with SSL, but not being a super guru, not sure of the implications of doing that.
  
I am open to any suggestions on how to do this.  any ideas?  I'm sure that somebody is managing to do this.

Regards,

bertmanphx

---

### Post by cdenley on 2010-03-11
I'm not familiar with squid or dansguardian, but the only way to filter SSL web connections would be by IP. You cannot filter by content because the encryption must be negotiated between the browser and the destination server and the proxy will not be able to see what kind of requests are being sent (no hostname) or what kind of content is being served.

I use a firewall to filter web traffic, and simply whitelist hostnames I need to allow access to. Of course, the traffic is only filtered by IP, so when the DNS record for a hostname has a short TTL and changes frequently, this can be problematic.

---

### Post by JSeymour on 2010-03-11
Would using iptables and putting in the necessary rules to control source and destination IPs work for you?

Jim

---

### Post by bertmanphx on 2010-03-11
JSeymour,
I suppose that would work.  Although I have not done it before, am sure I could read up on it and get it implemented.   
Right now, the Gateway is a router, and does not have that kind of functionality.  
I suppose I would have to setup a DNS server?  And, point the client machines to it for resolution?

Right now, the client Firefox's have the proxy settings for port 80 traffic only.  I could set the ssl traffic to point somewhere else (DNS server?) with this filtering capabilities via IP Tables?

bertmanphx

---

### Post by hessiess on 2010-03-11
You CANNOT proxy SSL and you CANNOT filter it. SSL provides a very strong level of encryption meaning that it is completely imposable to see inside an SSL connection. Filtering SSL would be  the same as a man in the middle attack, which is exactly what it is designed to prevent.

The only way to `proxy' SSL is to pass it through as is.

---

### Post by cdenley on 2010-03-11
> **hessiess said:**
> You CANNOT proxy SSL and you CANNOT filter it. SSL provides a very strong level of encryption meaning that it is completely imposable to see inside an SSL connection. Filtering SSL would be  the same as a man in the middle attack, which is exactly what it is designed to prevent.

The only way to `proxy' SSL is to pass it through as is.

The only way without getting browser warnings about invalid or self-signed certificates. Even if you did manage to proxy SSL and configured all browsers to accept the proxy's certificate for all domains, the proxy would have to decide which SSL certificates for web server's it would accept, which would mean the users couldn't make exceptions for self-signed or expired certificates.

This is pretty much what I was trying to say, though.

---

### Post by bertmanphx on 2010-03-12
Hessiess,
Then, this tells me I can only block them by using a domain name filter, or at a dns?

bertmanphx

---

### Post by cdenley on 2010-03-12
> **bertmanphx said:**
> Hessiess,
Then, this tells me I can only block them by using a domain name filter, or at a dns?

bertmanphx

You can't filter SSL traffic based on domain name, only IP. You can create a list of domains then resolve their IP's and filter those IP's, but as I said, some domains change IP's constantly. You can filter DNS, but then they can always resolve domains with a different DNS server.

---

