---
title: "DNS update by DHCPD"
date: 2008-11-20
forum: Server Platforms
---

### Post by Koybe on 2008-11-20
Hello,

I'm using Bind9 and Dhcpd3 on a Hardy Server. I would like to make the dhcp update dns records automaticaly. I've already set this up on Dapper somme times ago.

I think, I've made it, but anyway, my reverse zone update well and my forward zone don't. I'm getting mad, so if you have any good idea. 

Here are some infos: 

/etc/bind/named.conf.local (other bind conf files aren't modified) :
```
controls {
         inet 127.0.0.1 allow { localhost; } keys { rndc-key; };
};
include "/etc/bind/rndc.key";

zone "my.local" {
        type master;
        file "my.local.zone";
        allow-update { key rndc-key; };
        notify yes;
};

zone "1.168.192.in-addr.arpa" {
        type master;
        file "reverse.zone";
        allow-update { key rndc-key; };
        notify yes;
};
```/var/cache/bind/my.local.zone :
```
$TTL    86400
@       IN      SOA     my.local. root.my.local. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                          86400 )       ; Negative Cache TTL
;
@       IN      NS      serv.my.local.

serv IN      A       192.168.1.1
```/var/cache/bind/reverse.zone (as you can see it is update and I have a jnl file)
```
$ORIGIN .
$TTL 86400      ; 1 day
1.168.192.in-addr.arpa  IN SOA  my.local. root.my.local. (
                                4          ; serial
                                604800     ; refresh (1 week)
                                86400      ; retry (1 day)
                                2419200    ; expire (4 weeks)
                                86400      ; minimum (1 day)
                                )
                        NS      serv.my.local.
$ORIGIN 1.168.192.in-addr.arpa.
$TTL 300        ; 5 minutes
150                     PTR     portable.my.local.
$TTL 86400      ; 1 day
1                      PTR     serv.my.local.
```/etc/dhcp3/dhcpd.conf : (lease time is short for testing purpose)
```
include "/etc/bind/rndc.key";

zone my.local {
        primary 127.0.0.1;
        key rndc-key;
}
zone 1.168.192.in-addr.arpa {
        primary 127.0.0.1;
        key rndc-key;
}

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style interim;
ddns-updates on;
allow client-updates;

# option definitions common to all supported networks...
option domain-name "my.local";
option domain-name-servers 192.168.1.1;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.50 192.168.1.150;
  option routers 192.168.1.1;
}
```Here's what i can see in logs :
/var/log/syslog :
```
Nov 20 14:53:19 serv named[8334]: client 127.0.0.1#36732: updating zone '1.168.192.in-addr.arpa/IN': deleting rrset at '150.1.168.192.in-addr.arpa' PTR
Nov 20 14:53:19 serv named[8334]: client 127.0.0.1#36732: updating zone '1.168.192.in-addr.arpa/IN': adding an RR at '150.1.168.192.in-addr.arpa' PTR
Nov 20 14:53:19 serv named[8334]: journal file reverse.zone.jnl does not exist, creating it
Nov 20 14:53:19 serv named[8334]: zone 1.168.192.in-addr.arpa/IN: sending notifies (serial 2)
Nov 20 14:53:19 serv dhcpd: added reverse map from 150.1.168.192.in-addr.arpa. to portable.my.local
Nov 20 14:53:19 serv dhcpd: DHCPREQUEST for 192.168.1.150 from 00:18:8b:d1:ce:9e via eth0
Nov 20 14:53:19 serv dhcpd: DHCPACK on 192.168.1.150 to 00:18:8b:d1:ce:9e (portable) via eth0
```

rndc file is readable by bind and dhcp user, dhcp and dns work perfectly, just the update is missing.

I hope someone will have an idea ;) Thank you.

---

### Post by Koybe on 2008-11-27
Up!

---

