---
title: "Bind9 Help with Subdomains."
date: 2005-06-01
forum: Server Platforms
---

### Post by Myles3 on 2005-06-01
I have recently install Bind9 on my Ubuntu Warty Server and it seems not to be working with two subdomains. But the rest of fine.
**db.com.domain file** 
```
$TTL 604899
@ IN SOA        dns.domain.com root.domain.com. (
        1               ; Serial
        7200            ; Refresh
        7200            ; Retry
        2419200         ; Expiry
        86400 )         ; Negatice Cache TTL
;
                NS      dns.domain.com.
                NS      ns1.domain.com.
                NS      ns2.domain.com.
                NS      ns3.domain.com.
                MX      10      mail.domain.com.
dns             IN      A       70.85.129.86
ns1             IN      A       70.85.129.86
www             IN      A       70.85.129.86
blog            IN      A       70.85.129.86
idisk           IN      A       70.85.129.86
wiki            IN      A       70.85.129.86
mail            IN      A       70.85.129.86
ftp             IN      A       70.85.129.86
jabber          IN      A       70.85.129.86
projects        IN      A       70.85.129.86
jabber          IN      A       70.85.129.86
ns2             IN      A       209.126.159.118
ns3             IN      A       206.55.124.4
@               IN      A       70.85.129.86
``` 
```
Jun  1 12:46:34 MBserver named[3176]: starting BIND 9.2.4 -u bind
Jun  1 12:46:34 MBserver named[3176]: using 1 CPU
Jun  1 12:46:34 MBserver named[3178]: loading configuration from '/etc/bind/named.conf'
Jun  1 12:46:34 MBserver named[3178]: listening on IPv4 interface lo, 127.0.0.1#53
Jun  1 12:46:34 MBserver named[3178]: listening on IPv4 interface eth0, 70.85.129.86#53
Jun  1 12:46:34 MBserver named[3178]: command channel listening on 127.0.0.1#953
Jun  1 12:46:34 MBserver named[3178]: command channel listening on ::1#953
Jun  1 12:46:34 MBserver named[3178]: zone 0.in-addr.arpa/IN: loaded serial 1
Jun  1 12:46:34 MBserver named[3178]: zone 127.in-addr.arpa/IN: loaded serial 1
Jun  1 12:46:34 MBserver named[3178]: zone 255.in-addr.arpa/IN: loaded serial 1
Jun  1 12:46:34 MBserver named[3178]: zone domain.com/IN: loaded serial 1
Jun  1 12:46:34 MBserver named[3178]: zone localhost/IN: loaded serial 1
Jun  1 12:46:34 MBserver named[3178]: running
Jun  1 12:46:34 MBserver named[3178]: zone domain.com/IN: sending notifies (serial 1)
Jun  1 12:46:34 MBserver named[3178]: received notify for zone 'mylesbraithwaite.com'
Jun  1 12:46:35 MBserver named[3178]: zone ns8.zoneedit.com/IN: refresh: non-authoritative answer from master 206.55.124.4#53
```

---

### Post by LordHunter317 on 2005-06-02
Your zone looks ok to me, so the relevant sections of named.conf would be helpful.

---

