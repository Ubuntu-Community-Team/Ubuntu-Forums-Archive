---
title: "bind load errors"
date: 2017-04-20
forum: Server Platforms
---

### Post by scott-w-reeve on 2017-04-20
Getting bind load errors.
Looks like there's a bug in db.dc.org.
If you have any suggestions they would be greatly appreciated.



From syslog:

```
Apr 14 08:54:04 dcn1 named[3738]: managed-keys-zone: loaded serial 658
Apr 14 08:54:04 dcn1 named[3738]: zone 0.in-addr.arpa/IN: loaded serial 1
Apr 14 08:54:04 dcn1 named[3738]: zone 28.101.10.in-addr.arpa/IN: loaded serial 1
Apr 14 08:54:04 dcn1 named[3738]: zone localhost/IN: loaded serial 2
Apr 14 08:54:04 dcn1 named[3738]: zone 255.in-addr.arpa/IN: loaded serial 1
Apr 14 08:54:04 dcn1 named[3738]: zone 127.in-addr.arpa/IN: loaded serial 1
Apr 14 08:54:04 dcn1 named[3738]: zone dc.org/IN: NS 'dcn1.dc.org' has no address records (A or AAAA)
Apr 14 08:54:04 dcn1 named[3738]: zone dc.org/IN: not loaded due to errors.
Apr 14 08:54:04 dcn1 named[3738]: all zones loaded
```





sreeve@dcn1:/etc/bind$ cat named.conf.local

```
//
// Do any local configuration here
//


// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";


zone "dc.org" {
type master;
file "/etc/bind/db.dc.org";
};


zone "28.101.10.in-addr.arpa" {
type master;
notify no;
file "/etc/bind/db.10";
};

```

sreeve@dcn1:/etc/bind$ cat db.dc.org
```

;
; BIND data file for local loopback interface
;
$TTL 604800
@ IN SOA dcn1.dc.org. root.localhost. (
2 ; Serial
604800 ; Refresh
86400 ; Retry
2419200 ; Expire
604800 ) ; Negative Cache TTL
;
@ IN NS dcn1.dc.org.
@ IN A 127.0.0.1
@ IN AAAA ::1
vsd2 IN A 10.101.28.30
vcentersso IN A 192.168.10.134
xmpp IN A 10.101.28.30
_xmpp-client._tcp.xmpp.dc.org. IN SRV 10 0 5222 vsd2.dc.org.
vsc1man IN A 10.101.28.32
vsc1 IN A 10.101.28.32
vrs1 IN A 192.168.10.150
vrs2 IN A 192.168.10.151
```






sreeve@dcn1:/etc/bind$ cat db.10
```

;
; BIND reverse data file for local loopback interface
;
$TTL 604800
@ IN SOA dcn1.dc.org. root.localhost. (
1 ; Serial
604800 ; Refresh
86400 ; Retry
2419200 ; Expire
604800 ) ; Negative Cache TTL
;
@ IN NS dcn1.dc.org.


30 IN PTR vsd2.dc.org.
134 IN PTR vcentersso.dc.org.
140 IN PTR vsc1man.dc.org.
32 IN PTR vsc1.dc.org.
150 IN PTR vrs1.dc.org.
152 IN PTR vrs2.dc.org.
154 IN PTR vrs3.dc.org.
```

---

### Post by Doug S on 2017-04-20
You have not defined dcn1.dc.org. I would make the SOA just dc.org, defining it, and then define dcn1.dc.org separately. As below (where I have given arbitrary IP addresses to them):

```
;
; BIND data file for local loopback interface
;
$TTL 604800
@ IN SOA dc.org. root.localhost. (
2 ; Serial
604800 ; Refresh
86400 ; Retry
2419200 ; Expire
604800 ) ; Negative Cache TTL
  IN A 10.101.28.30
;
@ IN NS dcn1.dc.org.
@ IN A 127.0.0.1
@ IN AAAA ::1
dcn1 IN A 10.101.28.30

vsd2 IN A 10.101.28.30
vcentersso IN A 192.168.10.134
xmpp IN A 10.101.28.30
_xmpp-client._tcp.xmpp.dc.org. IN SRV 10 0 5222 vsd2.dc.org.
vsc1man IN A 10.101.28.32
vsc1 IN A 10.101.28.32
vrs1 IN A 192.168.10.150
vrs2 IN A 192.168.10.151

```Which now passes the check:
```
doug@DOUG-64:~/config/etc/bind/tempq$ named-checkzone dc.org db.dc.org
zone dc.org/IN: loaded serial 2
OK

```
EDIT: Oh, by the way, db.10 doesn't make sense. For example a reverse lookup of vrs1.dc.org will give 10.101.28.150, not 192.168.10.150.

---

### Post by scott-w-reeve on 2017-04-20
True about the vrs1.dc.org - hadn't gotten to that part of it yet.
But hey - it loads fine and all my errors are gone.
Looks to be working great - thank you.

---

