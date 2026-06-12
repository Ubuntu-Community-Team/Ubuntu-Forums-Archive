---
title: "BIND troubles"
date: 2009-06-09
forum: Server Platforms
---

### Post by jfmanamtr on 2009-06-09
I am trying to setup a DNS server that is a caching name server & one that resolves my local network. I have the caching side working fine, but the internal forward & reverse zones aren't cooperating as well as I had hoped. I was wondering if you guys could help me see what I am doing wrong. I am guessing you will want to see my named.conf.local, & then the zone files. So, here they are:

named.conf.local
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
include "/etc/bind/zones.rfc1918";

zone "my-network" {
        type master;
        file "/etc/bind/db.my-network";
};

zone "1.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192";
};
```db.my-network (forward zone)
```
;
; BIND forward data file for my-network zone
;
$TTL    604800
@       IN      SOA     ubuntu-server. jmorren.gmail.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@              IN      NS      ubuntu-server.
@              IN      A       192.168.1.3
ubuntu-server. IN      A       192.168.1.3
my-router.     IN      A       192.168.1.1
john-pc.       IN      A       192.168.1.95
media-pc.      IN      A       192.168.1.96
emily-laptop.  IN      A       192.168.1.97
```db.192 (reverse zone)
```
;
; BIND reverse data file for my-network zone
;
$TTL    604800
@       IN      SOA     ubuntu-server. jmorren.gmail.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ubuntu-server
3       IN      PTR     ubuntu-server
1       IN      PTR     my-router
95      IN      PTR     john-pc
96      IN      PTR     media-pc
97      IN      PTR     emily-laptop
```

So, there you have it. I am pretty sure that I am missing something simple, but I can't for the life of me figure out what. When I do a dig for any of the listed devices, I get these kind of results:

dig my-router & dig 192.168.1.1
```
; <<>> DiG 9.5.1-P2 <<>> my-router
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 51177
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;my-router.            IN    A

;; AUTHORITY SECTION:
.            10    IN    SOA    A.ROOT-SERVERS.NET. NSTLD.VERISIGN-GRS.COM. 2009060801 1800 900 604800 86400

;; Query time: 49 msec
;; SERVER: 192.168.1.3#53(192.168.1.3)
;; WHEN: Tue Jun  9 09:09:31 2009
;; MSG SIZE  rcvd: 102

; <<>> DiG 9.5.1-P2 <<>> 192.168.1.1
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 16500
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;192.168.1.1.            IN    A

;; AUTHORITY SECTION:
.            10    IN    SOA    a.root-servers.net. nstld.verisign-grs.com. 2009060801 1800 900 604800 86400

;; Query time: 60 msec
;; SERVER: 192.168.1.3#53(192.168.1.3)
;; WHEN: Tue Jun  9 09:10:21 2009
;; MSG SIZE  rcvd: 104
```So, from what I understand of DNS, these dig results mean that my DNS server is not answering for any local requests.If you need me to post anything else, just let me know & I will get it on here asap (I am at work so it may take me a little to respond). Any Ideas or thoughts?

~John

---

### Post by blackxored on 2009-06-09
I don't see the FQDN of your local network here.

---

### Post by jfmanamtr on 2009-06-09
OK. I am not understanding. I wasn't trying to use the FQDN internally. I have an FQDN that goes to my website. I was only trying to have the name to IP resolution done internally for my-network. Am I going about this the wrong way?

~John

---

### Post by jfmanamtr on 2009-06-09
Ok. I appear to have been able to fix DNS to work like I want. I just wanted to be able to type things like "ping <name of a pc on my network>" & have it respond to the correct IP. It looks like I reconstructed the zone files & it is now working. Thanks.

~John

---

