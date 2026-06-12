---
title: "Appache ProxyPass filling up my logs"
date: 2008-07-24
forum: Server Platforms
---

### Post by drubin on 2008-07-24
Hi

I have been searching for a while but I can not seem to figure out how to stop just the mod_proxy from filling up my error logs every connection that connects. 

I would like to keep the rest of my logging level at "debug" but just turn off the ProxyPass  logging level.. or at least a higher level.

> 
[Thu Jul 24 13:24:09 2008] [debug] mod_proxy_http.c(1448): proxy: start body send
[Thu Jul 24 13:24:09 2008] [debug] mod_proxy_http.c(1537): proxy: end body send
[Thu Jul 24 13:24:09 2008] [debug] proxy_util.c(1816): proxy: HTTP: has released connection for (127.0.0.1)
[Thu Jul 24 13:24:09 2008] [debug] mod_proxy_http.c(54): proxy: HTTP: canonicalising URL //127.0.0.1:7070/test/
[Thu Jul 24 13:24:09 2008] [debug] proxy_util.c(1378): [client 192.168.0.35] proxy: http: found worker [http://127.0.0.1:7070/test/](http://127.0.0.1:7070/test/) for [http://127.0.0.1:7070/test/](http://127.0.0.1:7070/test/), 
[Thu Jul 24 13:24:09 2008] [debug] mod_proxy.c(756): Running scheme http handler (attempt 0)
[Thu Jul 24 13:24:09 2008] [debug] mod_proxy_http.c(1662): proxy: HTTP: serving URL [http://127.0.0.1:7070/test/](http://127.0.0.1:7070/test/)
[Thu Jul 24 13:24:09 2008] [debug] proxy_util.c(1798): proxy: HTTP: has acquired connection for (127.0.0.1)
[Thu Jul 24 13:24:09 2008] [debug] proxy_util.c(1858): proxy: connecting [http://127.0.0.1:7070/test/](http://127.0.0.1:7070/test/) to 127.0.0.1:7070
[Thu Jul 24 13:24:09 2008] [debug] proxy_util.c(1951): proxy: connected /test/ to 127.0.0.1:7070
[Thu Jul 24 13:24:09 2008] [debug] proxy_util.c(2141): proxy: HTTP: connection complete to 127.0.0.1:7070 (127.0.0.1)


Thanks

---

