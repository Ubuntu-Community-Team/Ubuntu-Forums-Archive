---
title: "high availability web server, mail servers, and dns server"
date: 2008-10-24
forum: Server Platforms
---

### Post by chriswebb18 on 2008-10-24
OK, to start, here is my end goal:
2 loadbalancing servers running heartbeat to control data flow
2 web servers to receive requests from load balancers
2 mail servers (can heartbeat also handle mailflow?)
2 dns servers, for internal use at first, but then later as public dns servers

-i have 2 web servers currently, one is just an image of the other that i can switch in in case of a hardware failure until hardware is replaced and data restored.

-i know how to configure heartbeat for controlling flow of web sites, and i can configure bind for internal use.  i am a microsoft exchange sys engineer, but with linux, especialy no gui, i don't know what hardware would be sufficient for my needs

-i have 2 opteron quad-core 2.4 Ghz with 6GB ram for my web servers.  

-i do not know how important ram and proc is on the loadbalancers, so any recommendations there would be helpful.  

-i host 22 different sites on my web servers, and i want to ensure high availability for my clients.  the internal dns is simply because i find heartbeat is more efficient with an internal dns server.  they are not as much a priority, but eventually i would also like to host my own dns servers to teh public.  what hardware would be needed for a BIND server?  

-also, exchange takes quite a bit of resources, but it has the windows gui running as well.  i am not sure which program to use for my mail servers, yet.  any suggestions on the most efficient program and hardware recommendations would be appreciated.  

thank you all for your help

---

