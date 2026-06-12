---
title: "Permission denied to read /proc/net/sockstat as the running process' user"
date: 2019-08-01
forum: Server Platforms
---

### Post by zeroburn on 2019-08-01
Hello there, 

I'm currently baffled by what's going on here. While I was installing [Netdata ]("https://docs.netdata.cloud/docs/what-is-netdata/") I realized that it was unable to monitor several system functions, for example the network sockets. A look at its logs and several "permission denied" entries showed up, all pointing to the /proc files it needed to read to collect the server's status.

This happened in two servers, and both had gone through an upgrade from 14.04 LTS to 18.04 LTS, following the standard release upgrade procedure. Everything worked out correctly and I had not spotted any issues until this. 

I started gathering differences from a fresh 18.04 LTS install where netdata works perfectly, and all I can see is that the /proc/[pid] folders have slightly different permissions, for example:

Broken systems have:
```
dr-xr-x--- 7 netdata  root    0 Aug  1 14:52 36440/
```

Working systems have:
```
dr-xr-xr-x 9 netdata  netdata    0 Aug  1 04:07 3534/
```

These are all machines hosted in OVH, and the other major difference is the kernel they're running:

Broken systems use:
```
3.14.32-xxxx-grs-ipv6-64
```

Working systems use:
```
4.15.0-55-generic
```

Replacing the kernel to check whether or not it would fix this issue is a risky move (might lack the correct raid modules) and these are production servers that I can't afford to stay offline for extended time (at least for non critical maintenance, which this isn't). I am wondering if anyone here can fill my knowledge gap regarding /proc and point me in a possible direction to a less invasive solution.

Thanks in advance for any input you can share, it will be very much appreciated!

---

