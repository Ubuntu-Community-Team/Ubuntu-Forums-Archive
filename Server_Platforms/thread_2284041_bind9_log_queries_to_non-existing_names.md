---
title: "bind9: log queries to non-existing names?"
date: 2015-06-26
forum: Server Platforms
---

### Post by tom192 on 2015-06-26
Good evening

we have a lot of attacks from some IP-Addresses which queries non-existing names, e.g.

qE3LuAk8YLRp.mydomain.com
EvwGUvQG53qL.mydomain.com
643AFsN569CH.mydomain.com

I've enabled bind9 logging for every category and log "debug 3" Level - and I get 10's MB logfiles. But it Looks like there is no Information which just says something like:

named: x.x.x.x: asked for non-existent Name asd98fzhsdf89.mydomain.com

Isn't there a way to detect queries to undefined names?

Thanks a lot for any help in advance,
kind regards,
Tom

---

### Post by nerdtron on 2015-06-28
I'm not sure how to detect unwanted queries for public DNS. But here's  a link for hardening your BIND9 server (mid to lower part) [https://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics](https://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics)

---

### Post by tom192 on 2015-06-29
Thank you very much for your answer and idea!, 
unfortunately it does not solve this kind of attack.

We try PowerDNS and it looks like they already detects such attackers :-)

---

