---
title: "Nut CGI in Web Server"
date: 2016-11-22
forum: Server Platforms
---

### Post by isidoro4 on 2016-11-22
Hi,
I have installed nut-cgi. I can see the ups stats at [http://ip.of.my.server/cgi-bin/nut/upsstats.cgi](http://ip.of.my.server/cgi-bin/nut/upsstats.cgi). Now I want a shorter url, for example [http://ip.of.my.server/nut](http://ip.of.my.server/nut). On my server I have also a virtual domain.
How Can I get nut accessible to multiple domain?

---

### Post by cariboo on 2016-11-23
I use /etc/hosts to alias a server name to an ip address eg:

```
192.168.0.205	willy
192.168.0.200	likely
192.168.0.104	skynet
192.168.0.110	server2
```

after that I use:

[noparse]http://willy/mediawiki[/noparse]

for example to access my wiki.

---

