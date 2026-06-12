---
title: "BIND9 caching problem"
date: 2010-04-08
forum: Server Platforms
---

### Post by stefangr1 on 2010-04-08
I'd like to run my own dns server, so I've read some material about bind9 and configured a test server (in vmware).

I notice that, when I repeat executing "dig www.google.nl" once a second, Query time is about 50ms the first time and then for 5 seconds or so 0ms, followed by another 50ms, and then 0ms again etc.

It thus seems that dns caching entries are refreshed every 5 seconds. Also, if I disconnect the server from internet, I notice that bind still know's entries from zones for which it has authority (luckely), but not for entries from the outside that are suppozed to be in cache.

How do I change/configure this behaviour? With the present configuration dns caching isn't really useful...

---

### Post by uljanow on 2010-04-08
It's probably not a caching problem. BIND looks at the TTL value and acts accordingly.

---

### Post by stefangr1 on 2010-04-08
> **uljanow said:**
> It's probably not a caching problem. BIND looks at the TTL value and acts accordingly.

Thanks for your explanation, I now notice that if I dig my own website, the 38400 from the output below corresponds to what I've configured for "Negative Cache TTL" in my own zone configuration.

However, all regular websites I checked (like ubuntuforums.org) use a TTL of 5 seconds. This I find a bit surprising, as the serveral turorials I read about bind stated that the advantage of running a caching server at home was faster loading of sites, but now it appears that it's only faster for sites that are visited every few miliseconds :).



; <<>> DiG 9.6.1-P2 <<>> [www.server.lan](www.server.lan)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 49281
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;[www.server.lan](www.server.lan).			IN	A

;; ANSWER SECTION:
[www.server.lan](www.server.lan).		38400	IN	A	192.168.135.3

;; AUTHORITY SECTION:
server.lan.		38400	IN	NS	ns1.server.lan.

;; ADDITIONAL SECTION:
ns1.server.lan.		38400	IN	A	192.168.135.3

;; Query time: 0 msec
;; SERVER: 192.168.135.3#53(192.168.135.3)
;; WHEN: Thu Apr  8 14:13:34 2010
;; MSG SIZE  rcvd: 82

---

