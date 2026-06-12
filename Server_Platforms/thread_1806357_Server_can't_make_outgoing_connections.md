---
title: "Server can't make outgoing connections"
date: 2011-07-17
forum: Server Platforms
---

### Post by esdfwasd on 2011-07-17
Hello, I have a ubuntu 10.04 dedicated server that I am having problems with. It intermittently cannot connect to any other servers outside its network.


```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
^C
--- 8.8.8.8 ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 7008ms
```
(I have tried a bunch of other ips too and none outside its network are pingable)

I'm not sure if this is a problem with my server or a problem with the networking outside the server. I have been emailing my server provider and they keep on insisting the problem is with the server and that their network is working fine. Apparently all of their other servers work and they can login into the gateway and ping 8.8.8.8 from there. So they just want to reinstall the OS, but I thought I'd post here to see if anyone has any ideas. 


Here is some info I have gained while troubleshooting:

I haven't changed any settings at all on the server for months. I haven't done any updates for about a week.

The problem started about 24 hours ago.

The strangest thing is that this is intermittent, there have been a few times in the last 24 hours where I have been able to ping 8.8.8.8 or other ips, but 98% of the time I can't. I have also tried rebooting the server, which had no effect.

I can ping the gateway, and I can ping other servers on the same subnet.

I can ssh onto the server from my home internet connection, and I can view webpages on apache, so incoming connections work.


does anyone have any ideas as to what might be wrong?

---

### Post by HermanAB on 2011-07-18
Intermittently - bah - hard to fix these ones...

Check these things:
1. ifconfig - packet loss means bad cable or ethernet adaptor.
2. route - verify default route and ensure that you have only one route outgoing.
3. Check your internet router/gateway.
4. dig - test all the DNS listed by the DHCP server.

Hope that helps!

---

