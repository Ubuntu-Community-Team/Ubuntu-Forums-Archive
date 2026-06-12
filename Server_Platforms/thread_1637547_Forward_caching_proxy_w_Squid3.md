---
title: "Forward caching proxy w/ Squid3"
date: 2010-12-04
forum: Server Platforms
---

### Post by banana989 on 2010-12-04
I'm trying to get squid3 to act as a proxy cache on a machine. I want all other client machines to point to the IP of this machine (in Firefox) when they want to use it as a forwarding cache. 

My squid3 proxy/cache works when I am on the server and point FF to localhost:3128. If I point it to the server's IP (still the same machine) I always get acccess denied. 

I thought this line was supposed to do it 

```
acl home_networks src 192.168.0.0/24
```

But alas- it does not.

---

