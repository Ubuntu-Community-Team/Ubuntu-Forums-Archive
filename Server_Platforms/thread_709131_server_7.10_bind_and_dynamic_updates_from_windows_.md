---
title: "server 7.10: bind and dynamic updates from windows clients: how?"
date: 2008-02-27
forum: Server Platforms
---

### Post by MarvinFS on 2008-02-27
](*,)
Guys, please assist! I'm sure it was discussed before, but cant find any real answer. I have ubuntu 7.10 server with bind and dhcp running on private 11.0.0.0/24 network. I got several winxp sp2 clients connecting and getting dhcp addresses (11.0.0.128-11.0.0.138 range) from this server (11.0.0.2)
but i cant get windows clients to update their corresponding records in forward lookup zone on bind! ARE DYNAMIC UPDATES POSSIBLE from windows xp to bind9?
(on windows's network properties i got "localdomain" as primary DNS suffix set up and register in dns checkbox is checked)

when on windows client i do ipconfig /registerdns 
it writes the following to daemon.log
Feb 27 13:10:12 stest dhcpd: DHCPREQUEST for 11.0.0.130 from 00:0c:29:7a:36:d7 via eth1
Feb 27 13:10:12 stest dhcpd: DHCPACK on 11.0.0.130 to 00:0c:29:7a:36:d7 via eth1
Feb 27 13:15:12 stest dhcpd: DHCPREQUEST for 11.0.0.130 from 00:0c:29:7a:36:d7 via eth1
Feb 27 13:15:12 stest dhcpd: DHCPACK on 11.0.0.130 to 00:0c:29:7a:36:d7 via eth1
Feb 27 13:20:12 stest dhcpd: DHCPREQUEST for 11.0.0.130 from 00:0c:29:7a:36:d7 via eth1
Feb 27 13:20:12 stest dhcpd: DHCPACK on 11.0.0.130 to 00:0c:29:7a:36:d7 via eth1
Feb 27 13:25:12 stest dhcpd: DHCPREQUEST for 11.0.0.130 from 00:0c:29:7a:36:d7 via eth1
Feb 27 13:25:12 stest dhcpd: DHCPACK on 11.0.0.130 to 00:0c:29:7a:36:d7 via eth1
Feb 27 13:30:12 stest dhcpd: DHCPREQUEST for 11.0.0.130 from 00:0c:29:7a:36:d7 via eth1
Feb 27 13:30:12 stest dhcpd: DHCPACK on 11.0.0.130 to 00:0c:29:7a:36:d7 via eth1
Feb 27 13:35:12 stest dhcpd: DHCPREQUEST for 11.0.0.130 from 00:0c:29:7a:36:d7 via eth1
Feb 27 13:35:12 stest dhcpd: DHCPACK on 11.0.0.130 to 00:0c:29:7a:36:d7 via eth1
Feb 27 13:40:12 stest dhcpd: DHCPREQUEST for 11.0.0.130 from 00:0c:29:7a:36:d7 via eth1
Feb 27 13:40:13 stest dhcpd: DHCPACK on 11.0.0.130 to 00:0c:29:7a:36:d7 via eth1
Feb 27 13:45:13 stest dhcpd: DHCPREQUEST for 11.0.0.130 from 00:0c:29:7a:36:d7 via eth1
Feb 27 13:45:13 stest dhcpd: DHCPACK on 11.0.0.130 to 00:0c:29:7a:36:d7 via eth1
Feb 27 13:50:13 stest dhcpd: DHCPREQUEST for 11.0.0.130 from 00:0c:29:7a:36:d7 via eth1
Feb 27 13:50:13 stest dhcpd: DHCPACK on 11.0.0.130 to 00:0c:29:7a:36:d7 via eth1
Feb 27 13:55:13 stest dhcpd: DHCPREQUEST for 11.0.0.130 from 00:0c:29:7a:36:d7 via eth1
Feb 27 13:55:13 stest dhcpd: DHCPACK on 11.0.0.130 to 00:0c:29:7a:36:d7 via eth1

and nothing about zone updates... 

BTW from my w2k3 server i've managed to get updates but only for reverse zone... still no updates for forward zone...

Reverse lookupzone
**pri.0.0.11.in-addr.arpa**
$ORIGIN .
$TTL 86400  ; 1 day
0.0.11.in-addr.arpa IN SOA  stest.localdomain. root.localhost. (
        2008021417 ; serial
        604800     ; refresh (1 week)
        86400      ; retry (1 day)
        2419200    ; expire (4 weeks)
        86400      ; minimum (1 day)
        )
      NS  stest.localdomain.
      NS  ns.localdomain.
$ORIGIN 0.0.11.in-addr.arpa.
$TTL 1200 ; 20 minutes
128     PTR SBS.test.local.
129     PTR SBS.localdomain.
$TTL 86400  ; 1 day
2     PTR localdomain.

forward lookup zone
**db.localdomain**
$TTL  86400
@ IN  SOA stest.localdomain. root.localhost. (
      2008021414  ; Serial
       604800   ; Refresh
        86400   ; Retry
      2419200   ; Expire
        86400 ) ; Negative Cache TTL
;
@ IN  NS  stest.localdomain.
@ IN  NS  ns.localdomain.
@ IN  MX  10  stest.localdomain.
localdomain.  A 11.0.0.2
www A 11.0.0.2
stest A 11.0.0.2
ns  A 11.0.0.2


**named.conf.options**
options {
  directory "/etc/bind";
 auth-nxdomain no;    # conform to RFC1035
version "[secured]";
statistics-file "/var/run/named.stats";
dump-file "/var/run/named.db";
#
#pid-file "/var/run/named/named.pid";
forwarders {10.0.0.2;};
};

**named.conf**
include "/etc/bind/named.conf.options";
zone "." {
  type hint;
  file "/etc/bind/db.root";
};

zone "localhost" {
  type master;
  file "/etc/bind/db.local";
};

zone "localdomain" {
  type master;
    allow-update {any;};
  file "/etc/bind/db.localdomain";
};

zone "0.0.11.in-addr.arpa" {
  type master;
    allow-update {11.0.0.0/24;};
  file "/etc/bind/pri.0.0.11.in-addr.arpa";
};
zone "127.in-addr.arpa" {
  type master;
  file "/etc/bind/db.127";
};
zone "0.in-addr.arpa" {
  type master;
  file "/etc/bind/db.0";
};
zone "255.in-addr.arpa" {
  type master;
  file "/etc/bind/db.255";
};

---

### Post by opus on 2008-02-27
I think the problem is you are using "localdomain".  I think that is reserved for only the local host, much like localhost is.  Try setting it up using some other domain name and allow updates on that zone.

---

### Post by MarvinFS on 2008-02-27
nop! changed my linux domain everywhere from "localdomain" to "mtest" (in dhcp, in hosts, in named and zonez) didn't do the trick! just the same behavior. wxp register's nothing. w2k3 server updates only reverse zone.  any ideas?

---

### Post by MarvinFS on 2008-02-28
seems to me that it's internal ubuntu sucksness!!! it uses old dhcpd version 2 which is not yet supporting ddns * options in .conf. ****! i had to check version first!!!! for god sake it should me mentioned somewhere in FAQ!!! i broke my head off working on that issue...

---

### Post by MarvinFS on 2008-03-01
it's my lameness! :) 
i did apt-get install dhcp
but not the
apt-get install dhcp3-server

****! :) lost a week...

---

