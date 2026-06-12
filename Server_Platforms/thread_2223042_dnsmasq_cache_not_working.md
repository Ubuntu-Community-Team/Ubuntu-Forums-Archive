---
title: "dnsmasq cache not working?"
date: 2014-05-09
forum: Server Platforms
---

### Post by slug3 on 2014-05-09
Testing with dig bbc.co.uk the fist once takes a few ms then after that it is 0ms. Wait for about 5 mins on a dead network and dig take a few ms again. This make me think it's not caching correctly?


May  9 11:29:05 ds01 dnsmasq[29421]: time 1399631345
May  9 11:29:05 ds01 dnsmasq[29421]: cache size 10000, 0/1170 cache insertions re-used unexpired cache entries.
May  9 11:29:05 ds01 dnsmasq[29421]: queries forwarded 388, queries answered locally 302
May  9 11:29:05 ds01 dnsmasq[29421]: queries for authoritative zones 0
May  9 11:29:05 ds01 dnsmasq[29421]: DNSSEC memory in use 0, max 0, allocated 999984
May  9 11:29:05 ds01 dnsmasq[29421]: server 8.8.8.8#53: queries sent 144, retried or failed 6
May  9 11:29:05 ds01 dnsmasq[29421]: server 8.8.4.4#53: queries sent 84, retried or failed 5
May  9 11:29:05 ds01 dnsmasq[29421]: server 194.168.4.100#53: queries sent 236, retried or failed 1

---

### Post by Doug S on 2014-05-09
Hi and welcome to Ubuntu forums,

I think caching is working fine. bbc.co.uk seems to be using short TTL (Time To Live) of 5 minutes. A lot of big sites use short times and you often see the order of IP addresses change, probably for load balancing reasons. Just keep doing "dig bbc.co.uk" and you will observe the TTL column decreasing, with short lookup times, until it gets to 0, then you will see it go back to 300 seconds, with a longer lookup time, and probably see the order of IP addresses change. Example:```
doug@doug-64:~/init$ [COLOR=#ff0000]dig bbc.co.uk[/COLOR]

; <<>> DiG 9.8.1-P1 <<>> bbc.co.uk
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 48744
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 3, ADDITIONAL: 1

;; QUESTION SECTION:
;bbc.co.uk.                     IN      A

;; ANSWER SECTION:
bbc.co.uk.              [COLOR=#ff0000]122[/COLOR]     IN      A       [COLOR=#ff0000]212.58.244.20[/COLOR]
bbc.co.uk.              [COLOR=#ff0000]122[/COLOR]     IN      A       212.58.246.103
bbc.co.uk.              [COLOR=#ff0000]122[/COLOR]     IN      A       212.58.246.104
bbc.co.uk.              [COLOR=#ff0000]122[/COLOR]     IN      A       212.58.244.18

;; AUTHORITY SECTION:
bbc.co.uk.              422     IN      NS      ns1.rbsov.bbc.co.uk.
bbc.co.uk.              422     IN      NS      ns1.tcams.bbc.co.uk.
bbc.co.uk.              422     IN      NS      ns1.thdow.bbc.co.uk.

;; ADDITIONAL SECTION:
ns1.tcams.bbc.co.uk.    86250   IN      A       212.72.49.3

;; [COLOR=#ff0000]Query time: 0 msec[/COLOR]
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri May  9 08:48:02 2014
;; MSG SIZE  rcvd: 179

doug@doug-64:~/init$ [COLOR=#ff0000]dig bbc.co.uk[/COLOR]

; <<>> DiG 9.8.1-P1 <<>> bbc.co.uk
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 13114
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 3, ADDITIONAL: 1

;; QUESTION SECTION:
;bbc.co.uk.                     IN      A

;; ANSWER SECTION:
bbc.co.uk.              [COLOR=#ff0000]300[/COLOR]     IN      A       [COLOR=#ff0000]212.58.244.18[/COLOR]
bbc.co.uk.              [COLOR=#ff0000]300 [/COLOR]    IN      A       212.58.244.20
bbc.co.uk.              [COLOR=#ff0000]300[/COLOR]     IN      A       212.58.246.103
bbc.co.uk.              [COLOR=#ff0000]300[/COLOR]     IN      A       212.58.246.104

;; AUTHORITY SECTION:
bbc.co.uk.              260     IN      NS      ns1.tcams.bbc.co.uk.
bbc.co.uk.              260     IN      NS      ns1.rbsov.bbc.co.uk.
bbc.co.uk.              260     IN      NS      ns1.thdow.bbc.co.uk.

;; ADDITIONAL SECTION:
ns1.tcams.bbc.co.uk.    86088   IN      A       212.72.49.3

;; [COLOR=#ff0000]Query time: 174 msec[/COLOR]
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri May  9 08:50:44 2014
;; MSG SIZE  rcvd: 179
```

---

### Post by SlugSlug on 2014-05-09
Ahh that make sense, never thought anyone would use such short TTL's thanks.

For reference 

[http://www.cyberciti.biz/faq/howto-use-dig-to-find-dns-time-to-live-ttl-values/](http://www.cyberciti.biz/faq/howto-use-dig-to-find-dns-time-to-live-ttl-values/)

---

