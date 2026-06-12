---
title: "Bind9 Internal DNS issue"
date: 2011-05-12
forum: Server Platforms
---

### Post by marcanthony81 on 2011-05-12
I'm running Ubuntu 10.10 Kernel 2.6.35-28-generic with BIND version: 9.7.1-P2 installed. I created a domain for internal purposes only 'example.local', but for some reason I can not ping the FQDN. Oddly enough though I can however ping the hostname. 

For example:

1) Pinging just the host name works fine!

root@host1:/# ping host1
PING host1.example.local (192.168.0.69) 56(84) bytes of data.
64 bytes from host1.example.local (192.168.0.69): icmp_req=1 ttl=64 time=0.026 ms
64 bytes from host1.example.local (192.168.0.69): icmp_req=2 ttl=64 time=0.031 ms
^C
--- host1.example.local ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.026/0.028/0.031/0.005 ms

2) Pinging the internal FQDN doesn't work!

root@host1:/# ping host1.example.local
ping: unknown host host1.example.local

My config files: (very simple)

(named.conf.local)

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "example.local" {
        type master;
        file "/etc/bind/db.example.local";
};

zone "0.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192";
};

(zone files)

$TTL    30m
$ORIGIN example.local.

@       IN      SOA     host1.example.local. root.example.local. (
                     2011051203         ; Serial
                             1h         ; Refresh
                            15m         ; Retry
                             4w         ; Expire
                            10m)        ; Negative Cache TTL
;

@       IN      NS      host1.example.local.
@       IN      MX      10 host1.example.local.

host1      IN      A       192.168.0.69
host2      IN      A       192.168.0.70
router          IN      A       192.168.0.1

----------------------------------------------------------------------

$TTL    30m

@       IN      SOA     host1.example.local. root.example.local. (
                     2011051201         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;

@       IN      NS      host1.example.local. 

69      IN      PTR     host1.example.local. 
70      IN      PTR     host2.example.local. 
1       IN      PTR     router.example.local.

---

### Post by hawkmage on 2011-05-12
What do you get if you use nslookup like this:
```
nslookup host1 192.168.0.69
nslookup host1.example.local 192.168.0.69
```

Also what do you have onthe "hosts" line in the /etc/nsswitch.conf file?

---

