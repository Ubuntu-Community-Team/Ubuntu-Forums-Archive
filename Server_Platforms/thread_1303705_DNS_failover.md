---
title: "DNS failover"
date: 2009-10-28
forum: Server Platforms
---

### Post by cdenley on 2009-10-28
In the near future, I will be adding another WAN connection to our network. We will have two internet connections from two ISP's. Each server will be accessible through either WAN connection (different IP's). I want some kind of DNS failover, so if the primary WAN connection goes down (such as a service outage), all our domain names will resolve to the secondary WAN's IP's. Obviously, I would set a lower TTL so the failover wouldn't take too long. My idea was to use two DNS servers, one available through each WAN connection. The primary DNS server would be used until the primary WAN connection failed, then the secondary DNS would kick in through the secondary WAN connection, correct?

---

### Post by koenn on 2009-10-28
> **cdenley said:**
>  My idea was to use two DNS servers, one available through each WAN connection. The primary DNS server would be used until the primary WAN connection failed, then the secondary DNS would kick in through the secondary WAN connection, correct?
2 DNS servers, one on WAN 1, one on WAN 2, right ?

sounds like a plan, 
but to be sure, you'd need to find out how a dns server would process the list of name servers for your domain;
if they are tried in order until one replies, then your plan would work, I think.
So we need to find a spec of the DNS protocol ... ?

---

### Post by cdenley on 2009-10-29
> **koenn said:**
> 2 DNS servers, one on WAN 1, one on WAN 2, right ?

sounds like a plan, 
but to be sure, you'd need to find out how a dns server would process the list of name servers for your domain;
if they are tried in order until one replies, then your plan would work, I think.
So we need to find a spec of the DNS protocol ... ?

Yes. I was hoping someone with a better understanding of the DNS protocol than myself would comment on whether this was a good idea. I found this document, which seems relevant.
[http://tools.ietf.org/html/rfc2182](http://tools.ietf.org/html/rfc2182)
It seems when resolving domains, one server will not be favored over the other. If I understand correctly, half the users would have my domains resolved to my "secondary" WAN. This might actually be better, like load-balancing. If one DNS server becomes unavailable, the other should be used, since this is the whole point of having more than one.

I'll have to re-read that later, do some more research, then maybe re-think my approach.

---

