---
title: "ubuntu server 9.04 with domain name"
date: 2009-08-17
forum: Server Platforms
---

### Post by themoddingden on 2009-08-17
hi;
I have a server and i have a domain name(godaddy.com).
Now I can connect to the server from the LAN but,
others can't see it on the net it times out.
I set the lan to static in ubuntu 9.04 64bit and in my netgear (wgr614)router.
I put ddclient in as well.
thinking it was a dns issue.
I keep my port to default as well.
I forwarded port 80 through the router as well.
I have the domain pointing to my lan ip as well as dyndns host name via cname entry.
But this hasn't helped.
I thought it was working but found out it works just for me :(
any help anyone can give me would be great.

---

### Post by Cheesemill on 2009-08-17
If you're sure that you are forwarding the ports on your router correctly then it could be your ISP. Alot of them block access over port 80 on residential broadband accounts.
 
Can you access it externally by using your external IP?

---

