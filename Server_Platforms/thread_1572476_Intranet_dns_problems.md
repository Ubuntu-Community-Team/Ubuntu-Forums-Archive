---
title: "Intranet dns problems"
date: 2010-09-11
forum: Server Platforms
---

### Post by zakarra on 2010-09-11
Hi,

I have a problem with Ubuntu dns server. i think that the problem is with dns server but maybe could be a concept error, i'm not so sure. My net estructure is next one.

85.86.x.x    10.0.x.x       192.168.2.1      192.168.2.x
Internet ->   router1 ->  router2      ->    LAN (dns server, 2 linux server, 3 pcs)

router1 redirect all ports to router2
router2 redirect all ports to dns server
dns server redirect to linux servers

from intranet dns server runs ok, everithing goes perfect, but when i try to conect from a internet, my domain points to correct IP but the enruting dies when it arrives to dns server.

these are my configuration files

named.conf.local

```
 

    zone "server.net" {
        type master;
        file "/etc/bind/db.server";
    };


    zone "example.com" {
        type master;
        file "/etc/bind/db.example";
    };



    zone "example2.com" {
        type master;
        file "/etc/bind/db.example2";
    };

 
zone "192.in-addr.arpa" {
    type master;
    file "/etc/bind/db.192";
};

``` db.example & db.server (just change zone name)

```

$TTL    604800
example.com.    IN    SOA    ns0.server.net. root.server.net. (
                  1        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
    IN     NS    ns0.server.net.


$ORIGIN example.com.
ns0    IN    A    192.168.2.254
www    IN    A    192.168.2.200
server1    IN    A    192.168.2.200

```db.example2


```

$TTL    604800
example2.com.    IN    SOA    ns0.server.net. root.server.net. (
                  1        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
    IN     NS    ns0.server.net.


$ORIGIN example2.com.
ns0    IN    A    192.168.2.254
www    IN    A    192.168.2.300
server1    IN    A    192.168.2.200

```Please, help & thanks!

---

### Post by terazen on 2010-09-13
I assume you are trying to get to a webpage and it's resolving to 192.168.2.200, but you aren't pulling up the webpage.  If that's the case then the issue is 192.168.*.* ip addresses can't go on the internet.  You would need to setup an internal zone and external zone in bind and have internal resolve to the 192.168 ip and external clients resolve the 85.86 ip.

---

