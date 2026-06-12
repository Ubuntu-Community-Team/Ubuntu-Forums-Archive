---
title: "bind9 + in-addr.arpa on delegated public subnet = fail"
date: 2009-07-13
forum: Server Platforms
---

### Post by n8bounds on 2009-07-13
Hello community!

I'm running Version: 1:9.4.2.dfsg.P2-2ubuntu0.1 of bind9 installed on Ubuntu 8.04.2 with kernel 2.6.24-24-server (x86_64).

Everything has been going fine (this is a mail/name server) but I neglected to setup a reverse lookup zone when I configured all this. Named answers properly to all queries for the 6 public zones for which it is master, but refuses to answer (it thinks its not authoritative) for the in-addr.arpa zone I recently added.

I've never used in-addr.arpa zones before, so I must be missing something.

We have the following subnet delegated to us by our ISP: 12.145.82.128/28

Now, as I understand it, this should translate to: 128/28.82.145.12.in-addr.arpa. (or 128-28.82.145.12.in-addr.arpa.) This is what I based my configurations on. Below are the relevant files:

```

root@mail:~# cat /etc/bind/named.conf

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
```

and...

```
root@mail:~# cat /etc/bind/named.conf.options
        options {
	directory "/var/cache/bind";


	query-source address * port 53;

	allow-transfer { none; };
	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
        };

        logging {
             category lame-servers {null; };
             //category edns-disabled { null; };
        };
```

and...

```
root@mail:~# cat /etc/bind/named.conf.local

	acl "slaves" {  192.168.2.29; 192.168.5.29; 192.168.1.29; 
			192.168.6.10; 192.168.7.10; 192.168.9.10;
			199.191.128.105; 199.191.128.106; 12.127.16.69;
			12.127.16.70; 12.145.82.142; 192.168.101.11; 
		     };

include "/etc/bind/named.conf.local.int";
include "/etc/bind/named.conf.local.ext";
```

and...
```

root@mail:~# cat /etc/bind/named.conf.local.ext 
view "external" {
 match-clients { "any"; };
  recursion no;

    zone "epescarriers.com" IN {
        type master;
        notify yes;
        file "db.epescarriers.com";
        allow-update { none; };
        allow-transfer { "slaves"; };
    };

    zone "epestransport.com" IN {
        type master;
        notify yes;
        file "db.domains";
        allow-update { none; };
        allow-transfer { "slaves"; };
    };

    zone "epeslogistics.com" IN {
        type master;
        notify yes;
        file "db.domains";
        allow-update { none; };
        allow-transfer { "slaves"; };
    };

    zone "epesexpress.com" IN {
        type master;
        notify yes;
        file "db.domains";
        allow-update { none; };
        allow-transfer { "slaves"; };
    };

    zone "tsexpress.com" IN {
        type master;
        notify yes;
        file "db.domains";
        allow-update { none; };
        allow-transfer { "slaves"; };
    };

    zone "epesfms.com" IN {
        type master;
        notify yes;
        file "db.domains";
        allow-update { none; };
        allow-transfer { "slaves"; };
    };

     //zone "128/28.82.145.12.in-addr.arpa" IN {
     //zone "82.145.12.IN-ADDR.ARPA" IN {
     //zone "82.145.12.in-addr.arpa." IN { //sort of works
     zone "128-28.82.145.12.IN-ADDR.ARPA" IN {
    type master;
    notify yes;
    allow-update { none; };
        allow-transfer { "slaves"; };
    file "db.ext.ptr";
   };

    };

```
and...

```
root@mail:~# cat /etc/bind/named.conf.local.int
view "internal" {
 match-clients 	{ 192.168.0.0/23; 192.168.2.0/24; 192.168.5.0/24; 
		  192.168.6.0/24; 192.168.7.0/24; 192.168.6.0/24; 
		  192.168.7.0/24; 192.168.9.0/24; 
		};
  allow-recursion { 192.168.0.0/16; 192.168.101.0/24; 127.0.0.1; };

        zone "epescarriers.com" {
             type master;
             notify yes;
             file "db.int.epescarriers.com";
             allow-update { none; };
             allow-transfer { "slaves"; };
        };

        zone "epescarriers.lan" {
             type master;
             notify yes;
             file "db.int.epescarriers.lan";
             allow-update { none; };
             allow-transfer { "slaves"; };
        };

        zone "epesfms.com" {
             type master;
             notify yes;
             file "db.int.epesfms.com";
             allow-update { none; };
             allow-transfer { "slaves"; };
        };

        zone "epeslogistics.com" {
             type master;
             notify yes;
             file "db.int.epeslogistics.com";
             allow-update { none; };
             allow-transfer { "slaves"; };
        };

        zone "epestransport.com" {
             type master;
             notify yes;
             file "db.int.epestransport.com";
             allow-update { none; };
             allow-transfer { "slaves"; };
        };

        zone "tsexpress.com" {
             type master;
             notify yes;
             file "db.int.tsexpress.com";
             allow-update { none; };
             allow-transfer { "slaves"; };
        };


//built-ins

        zone "10.IN-ADDR.ARPA" {
                type master;
                file "empty";
        };

        zone "16.172.IN-ADDR.ARPA" {
                type master;
                file "empty";
        };

        zone "168.192.IN-ADDR.ARPA" {
                type master;
                file "empty";
        };

        zone "localhost" {
                type master;
                file "/etc/bind/db.local";
        };

        zone "127.in-addr.arpa" {
                type master;
                file "/etc/bind/db.127";
        };

        zone "0.in-addr.arpa" {
                type master;
                file "/etc/bind/db.0";
        };

        zone "255.in-addr.arpa" {
                type master;
                file "/etc/bind/db.255";
        };

        zone "." {
                type hint;
                file "/etc/bind/db.root";
        };



                };
```

and, finally, the zone file in question itself...

```
$TTL 3D
;$ORIGIN 128/28.82.145.12.in-addr.arpa.
$ORIGIN 128-28.82.145.12.IN-ADDR.ARPA.
@       IN      SOA     ns.epescarriers.com. postmaster.epescarriers.com. (
                        2009071315      ; serial
                        4H              ; refresh
                        2H              ; retry
                        4W              ; expire
                        1D )            ; minimum

                NS      dbru.br.ns.els-gms.att.net.
                NS      dmtu.mt.ns.els-gms.att.net.
                NS      ns.epescarriers.com.


129     IN      CNAME   mail.epescarriers.com.

130     IN      PTR     mail-mx01.epescarriers.com.
131     IN      PTR     mail.epescarriers.com.
132     IN      PTR     mail-mx02.epescarriers.com.
```

When I try to query like this (from outside)...

```
root@poweredge:~# dig @ns.epescarriers.com -x 12.145.82.132

; <<>> DiG 9.5.1-P2 <<>> @ns.epescarriers.com -x 12.145.82.132
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: REFUSED, id: 51905
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;132.82.145.12.in-addr.arpa.	IN	PTR

;; Query time: 40 msec
;; SERVER: 12.145.82.132#53(12.145.82.132)
;; WHEN: Mon Jul 13 17:58
```:38 2009
;; MSG SIZE  rcvd: 44

This appears in the syslog...

```
Jul 13 17:58:38 mail named[18772]: client 65.188.241.191#64026: view external: query (cache) '132.82.145.12.in-addr.arpa/PTR/IN' denied
```

When the slave servers attempt to load the zone, this appears in syslog...

```
Jul 13 16:18:45 mail named[12825]: zone 128-28.82.145.12.IN-ADDR.ARPA/IN/external: loaded serial 2009071314
Jul 13 16:18:45 mail named[12825]: zone 128-28.82.145.12.IN-ADDR.ARPA/IN/external: sending notifies (serial 2009071314)
Jul 13 16:22:32 mail named[12825]: client 199.191.128.106#36345: view external: query (cache) '128/28.82.145.12.in-addr.arpa/SOA/IN' denied
Jul 13 16:22:32 mail named[12825]: client 199.191.128.106#50767: view external: bad zone transfer request: '128/28.82.145.12.in-addr.arpa/IN': non-authoritative zone (NOTAUTH)
```

...any ideas?

Thanks!

---

### Post by doas777 on 2009-07-13
try commenting the $origin lines in your reverse zone. 
you can use 'named-checkzone' to check your zone file for errors.

---

### Post by n8bounds on 2009-07-13
commented it out, then..

```

root@mail:~# named-checkzone 128-28.82.145.12.IN-ADDR.ARPA /var/cache/bind/db.ext.ptr
zone 128-28.82.145.12.IN-ADDR.ARPA/IN: loaded serial 2009071315
OK

```

so I bounced it..

```

root@mail:/var/cache/bind# /etc/init.d/bind9 restart;  tail -n 50 -f /var/log/syslog | grep named
 * Stopping domain name service... bind                                                                                                                                     [ OK ] 
 * Starting domain name service... bind                                                                                                                                     [ OK ] 
Jul 13 18:26:35 mail named[17343]: automatic empty zone: view internal: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jul 13 18:26:35 mail named[17343]: automatic empty zone: view internal: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jul 13 18:26:35 mail named[17343]: automatic empty zone: view internal: D.F.IP6.ARPA
Jul 13 18:26:35 mail named[17343]: automatic empty zone: view internal: 8.E.F.IP6.ARPA
Jul 13 18:26:35 mail named[17343]: automatic empty zone: view internal: 9.E.F.IP6.ARPA
Jul 13 18:26:35 mail named[17343]: automatic empty zone: view internal: A.E.F.IP6.ARPA
Jul 13 18:26:35 mail named[17343]: automatic empty zone: view internal: B.E.F.IP6.ARPA
Jul 13 18:26:35 mail named[17343]: /etc/bind/named.conf.options:10: using specific query-source port suppresses port randomization and can be insecure.
Jul 13 18:26:35 mail named[17343]: /etc/bind/named.conf.options:10: using specific query-source port suppresses port randomization and can be insecure.
Jul 13 18:26:35 mail named[17343]: command channel listening on 127.0.0.1#953
Jul 13 18:26:35 mail named[17343]: command channel listening on ::1#953
Jul 13 18:26:35 mail named[17343]: zone 0.in-addr.arpa/IN/internal: loaded serial 1
Jul 13 18:26:35 mail named[17343]: empty:4: using RFC1035 TTL semantics
Jul 13 18:26:35 mail named[17343]: zone 10.IN-ADDR.ARPA/IN/internal: loaded serial 1
Jul 13 18:26:35 mail named[17343]: zone 127.in-addr.arpa/IN/internal: loaded serial 1
Jul 13 18:26:35 mail named[17343]: empty:4: using RFC1035 TTL semantics
Jul 13 18:26:35 mail named[17343]: zone 16.172.IN-ADDR.ARPA/IN/internal: loaded serial 1
Jul 13 18:26:35 mail named[17343]: empty:4: using RFC1035 TTL semantics
Jul 13 18:26:35 mail named[17343]: zone 168.192.IN-ADDR.ARPA/IN/internal: loaded serial 1
Jul 13 18:26:35 mail named[17343]: zone 255.in-addr.arpa/IN/internal: loaded serial 1
Jul 13 18:26:35 mail named[17343]: blocked:4: using RFC1035 TTL semantics
Jul 13 18:26:35 mail named[17343]: zone epescarriers.com/IN/internal: loaded serial 29
Jul 13 18:26:35 mail named[17343]: zone epesfms.com/IN/internal: loaded serial 7
Jul 13 18:26:35 mail named[17343]: zone epeslogistics.com/IN/internal: loaded serial 12
Jul 13 18:26:35 mail named[17343]: zone epestransport.com/IN/internal: loaded serial 9
Jul 13 18:26:35 mail named[17343]: blocked:4: using RFC1035 TTL semantics
Jul 13 18:26:35 mail named[17343]: zone tsexpress.com/IN/internal: loaded serial 13
Jul 13 18:26:35 mail named[17343]: zone epescarriers.lan/IN/internal: loaded serial 27
Jul 13 18:26:35 mail named[17343]: zone localhost/IN/internal: loaded serial 2
Jul 13 18:26:35 mail named[17343]: zone 128-28.82.145.12.IN-ADDR.ARPA/IN/external: loaded serial 2009071315
Jul 13 18:26:35 mail named[17343]: zone epescarriers.com/IN/external: loaded serial 2019000003
Jul 13 18:26:35 mail named[17343]: zone epesexpress.com/IN/external: loaded serial 2009071302
Jul 13 18:26:35 mail named[17343]: zone epesfms.com/IN/external: loaded serial 2009071302
Jul 13 18:26:35 mail named[17343]: zone epeslogistics.com/IN/external: loaded serial 2009071302
Jul 13 18:26:35 mail named[17343]: zone epestransport.com/IN/external: loaded serial 2009071302
Jul 13 18:26:35 mail named[17343]: zone tsexpress.com/IN/external: loaded serial 2009071302
Jul 13 18:26:35 mail named[17343]: running
Jul 13 18:26:35 mail named[17343]: zone epescarriers.com/IN/internal: sending notifies (serial 29)
Jul 13 18:26:35 mail named[17343]: zone epescarriers.com/IN/external: sending notifies (serial 2019000003)
Jul 13 18:26:35 mail named[17343]: zone epescarriers.lan/IN/internal: sending notifies (serial 27)
Jul 13 18:26:35 mail named[17343]: zone epestransport.com/IN/external: sending notifies (serial 2009071302)
Jul 13 18:26:35 mail named[17343]: zone tsexpress.com/IN/internal: sending notifies (serial 13)
Jul 13 18:26:35 mail named[17343]: zone epesexpress.com/IN/external: sending notifies (serial 2009071302)
Jul 13 18:26:35 mail named[17343]: zone epeslogistics.com/IN/external: sending notifies (serial 2009071302)
Jul 13 18:26:35 mail named[17343]: zone tsexpress.com/IN/external: sending notifies (serial 2009071302)
Jul 13 18:26:35 mail named[17343]: zone epesfms.com/IN/external: sending notifies (serial 2009071302)
Jul 13 18:26:35 mail named[17343]: zone 128-28.82.145.12.IN-ADDR.ARPA/IN/external: sending notifies (serial 2009071316)

```

..and it looks fine.

Reverse lookups from the outside result in the same fail..

```

root@poweredge:~# host 12.145.82.132 ns.epescarriers.com
Using domain server:
Name: ns.epescarriers.com
Address: 12.145.82.132#53
Aliases: 

Host 132.82.145.12.in-addr.arpa not found: 5(REFUSED)

```

From what I can guess, it's not acting authoritative for that in-addr.arpa zone...

```

Jul 13 18:27:32 mail named[17879]: client 65.188.241.191#60378: view external: query (cache) '132.82.145.12.in-addr.arpa/PTR/IN' denied
Jul 13 18:27:32 mail named[17879]: client 65.188.241.191#51569: view external: query (cache) '132.82.145.12.in-addr.arpa/PTR/IN' denied

```

..but I don't know why! :(

---

### Post by n8bounds on 2009-07-13
If I..

  allow-recursion { any; };
  allow-query { any; };
  allow-query-cache { any; };

in that named.conf for the external view I then get these test results from external...

```
root@poweredge:~# host 12.145.82.132 ns.epescarriers.com
Using domain server:
Name: ns.epescarriers.com
Address: 12.145.82.132#53
Aliases: 

132.82.145.12.in-addr.arpa has no PTR record
root@poweredge:~# dig @ns.epescarriers.com -x 12.145.82.132

; <<>> DiG 9.5.1-P2 <<>> @ns.epescarriers.com -x 12.145.82.132
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 33415
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 13, ADDITIONAL: 13
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;132.82.145.12.in-addr.arpa.	IN	PTR

;; AUTHORITY SECTION:
.			518373	IN	NS	d.root-servers.net.
.			518373	IN	NS	f.root-servers.net.
.			518373	IN	NS	l.root-servers.net.
.			518373	IN	NS	j.root-servers.net.
.			518373	IN	NS	e.root-servers.net.
.			518373	IN	NS	g.root-servers.net.
.			518373	IN	NS	h.root-servers.net.
.			518373	IN	NS	a.root-servers.net.
.			518373	IN	NS	k.root-servers.net.
.			518373	IN	NS	i.root-servers.net.
.			518373	IN	NS	b.root-servers.net.
.			518373	IN	NS	m.root-servers.net.
.			518373	IN	NS	c.root-servers.net.

;; ADDITIONAL SECTION:
a.root-servers.net.	518373	IN	A	198.41.0.4
a.root-servers.net.	518373	IN	AAAA	2001:503:ba3e::2:30
b.root-servers.net.	518373	IN	A	192.228.79.201
c.root-servers.net.	518373	IN	A	192.33.4.12
d.root-servers.net.	518373	IN	A	128.8.10.90
e.root-servers.net.	518373	IN	A	192.203.230.10
f.root-servers.net.	518373	IN	A	192.5.5.241
f.root-servers.net.	518373	IN	AAAA	2001:500:2f::f
g.root-servers.net.	518373	IN	A	192.112.36.4
h.root-servers.net.	518373	IN	A	128.63.2.53
h.root-servers.net.	518373	IN	AAAA	2001:500:1::803f:235
i.root-servers.net.	518373	IN	A	192.36.148.17
j.root-servers.net.	518373	IN	A	192.58.128.30

;; Query time: 43 msec
;; SERVER: 12.145.82.132#53(12.145.82.132)
;; WHEN: Mon Jul 13 18:38:29 2009
;; MSG SIZE  rcvd: 499
```

Which is just my server passing external clients off to the root servers, and STILL being unathoritative...

---

### Post by n8bounds on 2009-07-13
Another strange thing, is that I my nameserver clearly things it is the SOA:

```
root@poweredge:~# dig 128/28.82.145.12.in-addr.arpa @ns.epescarriers.com

; <<>> DiG 9.5.1-P2 <<>> 128/28.82.145.12.in-addr.arpa @ns.epescarriers.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10805
;; flags: qr aa rd; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;128/28.82.145.12.in-addr.arpa.	IN	A

;; AUTHORITY SECTION:
128/28.82.145.12.in-addr.arpa. 86400 IN	SOA	ns.epescarriers.com. postmaster.epescarriers.com. 2009071319 14400 7200 2419200 86400

;; Query time: 38 msec
;; SERVER: 12.145.82.132#53(12.145.82.132)
;; WHEN: Mon Jul 13 19:46:12 2009
;; MSG SIZE  rcvd: 113
```

but no one else does....

```
root@poweredge:~# dig 131.82.145.12.in-addr.arpa. @192.5.5.241

; <<>> DiG 9.5.1-P2 <<>> 131.82.145.12.in-addr.arpa. @192.5.5.241
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 47956
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 4, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;131.82.145.12.in-addr.arpa.	IN	A

;; AUTHORITY SECTION:
12.in-addr.arpa.	86400	IN	NS	DBRU.BR.NS.ELS-GMS.ATT.NET.
12.in-addr.arpa.	86400	IN	NS	CBRU.BR.NS.ELS-GMS.ATT.NET.
12.in-addr.arpa.	86400	IN	NS	DMTU.MT.NS.ELS-GMS.ATT.NET.
12.in-addr.arpa.	86400	IN	NS	CMTU.MT.NS.ELS-GMS.ATT.NET.

;; Query time: 80 msec
;; SERVER: 192.5.5.241#53(192.5.5.241)
;; WHEN: Mon Jul 13 20:08:33 2009
;; MSG SIZE  rcvd: 144

```

---

### Post by n8bounds on 2009-07-13
I have to be close. Look at all this goodness coming back....

```
root@poweredge:~# dig 128/28.82.145.12.in-addr.arpa. any @ns.epescarriers.com

; <<>> DiG 9.5.1-P2 <<>> 128/28.82.145.12.in-addr.arpa. any @ns.epescarriers.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 65184
;; flags: qr aa rd; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 1
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;128/28.82.145.12.in-addr.arpa.	IN	ANY

;; ANSWER SECTION:
128/28.82.145.12.in-addr.arpa. 259200 IN SOA	ns.epescarriers.com. postmaster.epescarriers.com. 2009071320 14400 7200 2419200 86400
128/28.82.145.12.in-addr.arpa. 259200 IN NS	ns.epescarriers.com.
128/28.82.145.12.in-addr.arpa. 259200 IN NS	dmtu.mt.ns.els-gms.att.net.
128/28.82.145.12.in-addr.arpa. 259200 IN NS	dbru.br.ns.els-gms.att.net.

;; ADDITIONAL SECTION:
ns.epescarriers.com.	259200	IN	A	12.145.82.132

;; Query time: 38 msec
;; SERVER: 12.145.82.132#53(12.145.82.132)
;; WHEN: Mon Jul 13 20:10:07 2009
;; MSG SIZE  rcvd: 205

```

It still makes no sense why I can't get a direct answer...

```
root@poweredge:~# dig 131.82.145.12.in-addr.arpa. any @ns.epescarriers.com

; <<>> DiG 9.5.1-P2 <<>> 131.82.145.12.in-addr.arpa. any @ns.epescarriers.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: REFUSED, id: 7391
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;131.82.145.12.in-addr.arpa.	IN	ANY

;; Query time: 40 msec
;; SERVER: 12.145.82.132#53(12.145.82.132)
;; WHEN: Mon Jul 13 20:12:17 2009
;; MSG SIZE  rcvd: 44

```

---

### Post by n8bounds on 2009-07-14
The weird thing is, that is seems to be ALMOST working. For example, from an host external to the Epes network I can do this:

```

# dig -x 12.145.82.130

; <<>> DiG 9.5.1-P2 <<>> -x 12.145.82.130
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12418
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 3, ADDITIONAL: 3

;; QUESTION SECTION:
;130.82.145.12.in-addr.arpa.	IN	PTR

;; ANSWER SECTION:
130.82.145.12.in-addr.arpa. 1963 IN	CNAME	130.128/28.82.145.12.in-addr.arpa.
130.128/28.82.145.12.in-addr.arpa. 129728 IN PTR mail-mx01.epescarriers.com.

;; AUTHORITY SECTION:
128/28.82.145.12.in-addr.arpa. 129728 IN NS	ns.epescarriers.com.
128/28.82.145.12.in-addr.arpa. 129728 IN NS	dmtu.mt.ns.els-gms.att.net.
128/28.82.145.12.in-addr.arpa. 129728 IN NS	dbru.br.ns.els-gms.att.net.

;; ADDITIONAL SECTION:
ns.epescarriers.com.	92998	IN	A	12.145.82.132
dbru.br.ns.els-gms.att.net. 50608 IN	A	199.191.128.106
dmtu.mt.ns.els-gms.att.net. 50608 IN	A	12.127.16.70

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Jul 15 10:00:50 2009
;; MSG SIZE  rcvd: 236

```

But if I query the server directly, the request is refused:

```

root@poweredge:~# dig -x 12.145.82.130 @ns.epescarriers.com

; <<>> DiG 9.5.1-P2 <<>> -x 12.145.82.130 @ns.epescarriers.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: REFUSED, id: 4916
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;130.82.145.12.in-addr.arpa.	IN	PTR

;; Query time: 51 msec
;; SERVER: 12.145.82.132#53(12.145.82.132)
;; WHEN: Wed Jul 15 09:59:13 2009
;; MSG SIZE  rcvd: 44

```

...and I get this in the syslog:

```

Jul 15 10:13:37 mail named[23895]: client 65.188.241.191#57813: view external: query (cache) '130.82.145.12.in-addr.arpa/PTR/IN' denied

```

---

### Post by TruckStuff on 2009-07-30
I know this is a couple of weeks old now, but I'll post in case you are still looking for an answer.

When AT&T delegates reverse zones, they use CIDR notation as recommended in [RFC 2317](http://www.ietf.org/rfc/rfc2317.txt).  They CNAME the individual IPs on their end, so your servers will never actually receive a query for 130.82.145.12.in-addr.arpa from the internet.  The actual query you will receive will be for 130.128/28.82.145.12.in-addr.arpa.  Your servers *may* receive queries for 130.82.142.12.in-addr.arpa from internal machines, however.  So really, you need to define two zones to match each pattern.  Here's now I did it: ```
zone "128/28.82.145.12.in-addr.arpa" {
    type master;
    file "/path/to/zone/file";
};
zone "82.145.12.in-addr.arpa" {
    type master;
    file "/path/to/zone/file";
};
``` Then your zone file will look something like this: ```
$TTL 432000
@       IN      SOA     ns.epescarriers.com. postmaster.epescarriers.com. (
			200907301	; Serial
			1D			; Refresh
			30m		; Retry
			4W 			; Expire
			1D )		; Minimum
		NS	ns.epescarriers.com.	;

129     IN      CNAME   mail.epescarriers.com.

130     IN      PTR     mail-mx01.epescarriers.com.
131     IN      PTR     mail.epescarriers.com.
132     IN      PTR     mail-mx02.epescarriers.com.
``` This handles both reverse zones in a single zone file.  

Notice that your name servers were also different in the zone file than what you originally had.  AT&T's servers are no longer authoritative for this zone, as its been delegated to you. ;)

---

