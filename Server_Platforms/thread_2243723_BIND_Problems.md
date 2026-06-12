---
title: "BIND Problems"
date: 2014-09-10
forum: Server Platforms
---

### Post by Tithos on 2014-09-10
Following this link, I have been tring to bind youplus.biz 66.96.162.140(domain) to 192.169.218.8(hosting)


[http://linuxconfig.org/linux-dns-server-bind-configuration](http://linuxconfig.org/linux-dns-server-bind-configuration)


here is my stuff


File: db.youplus.biz


    ```
;
    ; BIND data file for youplus.biz
    ;
    $TTL    3h
    @       IN      SOA     NS1.DOMAIN.COM. youplus.biz. (
                              1        ; Serial
                              3h       ; Refresh after 3 hours
                              1h       ; Retry after 1 hour
                              1w       ; Expire after 1 week
                              1h )     ; Negative caching TTL of 1 day
    ;
    @       IN      NS      NS1.DOMAIN.COM.
    @       IN      NS      NS2.DOMAIN.COM.
    
    youplus.    IN      MX      30      mx.youplus.biz.
    youplus.    IN      A   192.169.218.8
    ;ns1                     IN      A       NS1.DOMAIN.COM.
    ;ns2                     IN      A       NS2.DOMAIN.COM.
    www 


                    IN      CNAME   youplus.biz.

```
File: db.218.169.192
```

    ; BIND reverse data file for 218.169.192.in-addr.arpa
    ;
    $TTL    604800
    218.169.192.in-addr.arpa.      IN      SOA     NS1.DOMAIN.COM. youplus.biz. (
                              1         ; Serial
                              3h       ; Refresh after 3 hours
                              1h       ; Retry after 1 hour
                              1w       ; Expire after 1 week
                              1h )     ; Negative caching TTL of 1 day
    ;
    218.169.192.in-addr.arpa.       IN      NS      NS1.DOMAIN.COM.
    218.169.192.in-addr.arpa.       IN      NS      NS2.DOMAIN.COM.
    
    
    8.218.169.192.in-addr.arpa.   IN      PTR     youplus.biz.

```
When I do :** $named-checkzone 0.168.192.in-addr.arpa /etc/bind/zones/master/db.218.169.192**


I get:
```

    /etc/bind/zones/master/db.218.169.192:5: ignoring out-of-zone data (218.169.192.in-addr.arpa)
    /etc/bind/zones/master/db.218.169.192:12: ignoring out-of-zone data (218.169.192.in-addr.arpa)
    /etc/bind/zones/master/db.218.169.192:13: ignoring out-of-zone data (218.169.192.in-addr.arpa)
    /etc/bind/zones/master/db.218.169.192:16: ignoring out-of-zone data (8.218.169.192.in-addr.arpa)
    zone 0.168.192.in-addr.arpa/IN: has 0 SOA records
    zone 0.168.192.in-addr.arpa/IN: has no NS records
    zone 0.168.192.in-addr.arpa/IN: not loaded due to errors.

```
The strange thing is when I do 


**dig @192.169.218.8 [www.youplus.biz**]("http://www.youplus.biz**")
and
**ping youplus.biz**


form within the server I get 
```

    ; <<>> DiG 9.9.5-3-Ubuntu <<>> @192.169.218.8 www.youplus.biz
    ; (1 server found)
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10575
    ;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1
    
    ;; OPT PSEUDOSECTION:
    ; EDNS: version: 0, flags:; udp: 4096
    ;; QUESTION SECTION:
    ;www.youplus.biz.        IN    A
    
    ;; ANSWER SECTION:
    www.youplus.biz.    10800    IN    CNAME    youplus.biz.
    
    ;; AUTHORITY SECTION:
    youplus.biz.        3600    IN    SOA    NS1.DOMAIN.COM. youplus.biz. 1 10800 3600 604800 3600
    
    ;; Query time: 0 msec
    ;; SERVER: 192.169.218.8#53(192.169.218.8)
    ;; WHEN: Wed Sep 10 13:00:21 MST 2014
    ;; MSG SIZE  rcvd: 108

```
and 
```

    root@youplus:/etc/bind/zones/master# ping youplus.biz 
    PING youplus.biz (192.169.218.8) 56(84) bytes of data.
    64 bytes from youplus.biz (192.169.218.8): icmp_seq=1 ttl=64 time=0.022 ms
    64 bytes from youplus.biz (192.169.218.8): icmp_seq=2 ttl=64 time=0.021 ms
    64 bytes from youplus.biz (192.169.218.8): icmp_seq=3 ttl=64 time=0.028 ms

```


Any thoughts?  This is driving me up the wall

---

### Post by SeijiSensei on 2014-09-11
Some places your files have 192.169, but others have 192.168.  Only the latter is a legitimate private address space.

The address space 192.169.128.0 - 192.169.255.255 [belongs to GoDaddy]("http://whois.arin.net/rest/nets;q=192.169.218.0?showDetails=true&showARIN=false&ext=netref2").  Is that your provider?  You cannot create reverse entries for this subnet since you do not control it.  You would have to coordinate with GoDaddy to set that up for you.

---

