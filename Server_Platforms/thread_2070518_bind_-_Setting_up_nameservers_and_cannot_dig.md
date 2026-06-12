---
title: "bind - Setting up nameservers and cannot dig"
date: 2012-10-13
forum: Server Platforms
---

### Post by framework on 2012-10-13
Hello all,

I'm setting up nameservers and I cannot dig from the actual nameserver. Any ideas? 

```
me@ns1:/etc/bind/zones$ dig @x.x.x.x domain.com

; <<>> DiG 9.8.1-P1 <<>> @x.x.x.x domain.com
; (1 server found)
;; global options: +cmd
;; connection timed out; no servers could be reached

```





named.conf.local:

```
zone "domain.com" {
       type master;
       file "/etc/bind/zones/master/db.domain.com";
};

zone "x.x.x.in-addr.arpa" {
       type master;
       file "/etc/bind/zones/master/db.x.x.x";
};
```


db.domain.com:

```
;
; BIND data file for domain.com
;
$TTL    3h
@       IN      SOA     ns1.domain.com. admin.domain.com. (
                          1        ; Serial
                          3h       ; Refresh after 3 hours
                          1h       ; Retry after 1 hour
                          1w       ; Expire after 1 week
                          1h )     ; Negative caching TTL of 1 day
;
@       IN      NS      ns1.domain.com.
@       IN      NS      ns2.domain.com.


domain.com.    IN      MX      10      mail.domain.com.
domain.com.    IN      A       x.x.x.x
ns1                     IN      A       x.x.x.x
ns2                     IN      A       x.x.x.x
www                     IN      CNAME   domain.com.
mail                    IN      A       x.x.x.x
```


db.x.x.x:

```
;
; BIND reverse data file for x.x.x.in-addr.arpa
;
$TTL    604800
x.x.x.in-addr.arpa.      IN      SOA     ns1.domain.com. admin.domain.com. (
                          1         ; Serial
                          3h       ; Refresh after 3 hours
                          1h       ; Retry after 1 hour
                          1w       ; Expire after 1 week
                          1h )     ; Negative caching TTL of 1 day
;
x.x.x.in-addr.arpa.       IN      NS      ns1.domain.com.
x.x.x.in-addr.arpa.       IN      NS      ns2.domain.com.

x.x.x.x.in-addr.arpa.   IN      PTR     domain.com.
```

---

