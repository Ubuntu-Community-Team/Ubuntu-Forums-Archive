---
title: "ping calls wrong IP address"
date: 2007-11-27
forum: Windows
---

### Post by dhtseany on 2007-11-27
Hey all,

I know this is something stupid but I can't figure it out :(

The box in question is running XP Pro.

We have 2 different and completely segregated networks running: 192.x.x.x and 172.x.x.x.

I have a PC on the 172.x network that is being a jerk. If I try and ping one of my servers (we'll call the UNC "server1"), ping errors out because it is trying to ping the server's 192.x address, not the 172.x address that it's supposed to. The funny thing is if I navigate through windows to \\server1 everything pops up the way its supposed to. The problem is that an application we run is erroring out because it's trying to connect to the 192.x network.

I've done **ipconfig /dnsflush**, then **ipconfig /release and ipconfig /renew** but the problem still happens.

I hope all that made sense...

Any suggestions?

Thanks,

Sean

PS- If it matters, both 192.x and 172.x are running 255.255.255.0 as their subnet address.

---

### Post by dhtseany on 2007-11-27
*Bump* :)

Sorry, this is kinda important

---

