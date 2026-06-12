---
title: "Server Computer Slows clients"
date: 2009-08-26
forum: Server Platforms
---

### Post by prongs_386 on 2009-08-26
I have ubuntu server 9.04 and I have a ppoe client setup on one interface and I'm routing the connection through the other interface.

The internet works perfectly from the server computer.. but on any clients using the server as a gateway, it runs really slowly.

I use webmin to monitor services etc and setup my firewall from there. I initially thought it was todo with my firewall however I'm still getting the problems with everything set to accept.(I'm not planning on leaving it like this)

I did have this setup and working perfectly for a while by just routing from interface A to B. But then i took my hardware router out of the equation and started using the pppoe client. I'm not entirely sure if thats what my issue is because at the time of doing that i set up a few other services like mysql etc.

A final thing i noticed was when trying to set a static ip address and specify my isp dns servers manually, the internet doesn't work at all.

A traceroute to my dns server from client and server return the same hops and time, apart from a 1ms delay at the server computer.

I'm sorry this is a mess of information, I'm not really looking for a quick fix because Idoubt there is one.. but If anyone can offer suggestions on how I can go about testing the system to try and find my problem I would really appreciate it. Thanks

---

### Post by prongs_386 on 2009-08-26
Ok,

After a bit of screwing around I found that the speed was back to normal if I only routed to my second interface which had access to the internet via a different router.

Ideally I would want my server to act as the pppoe client... but that is too slow when trying to route the connection.

I used the standard pppoe client for ubuntu.. it provided 2 new interfaces, pppoe and dsl-provider.. dsl-provider is created by the pppoe client and I think it was their intention for me to route via that interface.. however that wouldn't work at all so I just routed via the pppoe interface which worked apart from the speed issue.

Does anyone know more about this?

---

