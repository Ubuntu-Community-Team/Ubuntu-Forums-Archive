---
title: "BIND configuration for mirror sites"
date: 2009-05-23
forum: Server Platforms
---

### Post by devaparvata on 2009-05-23
I have 2 registered domains let's say domain1.com and domain2.com

On Ubuntu Server 8.04.2, it is installed bind9.

I configured bind for domain1.com and it works perfect. Here are the configuration files.
/etc/bind/named.conf.local
/etc/bind/db.domain1.com
/etc/bind/db.192

> /etc/bind/named.conf.local

```


zone "domain1.com" {
type master;
file "/etc/bind/db.domain1.com";
        };

zone "86.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192";
}; 

```



> /etc/bind/db.domain1.com 


```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.domain1.com. root.domain1.com. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.domain1.com.
@       IN      A       192.168.86.10

```


> /etc/bind/db.192 

```
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.domain1.com. root.domain1.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
10      IN      PTR     ns.domain1.com.
```



These are all as standard configuration, nothing tricky.

For domain2.com I made some changes (as bold)

> /etc/bind/named.conf.local

```


zone "domain1.com" {
type master;
file "/etc/bind/db.domain1.com";
        };

[B]zone "domain2.com" {
type master;
file "/etc/bind/db.domain2.com";
        };[/B]

zone "86.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192";
}; 

```


QUOTE]/etc/bind/**db.domain2.com **
[/QUOTE]

```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     **ns.domain2.com. root.domain2.com.** (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS     ** ns.domain2.com.**
@       IN      A       192.168.86.10

```


> /etc/bind/db.192 

```
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.domain1.com. root.domain1.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
10      IN      PTR     ns.domain1.com.

[B]$TTL    604800
@       IN      SOA     ns.domain2.com. root.domain2.com. (
                              3         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
10      IN      PTR     ns.domain2.com.[/B]


```


However it does not work. In > /var/log/daemon.log

```
dns_master_load: /etc/bind/db.192:26: 86.168.192.in-addr.arpa: multiple RRs of singleton type
zone 86.168.192.in-addr.arpa/IN: loading from master file /etc/bind/db.192 failed: multiple RRs of singleton type
zone domain1.com/IN NS 'ns1.domain1.com" has no address records (A or AAAA)
zone domain1.com/IN: loaded serial 1
running
zone domain1.com/IN: sending notifies (serial 1)
client XX.XXX.XXX.XXX#61563: query (cache) 'domain2.com/A/IN' denied
unexpected RCODE (REFUSED) resolving 'domain2.com/A/IN': XX.XXX.XXX.XXX#53
...
```

Can anyone help what how should I configure bind to host one site with two different hostnames?

---

### Post by kvizz on 2009-05-24
> **devaparvata said:**
> 

```

zone domain1.com/IN NS 'ns1.domain1.com" has no address records (A or AAAA)
...
```


took a quick look at your configs and did not see any records for ns1.domain1.com

---

