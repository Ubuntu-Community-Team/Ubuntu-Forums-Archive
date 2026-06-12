---
title: "ns-west.cerf.net.dns.cerf.net"
date: 2007-11-21
forum: Server Platforms
---

### Post by whoboo on 2007-11-21
nmap reports "interesting ports on ns-west.cerf.net.dns.cerf.net (127.0.0.1)"  on a scan of my machine..

Have I been dns rebound ?  Or what is going on and how can I fix and prevent it ?

ns-west.cerf.net.dns.cerf.net is in my /etc/hosts file with a lot of other sites which are not supposed to be able to connect to my machine.

; <<>> DiG 9.3.2 <<>> ns-west.cerf.net.dns.cerf.net
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 11829
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;ns-west.cerf.net.dns.cerf.net. IN      A

;; AUTHORITY SECTION:
cerf.net.               10800   IN      SOA     ns-west.cerf.net. notify.attens. com. 2007080500 3600 1800 604800 86400

;; Query time: 97 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Fri Nov 23 15:48:13 2007
;; MSG SIZE  rcvd: 108

---

