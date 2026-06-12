---
title: "Question Regarding UFW Blocking ACK RST and ACK FIN"
date: 2009-11-17
forum: Server Platforms
---

### Post by jwindle on 2009-11-17
I keep getting lines like the following in my messages log.

```
Nov 16 09:19:36 mybcclb1 kernel: [1016503.630546] [UFW BLOCK] IN=vlan81 OUT= MAC=00:04:23:d1:b0:12:00:1f:ca:bb:f8:37:08:00 SRC=168.156.41.179 DST=134.39.81.160 LEN=40 TOS=0x00 PREC=0x00 TTL=128 ID=4907 DF PROTO=TCP SPT=60156 DPT=443 WINDOW=0 RES=0x00 ACK RST URGP=0 
Nov 16 09:19:55 mybcclb1 kernel: [1016523.521628] [UFW BLOCK] IN=vlan81 OUT= MAC=00:04:23:d1:b0:12:00:1f:ca:bb:f8:37:08:00 SRC=168.156.40.253 DST=134.39.81.160 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=55346 DF PROTO=TCP SPT=41155 DPT=443 WINDOW=65535 RES=0x00 ACK FIN URGP=0
```

This server is acting as a load balancer using LVS for some web server nodes.

134.39.81.160 is the IP LVS listens for traffic on.

I would think I want these packets to travel to LVS so the get forwarded to the web nodes.

Am I correct in my assumption and if so what's the best way to disable this?

Thanks.

---

