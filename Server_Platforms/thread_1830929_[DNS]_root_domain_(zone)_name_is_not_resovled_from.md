---
title: "[DNS] root domain (zone) name is not resovled from local network"
date: 2011-08-22
forum: Server Platforms
---

### Post by kalosh on 2011-08-22
Hello.
First I like to say hello to all of you:) I am quite new to linux (few years ago I have been using debian as my home server OS). Now it is time to check my admin skills:)
I have reached problem which I cannot solve by myself.
So:
I have public IP and registered domain mydomain.eu. On domain provider DNS servers, mydomain.eu points to my machine called solis (10.10.10.1; this is gateway, dhcp and dns server; eth0 is outsite, eth1 inside my network). I have also laptop which is connected to eth1 through wireless AP. From laptop and solis I have access to outside and inside network without problems. But there is a 'but': from my local network (laptop or solis) name mydomain.eu is not resolved:
```
kalosh@solis:~$ nslookup mydomain.eu
Server:         10.10.10.1
Address:        10.10.10.1#53

*** Can't find mydomain.eu: No answer
```from outside the result is:
```
C:\Users\laptop>nslookup mydomain.eu
Server:  plusmx4.polkomtel.com.pl
Address:  212.2.96.54

Non authoritative ansver
Name:   mydomain.eu
Address:  mysuperhiddenpublicIP
```From my local network (laptop or solis) I am able to resolve the name solis.mydomain.eu:
```
nslookup solis.mydomain.eu
Server:         10.10.10.1
Address:        10.10.10.1#53

Name:   solis.mydomain.eu
Address: 10.10.10.1
```Now the bind configuration files:
named.config
```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";

```named.conf.options:
```
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders {
                62.129.252.30; // my domain provider's DNS
                195.66.144.2; // ISP DNS
                217.17.34.10; // ISP DNS
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};
```named.conf.local:
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
include "/etc/bind/zones.rfc1918";
```/etc/bind/zones.rfc1918:
```
zone "10.in-addr.arpa"      { type master; file "/etc/bind/db.empty"; };

zone "16.172.in-addr.arpa"  { type master; file "/etc/bind/db.empty"; };
zone "17.172.in-addr.arpa"  { type master; file "/etc/bind/db.empty"; };
zone "18.172.in-addr.arpa"  { type master; file "/etc/bind/db.empty"; };
zone "19.172.in-addr.arpa"  { type master; file "/etc/bind/db.empty"; };
zone "20.172.in-addr.arpa"  { type master; file "/etc/bind/db.empty"; };
zone "21.172.in-addr.arpa"  { type master; file "/etc/bind/db.empty"; };
zone "22.172.in-addr.arpa"  { type master; file "/etc/bind/db.empty"; };
zone "23.172.in-addr.arpa"  { type master; file "/etc/bind/db.empty"; };
zone "24.172.in-addr.arpa"  { type master; file "/etc/bind/db.empty"; };
zone "25.172.in-addr.arpa"  { type master; file "/etc/bind/db.empty"; };
zone "26.172.in-addr.arpa"  { type master; file "/etc/bind/db.empty"; };
zone "27.172.in-addr.arpa"  { type master; file "/etc/bind/db.empty"; };
zone "28.172.in-addr.arpa"  { type master; file "/etc/bind/db.empty"; };
zone "29.172.in-addr.arpa"  { type master; file "/etc/bind/db.empty"; };
zone "30.172.in-addr.arpa"  { type master; file "/etc/bind/db.empty"; };
zone "31.172.in-addr.arpa"  { type master; file "/etc/bind/db.empty"; };

zone "168.192.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };

# mydomain.eu domain zone
zone "mydomain.eu" {
        type master;
        file "/etc/bind/zones/mydomain.eu.db";
};

# reverse mydomain.eu
zone "0.10.10.10.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.0.10.10.10.in-addr.arpa";
};
```mydomain.eu.db:
```
$TTL  604800
@       IN      SOA     solis.mydomain.eu.      root.mydomain.eu. (
        5
        28800
        3600
        604800
        38400
);
@       IN      NS      solis.mydomain.eu.
solis   IN      A       10.10.10.1
gw      IN      CNAME   solis
ns      IN      CNAME   solis
```rev.0.10.10.10.in-addr.arpa:
```
$TTL 604800
@       IN      SOA     solis.mydomain.eu.      root.mydomain.eu. (
        04
        28800
        604800
        604800
        86400
);
@       IN      NS      solis.mydomain.eu.
1       IN      PTR     solis.mydomain.eu.
```Of course my dream is to have access to solis from local network using name 'mydomain.eu' but not fully name 'solis.mydomain.eu'. I think I missed some entry in DNS config but I do not know what:) Could you please help?
Thanks in advance and regrads, Dawid.

---

### Post by Wayne_V on 2011-08-23
you would need an "A" record for mydomain.eu as well.   then just add a "CNAME" record for solis to point to mydomain.eu

---

### Post by kalosh on 2011-08-23
Thanks for reply.
I have been trying the following:
mydomain.eu.db:
```
$TTL  604800
@       IN      SOA     solis.mydomain.eu.      root.mydomain.eu. (
        5
        28800
        3600
        604800
        38400
);
@       IN      NS      solis.mydomain.eu.
mydomain.eu    IN      A       10.10.10.1
solis   IN      CNAME   solis
gw      IN      CNAME   solis
ns      IN      CNAME   solis
```
and the result was:
```
kalosh@solis:~$ nslookup mydomain.eu
Server:         10.10.10.1
Address:        10.10.10.1#53

** server can't find mydomain.eu.mydomain.eu: SERVFAIL
```

---

### Post by SeijiSensei on 2011-08-23
Try this instead:

```
$TTL  604800
@       IN      SOA     solis.mydomain.eu.      root.mydomain.eu. (
        5
        28800
        3600
        604800
        38400
);
        IN      NS      solis.mydomain.eu.
        IN      A       10.10.10.1

solis   IN      A       10.10.10.1
gw      IN      CNAME   solis
ns      IN      CNAME   solis
```

Both the NS and A declarations refer to "@", which represents "mydomain.eu".  Also you have solis as a CNAME to itself; you need an A record as I entered above.  So you now have an A record for "mydomain.eu" and another A record for "solis.mydomain.eu".

---

### Post by kalosh on 2011-08-23
Thanks Selji:) The @ was that I needed.
Thanks for your help.

---

### Post by SeijiSensei on 2011-08-24
You're welcome.  Please mark the thread as SOLVED.

---

