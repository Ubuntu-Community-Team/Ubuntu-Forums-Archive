---
title: "Bind9 Intresting problem..."
date: 2008-04-07
forum: Server Platforms
---

### Post by thembimoyo on 2008-04-07
I have setup Ubuntu 7.10 sever and selected DNS on install Machine is call ns.mydns.org.
I have setup my local zone and the relevant reverse zone. 

I do a dig on ns.mydns.org ie dig [www.ns.mydns.org](www.ns.mydns.org) I get;

```
root@ns:~# dig www.ns.mydns.org

; <<>> DiG 9.4.1-P1 <<>> www.ns.mydns.org
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 48685
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;www.ns.mydns.org.	IN	A

;; ANSWER SECTION:
www.ns.mydns.org.	80480	IN	A	192.168.3.6

;; AUTHORITY SECTION:
ns.mydns.org.		80480	IN	NS	ns.mydns.org.

;; ADDITIONAL SECTION:
ns.ns.mydns.org.	80480	IN	A	192.168.3.4

;; Query time: 6 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Apr  7 08:02:22 2008
;; MSG SIZE  rcvd: 83

```

on ns.mydns.org I also do a dig @127.0.0.1 [www.yahoo.com](www.yahoo.com) i get;
```

root@ns:~# dig @127.0.0.1 www.yahoo.com

; <<>> DiG 9.4.1-P1 <<>> @127.0.0.1 www.yahoo.com
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 2570
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 9, ADDITIONAL: 9

;; QUESTION SECTION:
;www.yahoo.com.			IN	A

;; ANSWER SECTION:
www.yahoo.com.		247	IN	CNAME	www.yahoo-ht3.akadns.net.
www.yahoo-ht3.akadns.net. 8	IN	A	69.147.114.210

;; AUTHORITY SECTION:
akadns.net.		119611	IN	NS	usw2.akadns.net.
akadns.net.		119611	IN	NS	use4.akadns.net.
akadns.net.		119611	IN	NS	zc.akadns.org.
akadns.net.		119611	IN	NS	eur1.akadns.net.
akadns.net.		119611	IN	NS	use3.akadns.net.
akadns.net.		119611	IN	NS	zb.akadns.org.
akadns.net.		119611	IN	NS	asia9.akadns.net.
akadns.net.		119611	IN	NS	zd.akadns.org.
akadns.net.		119611	IN	NS	za.akadns.org.

;; ADDITIONAL SECTION:
asia9.akadns.net.	119611	IN	A	220.73.220.4
eur1.akadns.net.	119611	IN	A	213.254.204.197
use3.akadns.net.	119611	IN	A	204.2.178.133
use4.akadns.net.	119611	IN	A	208.44.108.137
usw2.akadns.net.	119611	IN	A	63.209.3.132
za.akadns.org.		119427	IN	A	195.219.3.169
zb.akadns.org.		119428	IN	A	206.132.100.105
zc.akadns.org.		119464	IN	A	124.211.40.4
zd.akadns.org.		119551	IN	A	63.209.3.132

;; Query time: 146 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Apr  7 08:06:07 2008
;; MSG SIZE  rcvd: 403

``` 

THEN I got to a client machine on my network which I have added to my named.config.options ```
allow-query-cache { localhost; 192.168.2.0/24; };
        allow-recursion {
                localhost;
                192.168.2.0;
                192.168.3.0;
                };

```

I do a dig @192.168.3.4 [www.yahoo.com](www.yahoo.com) 
I get ```
administrators-mac-mini:~ admin$ dig @192.168.3.4 www.yahoo.com

; <<>> DiG 9.4.1-P1 <<>> @192.168.3.4 www.yahoo.com
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58335
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 13, ADDITIONAL: 14
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;www.yahoo.com.			IN	A

;; AUTHORITY SECTION:
.			89914	IN	NS	I.ROOT-SERVERS.NET.
.			89914	IN	NS	D.ROOT-SERVERS.NET.
.			89914	IN	NS	H.ROOT-SERVERS.NET.
.			89914	IN	NS	F.ROOT-SERVERS.NET.
.			89914	IN	NS	E.ROOT-SERVERS.NET.
.			89914	IN	NS	A.ROOT-SERVERS.NET.
.			89914	IN	NS	J.ROOT-SERVERS.NET.
.			89914	IN	NS	C.ROOT-SERVERS.NET.
.			89914	IN	NS	K.ROOT-SERVERS.NET.
.			89914	IN	NS	B.ROOT-SERVERS.NET.
.			89914	IN	NS	M.ROOT-SERVERS.NET.
.			89914	IN	NS	G.ROOT-SERVERS.NET.
.			89914	IN	NS	L.ROOT-SERVERS.NET.

;; ADDITIONAL SECTION:
B.ROOT-SERVERS.NET.	437105	IN	A	192.228.79.201
C.ROOT-SERVERS.NET.	437105	IN	A	192.33.4.12
D.ROOT-SERVERS.NET.	437105	IN	A	128.8.10.90
E.ROOT-SERVERS.NET.	437105	IN	A	192.203.230.10
F.ROOT-SERVERS.NET.	437105	IN	A	192.5.5.241
F.ROOT-SERVERS.NET.	437105	IN	AAAA	2001:500:2f::f
G.ROOT-SERVERS.NET.	437105	IN	A	192.112.36.4
H.ROOT-SERVERS.NET.	437105	IN	A	128.63.2.53
H.ROOT-SERVERS.NET.	437105	IN	AAAA	2001:500:1::803f:235
I.ROOT-SERVERS.NET.	437105	IN	A	192.36.148.17
J.ROOT-SERVERS.NET.	176314	IN	A	192.58.128.30
K.ROOT-SERVERS.NET.	437105	IN	A	193.0.14.129
L.ROOT-SERVERS.NET.	176314	IN	A	199.7.83.42
M.ROOT-SERVERS.NET.	176314	IN	A	202.12.27.33

;; Query time: 3 msec
;; SERVER: 192.168.3.4#53(192.168.3.4)
;; WHEN: Mon Apr  7 08:11:15 2008
;; MSG SIZE  rcvd: 490


```
 I do a ping [www.yahoo.com](www.yahoo.com) on the same client machine I get
```
administrators-mac-mini:~ admin$ ping www.yahoo.com
ping: cannot resolve www.yahoo.com: Unknown host

```

My log looks like this```
07-Apr-2008 08:14:31.323 queries: client 192.168.2.132#1080: query: download948.avast.com IN A +
07-Apr-2008 08:14:45.352 queries: client 192.168.2.132#1080: query: download948.avast.com.mydns.org IN A +
07-Apr-2008 08:14:46.633 queries: client 192.168.2.224#60097: query: www.yahoo.com IN A +
07-Apr-2008 08:14:47.622 queries: client 192.168.2.163#1315: query: api.hi5.com IN AAAA +
07-Apr-2008 08:14:47.624 queries: client 192.168.2.163#1315: query: api.hi5.com.mydns.org IN AAAA +
07-Apr-2008 08:14:47.625 queries: client 192.168.2.163#1315: query: api.hi5.com IN A +
07-Apr-2008 08:14:47.627 queries: client 192.168.2.163#1315: query: api.hi5.com.mydns.org IN A +
07-Apr-2008 08:15:08.117 queries: client 192.168.2.107#3014: query: dnl-cd1.kaspersky-labs.com IN A +
07-Apr-2008 08:15:22.450 queries: client 192.168.2.113#1837: query: newsrss.bbc.co.uk IN AAAA +
07-Apr-2008 08:15:22.452 queries: client 192.168.2.113#1837: query: newsrss.bbc.co.uk.mydns.org IN AAAA +
07-Apr-2008 08:15:22.452 queries: client 192.168.2.113#1837: query: newsrss.bbc.co.uk IN A +

```
PLEASE HELP I AM OUT OF WORDS....

---

### Post by conjur3r on 2008-04-07
> **thembimoyo said:**
> 

THEN I got to a client machine on my network which I have added to my named.config.options ```
allow-query-cache { localhost; 192.168.2.0/24; };
        allow-recursion {
                localhost;
                192.168.2.0;
                192.168.3.0;
                };

```


Just a stab in the dark.  Should that be:

192.168.2.0/24;
192.168.3.0/24;

?

An alternative is to restrict using your firewall.

---

### Post by Robstarusa on 2008-04-07
> **thembimoyo said:**
> I have setup Ubuntu 7.10 sever and selected DNS on install Machine is call ns.mydns.org.
I have setup my local zone and the relevant reverse zone. 

I do a dig on ns.mydns.org ie dig [www.ns.mydns.org](www.ns.mydns.org) I get;

```
root@ns:~# dig www.ns.mydns.org

; <<>> DiG 9.4.1-P1 <<>> www.ns.mydns.org
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 48685
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;www.ns.mydns.org.	IN	A

;; ANSWER SECTION:
www.ns.mydns.org.	80480	IN	A	192.168.3.6

;; AUTHORITY SECTION:
ns.mydns.org.		80480	IN	NS	ns.mydns.org.

;; ADDITIONAL SECTION:
ns.ns.mydns.org.	80480	IN	A	192.168.3.4

;; Query time: 6 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Apr  7 08:02:22 2008
;; MSG SIZE  rcvd: 83

```

on ns.mydns.org I also do a dig @127.0.0.1 [www.yahoo.com](www.yahoo.com) i get;
```

root@ns:~# dig @127.0.0.1 www.yahoo.com

; <<>> DiG 9.4.1-P1 <<>> @127.0.0.1 www.yahoo.com
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 2570
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 9, ADDITIONAL: 9

;; QUESTION SECTION:
;www.yahoo.com.			IN	A

;; ANSWER SECTION:
www.yahoo.com.		247	IN	CNAME	www.yahoo-ht3.akadns.net.
www.yahoo-ht3.akadns.net. 8	IN	A	69.147.114.210

;; AUTHORITY SECTION:
akadns.net.		119611	IN	NS	usw2.akadns.net.
akadns.net.		119611	IN	NS	use4.akadns.net.
akadns.net.		119611	IN	NS	zc.akadns.org.
akadns.net.		119611	IN	NS	eur1.akadns.net.
akadns.net.		119611	IN	NS	use3.akadns.net.
akadns.net.		119611	IN	NS	zb.akadns.org.
akadns.net.		119611	IN	NS	asia9.akadns.net.
akadns.net.		119611	IN	NS	zd.akadns.org.
akadns.net.		119611	IN	NS	za.akadns.org.

;; ADDITIONAL SECTION:
asia9.akadns.net.	119611	IN	A	220.73.220.4
eur1.akadns.net.	119611	IN	A	213.254.204.197
use3.akadns.net.	119611	IN	A	204.2.178.133
use4.akadns.net.	119611	IN	A	208.44.108.137
usw2.akadns.net.	119611	IN	A	63.209.3.132
za.akadns.org.		119427	IN	A	195.219.3.169
zb.akadns.org.		119428	IN	A	206.132.100.105
zc.akadns.org.		119464	IN	A	124.211.40.4
zd.akadns.org.		119551	IN	A	63.209.3.132

;; Query time: 146 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Apr  7 08:06:07 2008
;; MSG SIZE  rcvd: 403

``` 

THEN I got to a client machine on my network which I have added to my named.config.options ```
allow-query-cache { localhost; 192.168.2.0/24; };
        allow-recursion {
                localhost;
                192.168.2.0;
                192.168.3.0;
                };

```

I do a dig @192.168.3.4 [www.yahoo.com](www.yahoo.com) 
I get ```
administrators-mac-mini:~ admin$ dig @192.168.3.4 www.yahoo.com

; <<>> DiG 9.4.1-P1 <<>> @192.168.3.4 www.yahoo.com
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58335
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 13, ADDITIONAL: 14
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;www.yahoo.com.			IN	A

;; AUTHORITY SECTION:
.			89914	IN	NS	I.ROOT-SERVERS.NET.
.			89914	IN	NS	D.ROOT-SERVERS.NET.
.			89914	IN	NS	H.ROOT-SERVERS.NET.
.			89914	IN	NS	F.ROOT-SERVERS.NET.
.			89914	IN	NS	E.ROOT-SERVERS.NET.
.			89914	IN	NS	A.ROOT-SERVERS.NET.
.			89914	IN	NS	J.ROOT-SERVERS.NET.
.			89914	IN	NS	C.ROOT-SERVERS.NET.
.			89914	IN	NS	K.ROOT-SERVERS.NET.
.			89914	IN	NS	B.ROOT-SERVERS.NET.
.			89914	IN	NS	M.ROOT-SERVERS.NET.
.			89914	IN	NS	G.ROOT-SERVERS.NET.
.			89914	IN	NS	L.ROOT-SERVERS.NET.

;; ADDITIONAL SECTION:
B.ROOT-SERVERS.NET.	437105	IN	A	192.228.79.201
C.ROOT-SERVERS.NET.	437105	IN	A	192.33.4.12
D.ROOT-SERVERS.NET.	437105	IN	A	128.8.10.90
E.ROOT-SERVERS.NET.	437105	IN	A	192.203.230.10
F.ROOT-SERVERS.NET.	437105	IN	A	192.5.5.241
F.ROOT-SERVERS.NET.	437105	IN	AAAA	2001:500:2f::f
G.ROOT-SERVERS.NET.	437105	IN	A	192.112.36.4
H.ROOT-SERVERS.NET.	437105	IN	A	128.63.2.53
H.ROOT-SERVERS.NET.	437105	IN	AAAA	2001:500:1::803f:235
I.ROOT-SERVERS.NET.	437105	IN	A	192.36.148.17
J.ROOT-SERVERS.NET.	176314	IN	A	192.58.128.30
K.ROOT-SERVERS.NET.	437105	IN	A	193.0.14.129
L.ROOT-SERVERS.NET.	176314	IN	A	199.7.83.42
M.ROOT-SERVERS.NET.	176314	IN	A	202.12.27.33

;; Query time: 3 msec
;; SERVER: 192.168.3.4#53(192.168.3.4)
;; WHEN: Mon Apr  7 08:11:15 2008
;; MSG SIZE  rcvd: 490


```
 I do a ping [www.yahoo.com](www.yahoo.com) on the same client machine I get
```
administrators-mac-mini:~ admin$ ping www.yahoo.com
ping: cannot resolve www.yahoo.com: Unknown host

```

My log looks like this```
07-Apr-2008 08:14:31.323 queries: client 192.168.2.132#1080: query: download948.avast.com IN A +
07-Apr-2008 08:14:45.352 queries: client 192.168.2.132#1080: query: download948.avast.com.mydns.org IN A +
07-Apr-2008 08:14:46.633 queries: client 192.168.2.224#60097: query: www.yahoo.com IN A +
07-Apr-2008 08:14:47.622 queries: client 192.168.2.163#1315: query: api.hi5.com IN AAAA +
07-Apr-2008 08:14:47.624 queries: client 192.168.2.163#1315: query: api.hi5.com.mydns.org IN AAAA +
07-Apr-2008 08:14:47.625 queries: client 192.168.2.163#1315: query: api.hi5.com IN A +
07-Apr-2008 08:14:47.627 queries: client 192.168.2.163#1315: query: api.hi5.com.mydns.org IN A +
07-Apr-2008 08:15:08.117 queries: client 192.168.2.107#3014: query: dnl-cd1.kaspersky-labs.com IN A +
07-Apr-2008 08:15:22.450 queries: client 192.168.2.113#1837: query: newsrss.bbc.co.uk IN AAAA +
07-Apr-2008 08:15:22.452 queries: client 192.168.2.113#1837: query: newsrss.bbc.co.uk.mydns.org IN AAAA +
07-Apr-2008 08:15:22.452 queries: client 192.168.2.113#1837: query: newsrss.bbc.co.uk IN A +

```
PLEASE HELP I AM OUT OF WORDS....

I think you need to add 192.168.3.0/24 to your "allow-query-cache' option.

---

