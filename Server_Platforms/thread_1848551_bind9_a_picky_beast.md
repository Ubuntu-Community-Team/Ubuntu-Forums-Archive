---
title: "bind9 a picky beast"
date: 2011-09-22
forum: Server Platforms
---

### Post by mikeym on 2011-09-22
Hi,

I've spent quite a bit of time today trying to get a simple bind9 setup. I have one server for my home network that I would like to handle DNS caching and FQDN resolution for my little network. 

I've tried a number of examples and none have even given me a simple working config. Examining the logged output I've managed to get something that seems to work, but it seems to be a picky beast about what it will accept. 

I've had to make a number of guesses to get it here. I would love to get feedback to know if there are any obvious mistakes from people who know. :)

Here are my configs:

**/etc/bind/named.conf.local**
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "indigenous" {
        type master;
        file "/etc/bind/db.indigenous";
};

zone "0.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192";
};
```

**/etc/bind/named.conf.options** has my forward DNSs

**/etc/bind/db.192**
```
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.hub. root.jon.hub. (
                     2011092201         ; Serial YYYMMDD## where ## is 00 to 99
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.hub.
1       IN      PTR     modem.hub.
2       IN      PTR     jon.hub.
2       IN      PTR     ns.hub.
2       IN      PTR     www.hub.
2       IN      PTR     mail.hub.
3       IN      PTR     tom.hub.
4       IN      PTR     don.hub.
```

**/etc/bind/db.indigenous**
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.hub. root.jon.hub. (
                     2011092209         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.hub.
@       IN      A       192.168.0.2
ns      IN      A       192.168.0.2
www     IN      A       192.168.0.2
mail    IN      A       192.168.0.2
        IN      MX 10   mail.hub.
jon     IN      A       192.168.0.2
tom     IN      A       192.168.0.3
don     IN      A       192.168.0.4
modem   IN      A       192.168.0.1
```

---

### Post by hawkmage on 2011-09-22
Where you define 'zone "indigenous"'  with the zone file would indicate that you are defining FQDN for  your hosts like:
tom.indigenous
jon.indigenous
mail.indigenous

But when you have defined the reverse zone your hosts are:
tom.hub
jon.hub
mail.hub

If you want the forward and reverse to match change the "indigenous" to "indigenous"

---

### Post by mikeym on 2011-09-23
Erm... woopse. Missed that one. Yes in fact all are "indigenous" in the original file. I changed the network IP, hostnames and domain for security reasons before posting online, while leaving the general structure the same.

When trying variations the file I tried to reduce the number of times I had the same IP address for my server written using CNAME's and A's but couldn't make any of my attempts work.

---

### Post by e_torano on 2011-09-23
Are you set on using BIND? NSD is much lighter and easier to setup in my experience. It's what I always use anyway.

---

