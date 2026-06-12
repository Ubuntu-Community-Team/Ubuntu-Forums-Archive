---
title: "help with squid"
date: 2006-12-24
forum: Server Platforms
---

### Post by faizy on 2006-12-24
hey ppl,

i need help in setting up squid on my ubuntu edgy 6.10 ... i have 2 ethernet cards on my pc .. eth0 and eth1 .. eth0 is connected to the internet and it behind a proxy (say xxx.xxx.xxx.xxx.:8080)(and wont work without using a proxy) .. and eth1 is connected to a local network .. what i need to do is share eth0's connection on eth1 along with transparent proxying with squid ... how can i do this ?... ive been snoopin around squid but cant make it ,...](*,) ](*,) ](*,)

---

### Post by jonathan.lees on 2006-12-26
Hi Faizy,
If I'm right eth0 is connected to the internet and is behind a proxy. You therefore have an upstream proxy and you need to tell squid this. Open the squid.conf file and under Options which affect the neighbor selection… at the bottom of the section enter the following for upstream proxy:
cache_peer proxy 10.40.0.2 parent 80 0 no-query default login=Username:Password
(where 10.40.0.2 is the IP of the upstream proxy, 80 is the Port)

Here's a link for configuring transparency:

[http://wiki.squid-cache.org/SquidFaq/InterceptionProxy](http://wiki.squid-cache.org/SquidFaq/InterceptionProxy)

Jonathan

---

