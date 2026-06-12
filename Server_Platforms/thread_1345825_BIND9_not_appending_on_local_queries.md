---
title: "BIND9 not appending on local queries"
date: 2009-12-04
forum: Server Platforms
---

### Post by jimmah6786 on 2009-12-04
Is there a specific option I have to set to have my BIND9 DNS server automagically appened my domain suffix when querying local machines on the local network. For example, lets say I want to ping a local machine called "foo" which does exist. I get a hostname not found. however if I do a dig "foo.mydomain.example" I get:

```

; <<>> DiG 9.6.1-P1 <<>> foo.mydomain.example
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 53757
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;foo.mydomain.example.    IN      A

;; AUTHORITY SECTION:
mydomain.example.        604800  IN      SOA     ns.mydomain.example. root.mydomain.example. 9 604800 86400 2419200 604800

;; Query time: 1 msec
;; SERVER: 192.168.10.1#53(192.168.10.1)
;; WHEN: Fri Dec  4 12:03:09 2009
;; MSG SIZE  rcvd: 100



```

---

### Post by KiLaHuRtZ on 2009-12-07
For each client, add this to '/etc/resolv.conf'...

```
domain mydomain.example
search mydomain.example
```

Optionally, if you run a DHCP server (ISC DHCPD), add this and it will tell your clients what to append with...

```
option domain-name "mydomain.example";
```

---

