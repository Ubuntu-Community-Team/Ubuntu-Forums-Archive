---
title: "Reverse nslookup fail BIND9 DNS"
date: 2010-02-11
forum: Server Platforms
---

### Post by Ronca_Lapor on 2010-02-11
Hello everyone


I have been trying to get BIND9 to work in our servers here, I have been reaserching and trying a few things here and there; though i got stuck in a particular problem. this is still in testing stage and I hope you guys can help me out.
The problem is:

I have set up bind9 DNS server, created zones; everything seems to work flawlessly but: there is one reverse zone I cannot lookup

I have created 3 zones in bind9; digitata, digitata.au and rorotika; 

BIND9 is installed in "/etc/bind" and the zones are saved under "/etc/bind/zones"

Here is what the 2 files i edited in "/etc/bind" look like

my machine's name is "lobster" BTW

**named.conf**
```
include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";

```**named.conf.local**
```
include "/etc/bind/zones.rfc1918";

zone "digitata" {
        type master;
        file "/etc/bind/zones/digitata.db";
        allow-transfer {
                10.1.1.40;
                10.10.10.2;
        };
};


zone "digitata.au" {
        type master;
        file "/etc/bind/zones/digitata.au.db";
        allow-transfer {
                10.1.1.40;
                10.10.10.2;
        };
};

zone "rorotika" {
        type master;
        file "/etc/bind/zones/rorotika.db";
        allow-transfer {10.1.1.40;};
};


zone "1.10.10.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.1.10.10.in-addr.arpa";
        allow-update { key "rndc-key"; };
        allow-transfer {10.10.1/24; };
};

zone "10.10.10.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.10.10.10.in-addr.arpa";
        allow-update { key "rndc-key"; };
        allow-transfer {10.10.10/24; };
};

zone "1.1.10.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.1.1.10.in-addr.arpa";
        allow-update { key "rndc-key"; };
        allow-transfer {10.1.1/24; };
};

```and this is what the zones files inside /etc/bind/zones

**digitata.au.db**
```
$TTL    604800
digitata.au.    IN      SOA     honeypot.digitata.au. root.digitata.au. (
                        45070101        ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
digitata.au.    IN      NS      honeypot.digitata.au.

honeypot        IN      A       10.10.10.2

```**digitata.db**
```
$TTL    604800
digitata.       IN      SOA     lobster.digitata. root.digitata. (
                         12345856       ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
digitata.       IN      NS      lobster.digitata.


gill            IN      A       10.10.1.7
alfresco        IN      A       10.10.1.23

```**rorotika.db**
```
$TTL    604800
rorotika.       IN      SOA     pancake.rorotika. root.rorotika. (
                        2010011         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
rorotika.       IN      NS      pancake.rorotika.

pancake         IN      A       10.1.1.40
waffle          IN      A       10.1.1.43
rorotikasvr1    IN      A       10.1.1.2

```**rev.10.10.10.in-addr.arpa**
```
$TTL    86400
@       IN      SOA     honeypot.digitata.au. root.localhost. (
                      070101144         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                          86400 )       ; Negative Cache TTL
;
;       IN      NS      alfresco.digitata.
        IN      NS      honeypot.digitata.au.
;       IN      NS      gill.digitata.

2       IN      PTR     honeypot.digitata.au.

```**rev.1.10.10.in-addr.arpa**
```

$TTL    86400
@       IN      SOA     lobster.digitata. root.localhost. (
                        070101153       ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                          86400 )       ; Negative Cache TTL
;
        IN      NS      alfresco.digitata.
;       IN      NS      honeypot.digitata. - commented out because honeypot
 under digitata.au
        IN      NS      gill.digitata.


23      IN      PTR     alfresco.digitata.
7       IN      PTR     gill.digitata.

```**rev.1.1.10.in-addr.arpa**
```
$TTL    86400
@       IN      SOA     pancake.rorotika. root.localhost. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                          86400 )       ; Negative Cache TTL
;
        IN      NS      pancake.rorotika.

40      IN      PTR     pancake.rorotika.

```AND this is what my "/etc/hosts" file and "/etc/resolv.conf" look like

**hosts**
```
# 127.0.0.1     localhost
127.0.1.1       lobster.digitata lobster localhost

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```**resolv.conf**
```
nameserver 10.10.1.23

```WOW that was an awfull lot to read

now if i enter the command
```
nslookup 10.1.1.40
```which happens to be the IP address for pancake.rorotika I get the following:

```
Server:         10.10.1.23
Address:        10.10.1.23#53

40.1.1.10.in-addr.arpa  name = pancake.rorotika.

```however, if i enter either 

```
nslookup 10.10.1.7
```or
```
nslookup 10.10.1.23
```which both happen to be under digitata.db
i get the following messege

```
Server:         10.10.1.23
Address:        10.10.1.23#53

** server can't find 23.1.10.10.in-addr.arpa: SERVFAIL

```why is that, is there something i am missin out on?
Any ideas what could be possible wrong?!?

Thanks all

OFF topic: the whole idea of implementing the DNS server is that so, when we access alfresco share in our machines, instead of typing "http://10.10.1.23/share" we only enter "http://alfresco.digitata/share". Alfresco repositories will also be implemented in rorotika and digitata.au 

that is already possible, though i reckon reverse DNS will be usefull to our company in a near future...

---

### Post by noway2 on 2010-02-12
The "servfail" response suggests something more fundamentally amiss than simply not being able to resolve the IP address. 

Take a look at this post: [http://osdir.com/ml/network.dns.bind9.user/2003-09/msg00333.html](http://osdir.com/ml/network.dns.bind9.user/2003-09/msg00333.html). I found it by googling "in-addr.arpa: SERVFAIL".  I didn't read through it entirely, but it looks like when you have multiple zones like this, having multiple masters gets in the way of doing reverse look ups.

---

