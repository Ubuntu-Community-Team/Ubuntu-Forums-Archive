---
title: "squid strange client connection"
date: 2009-07-01
forum: Server Platforms
---

### Post by tr3s on 2009-07-01
hi!

i'm running squid and implemented delay pools properly to 192.168.0.0 192.168.1.0 and 192.168.2.0 networks. i use sqstat to monitor live squid connections. all of the client connections are following the delay pool's bandwidth limit except for one connection which is registered as 127.0.0.1 and is not governed by delay pools because it's eating up all the bandwidth. i'm sure it is someone on the network and it is not the squid server downloading.

what could be happening? how can i inspect and fix this?

thanks much

---

### Post by tr3s on 2009-07-01
i found out from the squid logs that the connection is an application/octet-stream type, probably something not really directly using squid. 

the workaround i made is trap the ports 1024-65535 (well, these ports are the safest based on my research) and redirected to squid's port 3128. now the actual ip address of where the connection is coming from is now registering in [sqstat]("http://samm.kiev.ua/sqstat/").

---

