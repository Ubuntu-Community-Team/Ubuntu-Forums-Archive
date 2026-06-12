---
title: "Can't get Bandwidthd working properly"
date: 2010-08-20
forum: Server Platforms
---

### Post by synd7 on 2010-08-20
Recently our houses internet usage has skyrocketed and i'm trying to keep an eye on it using bandwidthd (installed on the server). It installed fine and counts traffic fine, the problem is we have a server that hosts our music/movies/etc and when people pull music off the server it skews their bandwidth usage.

I'm looking for a way to exclude all traffic on the local network and only count internet traffic.

This is the filtering part of the config file
```
#Libpcap format filter string used to control what bandwidthd see's
#Please always include "ip" in the string to avoid strange problems
filter "ip and not ((src net 192.168.0) and (dst net 192.168.0))"

```

Using this results in no traffic being counted, local or external.
Why wouldn't this be working?

All computers on the network have IPs in the range 192.168.0.x
The server IP is 192.168.0.150

---

### Post by lombaardcj on 2010-08-20
What software did you install to perform your accounting?  I would like to do the same for my setup at home.

---

### Post by CharlesA on 2010-08-20
You would need to place it between the local machines and the internet.

You could set it up as a router, but it would be better to just use a router that can use dd-wrt, as it has bandwidthd installed.

If you've got a file server also handling routing, you are putting all yer eggs in one basket and if that server is compromised, you are boned.

---

