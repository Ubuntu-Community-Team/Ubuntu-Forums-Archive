---
title: "HAPROXY help - Need backend FQDN to resolve IPv6 (aaaa)"
date: 2016-02-04
forum: Server Platforms
---

### Post by john_d13 on 2016-02-04
Hello everyone my name is GD and I am new to the forums.  I have a specific question related to haproxy software.  I would like to proxy https traffic from my frontend listening on both v4/v6 dual stack interface to forward traffic to backend FQDN [www.example.com]("http://www.example.com") IPv6 addresses.   I can accomplish this by manually entering the v6 address but that would be volatile.  v4 and v6 records exist for [www.example.com]("http://www.example.com") but by default haproxy forwards to the v4 destination servers only.   Any way to force it to use v6?   I ran a capture and the server does not seem to be running and DNS lookups when the incoming request is initiated.   What mechanism does haproxy use to resolve the hostname?


Here is my config:

use-server [www.example.com]("http://www.example.com") if { req_ssl_sni -i [www.example.com]("http://www.example.com") }
  #server [www.example.com]("http://www.example.com") 2606:2800:220:1:248:1893:25c8:1946:443 check inter 10s fastinter 2s downinter 2s fall 1800   <<< Works but FQDN desired due to dynamic nature of IP changes
  server [www.example.com]("http://www.example.com") [www.example.com:443]("http://www.example.com:443") check inter 10s fastinter 2s downinter 2s fall 1800 << works but only forwards using v4 DNS records

your help is much appreciated

---

### Post by john_d13 on 2016-02-04
Ok so i figured out that haproxy performs a DNS lookup on the hostnames on startup then caches the A records. 

 Now question is if I can configure haproxy to prefer IPv6 lookups instead of v4.

---

### Post by djbon2112 on 2016-11-25
To prefer the AAAA record, you should use something like this in your "server" line:

> server name name.fqdn.org:80 check **resolvers resolvergroup resolve-prefer ipv6**

Edit: it appears I'm wrong. If I try to start haproxy with an IPv6-only hostname, it does fail to start. But with a dual-stack record and the options above, it immediately changes to the AAAA record upon startup and hums along.

---

