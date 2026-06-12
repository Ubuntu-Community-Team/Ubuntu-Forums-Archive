---
title: "bind wont respond (localhost works)"
date: 2010-11-09
forum: Server Platforms
---

### Post by HBE66 on 2010-11-09
hi everyone

ive installed bind9 on ubuntu server 10.10

i created a new zone xy.loc. with the following records:
xy.loc.  NS  localhost.
xy.loc.  A  10.10.0.2
server.xy.loc.  CNAME  xy.loc.
10.10.0.2.xy.loc.  PTR  server.xy.loc

the bind service is running and i can resolve the adress from localhost
but when i try resolving it from an other machine on the network i get no responce

theres no firewall between the two machines

has anyone got a clue why this could be?
does ubuntu run some sort of local firewall, where i first have to open a port?

thank you!

---

