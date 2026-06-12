---
title: "Insane Squid Question"
date: 2007-11-14
forum: Server Platforms
---

### Post by Cwolly on 2007-11-14
Ok, my scenario is as follows. I've got squid up and running on Gutsy server. It works great as a caching server, which is exactly what I want to use it for. However, I also have a comercial filtering box on the same network. I want to route my http traffic to the squid box, have the squid box query the content filter and if acceptable, come back to the user. In a hierarchy sense I am talking

content filter
\/
gutsy squid box
\/
client

So essentially I need to find a way for the squid box to forward requests from port 80 through the cache, to port 3128 on the content filter, and then have the request go back through the squid box to the client.

I was thinking I could use the squid box as a gatway for the client, which would by default then be accepting incoming requests on port 80.

I am racking my brain on this one and I just cant get the correct forwarding sequence. Any suggestions?

Thanks in advance,
Cwolly

---

### Post by pete.dawgg on 2007-11-19
so the commercial box acts as a (kind of) proxy in itself? in transparent mode?  if the clients use it as proxy explicitly (non-transparent) you don't need to route any traffic, just tell squid to get its content from the commercial box:
> cache_peer <commercial.box>  parent <PORT> 0 no-query default in squid.conf.
depending on how strict the filtering is supposed to be you can configure squid NEVER to get any content from the origin-servers directly, eg
```
acl restricted-clients src <client ips or local net>
never_direct allow  restricted-clients
``` or you configure the network accordingly so squid can't get anything from the outside networld (ugly way) ;)

same thing applies to transparent mode, except you can only have ONE machine acting as transparent proxy, so transfer the packet-mangling stuff from the comm-box to squid and have the comm-box accept only packets from squid.

the perfomance might be better if you could use the comm-box as a pre-filter before squid, since all the filtered requests are killed BEFORE the cache (squid) is bothered with them:
non-transparent (explicit proxy in client browser)
client GET url from comm-box->  comm-box: filter -> if allowed -> SQUID: from cache or origin server
[--->if not allowed: error handler ->stop ]

transparent (no proxy in client-browsers):
client GET url from origin-server -> packet mangled to comm-box -> filter -> if allowed -> SQUID: from cache or origin server
[--->if not allowed: error handler ->stop ]

good luck!

---

