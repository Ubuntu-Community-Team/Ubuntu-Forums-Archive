---
title: "DNS bind error"
date: 2012-02-24
forum: Security
---

### Post by gishaust on 2012-02-24
Hi ubuntu people I an setting up bind9 dns this is my first go. I keep getting the errors but I don't know how to fix it.

```

named-checkzone gishaust-office.com /etc/bind/db.gishaust-office.com
dns_master_load: /etc/bind/db.gishaust-office.com:29: gishaust-office.com: multiple RRs of singleton type
zone gishaust-office.com/IN: loading from master file /etc/bind/db.gishaust-office.com failed: multiple RRs of singleton type
zone gishaust-office.com/IN: not loaded due to errors.


```


This is what the file contains can anyone tell where I am going wrong?

```

;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     gishaust-office. gishaust.gishaust.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      localhost.
@       IN      A       127.0.0.1
@       IN      AAAA    ::1

;
;setups the local network
;
$TTL    604800
@       IN      SOA     ns.gishaust-office.com. gishaust.gishaust.com. (
                              3         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.gishaust-office.com.
@       IN      A       10.1.1.2
@       IN      AAAA    ::1
ns      IN      A       10.1.1.2



```

---

### Post by Doug S on 2012-02-24
It looks as though you have two completley different files merged as one file. If you delete the first 15 lines of your file it will pass named-checkzone (I tested it).
Once you get bind working, you can set the name server as localhost elsewhere, for that one computer. For example I set it as a prepend line in my dhclient.conf file.```
send host-name "<hostname>";
#prepend domain-name-servers 192.168.111.1;
prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;

``` I hope this helps.

---

### Post by Jonathan L on 2012-02-25
Hi

Just to clarify the error message a little:
```
dns_master_load: /etc/bind/db.gishaust-office.com:29:
gishaust-office.com: multiple RRs of singleton type
```

It's complaining that you have multiple "resource records" (ie, lines) for a record type for which only one record is allowed.

It's perfectly allowed to have multiple A records, multiple NS records and so on, but you're only allowed to have a single SOA record for each domain, which is the problem you have here.

Hope that's a little use.

Jonathan.

---

