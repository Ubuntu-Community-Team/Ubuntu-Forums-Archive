---
title: "Bind &amp; DHCP - wrong Reverse Address?"
date: 2016-05-28
forum: Server Platforms
---

### Post by clemens2408 on 2016-05-28
Hi Ubuntu Specialists,
i have the following error in my isc-dhcp-logfile:

```

May 28 22:23:53 dhcp01 dhcpd: Added new forward map from cknb.mydomain.home to 10.0.0.100
May 28 22:23:53 dhcp01 dhcpd: Added reverse map from 100.0.0.10.0.0.10.in-addr.arpa to cknb.mydomain.home

```
i dont get it, why isc-dhcp is assigning 100.0.0.10.0.0.10.in-addr.arpa to the host... :(
It should assign 100.0.0.10.in-addr.arpa :(

my dhcp-config is:

```

authoritative;
default-lease-time 86400;
max-lease-time 86400;
log-facility local7;

ddns-update-style interim;
ddns-updates on;
update-static-leases on;

key rndc-key { algorithm hmac-md5; secret ABC==;}
allow unknown-clients;
use-host-decl-names on;

server-name                 dhcp01;

subnet 10.0.0.0 netmask 255.255.255.0 {
   range                        10.0.0.100 10.0.0.250;

   ddns-domainname              "mydomain.home";
   ddns-rev-domainname          "0.0.10.in-addr.arpa";
   ddns-ttl                     86400;
   option domain-name           "mydomain.home";
   option domain-search         "mydomain.home";

   option subnet-mask           255.255.255.0;

   option domain-name-servers   10.0.0.254;

   option ntp-servers           10.0.0.10;
   option log-servers           10.0.0.11;

   option routers               10.0.0.254;


zone mydomain.home. {
    primary 10.0.0.14;
    key rndc-key;
}

zone 0.0.10.in-addr.arpa. {
    primary 10.0.0.14;
    key rndc-key;
}


}

```
the named.conf.local file looks like this:


```

key "rndc-key" {
        algorithm hmac-md5;
        secret "ABC==";
};

zone "mydomain.home" {
    type master;
    file "/var/lib/bind/mydomain.home.hosts";
    allow-update { key rndc-key; };
};

zone "0.0.10.in-addr.arpa" {
    type master;
    file "/var/lib/bind/10.0.0.rev";
    allow-update { key rndc-key; };
};

```


the forward-zone:

```

;; mydomain.home.hosts
;; Forwardlookupzone für mydomain.home
;;
$TTL 2D
@       IN      SOA     dns01.mydomain.home. dns.mydomain.home. (
                        2006032201      ; Serial
                                8H      ; Refresh
                                2H      ; Retry
                                4W      ; Expire
                                3H )    ; NX (TTL Negativ Cache)

@                               IN      NS      dns01.mydomain.home.
                                IN      A       10.0.0.14

```
the reverse zone:

```

;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     dns01.mydomain.home. dns.mydomain.home. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      dns01.mydomain.home.

```

Im Trying to fix this issue since hours... but without any success...

Regards
Clem

---

### Post by darkod on 2016-05-28
I don't know if it's related to this, but you have errors in both forward and reverse zone files.

The line @ IN SOA format is like:
```
@   IN   SOA   domain.com.   admin.domain.com. (
```

Instead of domain.com in that line you have put the fqdn of your nameserver. You don't put the nameserver there, you put only the domain.

Also later in the forward zone file, you will need a record for dns01, like:
```
dns01   IN   A   10.0.0.14
```

Why in the dhcp config you are sending option DNS 10.0.0.254 and option router the same IP? Is that the router?

If you are intending to use your own DNS server you have to assign its IP in the dhcp, not the router's. Otherwise the clients will ignore your DNS server and use the router as DNS.

---

### Post by darkod on 2016-05-28
Correction... I just consulted the documentation and actually in the reverse zone the:
```
@   IN   SOA   dns01.mydomain.home. dns.mydomain.home. (
```

is correct. But later in the file you don't repeat the:
```
@   IN   NS   dns01.mydomain.home.
```

Review the documentation and modify your zone files. Then try again.
[https://help.ubuntu.com/lts/serverguide/dns-configuration.html](https://help.ubuntu.com/lts/serverguide/dns-configuration.html)

Basically in the reverse zone it will look something like:
```
@   IN   NS   dns01.
14   IN   PTR   dns01.mydomain.home.
```

---

### Post by clemens2408 on 2016-05-28
Hi, thankx for your quick reply.
applied your changes but the problem still exists :sad:


changed my forward-zone:

```
;; mydomain.home.hosts
;; Forwardlookupzone für mydomain.home
;;
$TTL 2D
@       IN      SOA     mydomain.home. dns.mydomain.home. (
                        2006032201      ; Serial
                                8H      ; Refresh
                                2H      ; Retry
                                4W      ; Expire
                                3H )    ; NX (TTL Negativ Cache)

@                               IN      NS      dns01.mydomain.home.
                                IN      A       10.0.0.14


dhcp01                          IN      A       10.0.0.13
dns01                           IN      A       10.0.0.14

```

changed my reverse-zone:

```
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     dns01.mydomain.home. dns.mydomain.home. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      dns01.
;
13      IN      PTR     dhcp01.mydomain.home.
14      IN      PTR     dns01.mydomain.home.



```
changed my dhcpd.config

```

...
subnet 10.0.0.0 netmask 255.255.255.0 {
   range                        10.0.0.100 10.0.0.250;

   ddns-domainname              "mydomain.home";
   ddns-rev-domainname          "0.0.10.in-addr.arpa";
   ddns-ttl                     86400;
   option domain-name           "mydomain.home";
   option domain-search         "mydomain.home";

   option subnet-mask           255.255.255.0;

   option domain-name-servers   10.0.0.14;

   option ntp-servers           10.0.0.10;
   option log-servers           10.0.0.11;

   option routers               10.0.0.254;

}
...

```
dhcp-log:

```
May 28 23:19:06 dhcp01 dhcpd: DHCPREQUEST for 10.0.0.100 from 14:10:9f:f3:6e:2e via eth0
May 28 23:19:06 dhcp01 dhcpd: DHCPACK on 10.0.0.100 to 14:10:9f:f3:6e:2e (cknb) via eth0
May 28 23:19:06 dhcp01 dhcpd: Added new forward map from cknb.mydomain.home to 10.0.0.100
May 28 23:19:06 dhcp01 dhcpd: Added reverse map from 100.0.0.10.0.0.10.in-addr.arpa to cknb.mydomain.home
```

bind log:

```
May 28 23:19:06 dns01 named[4441]: client 10.0.0.13#61905/key rndc-key: signer "rndc-key" approved
May 28 23:19:06 dns01 named[4441]: client 10.0.0.13#61905/key rndc-key:  updating zone 'mydomain.home/IN': adding an RR at 'cknb.mydomain.home' A
May 28 23:19:06 dns01 named[4441]: client 10.0.0.13#61905/key rndc-key:  updating zone 'mydomain.home/IN': adding an RR at 'cknb.mydomain.home'  TXT
May 28 23:19:06 dns01 named[4441]: zone mydomain.home/IN: sending notifies (serial 2006032202)
May 28 23:19:06 dns01 named[4441]: client 10.0.0.13#61905/key rndc-key: signer "rndc-key" approved
May 28 23:19:06 dns01 named[4441]: client 10.0.0.13#61905/key rndc-key:  updating zone '0.0.10.in-addr.arpa/IN': deleting rrset at  '100.0.0.10.0.0.10.in-addr.arpa' PTR
May 28 23:19:06 dns01 named[4441]: client 10.0.0.13#61905/key rndc-key:  updating zone '0.0.10.in-addr.arpa/IN': adding an RR at  '100.0.0.10.0.0.10.in-addr.arpa' PTR
May 28 23:19:06 dns01 named[4441]: zone 0.0.10.in-addr.arpa/IN: sending notifies (serial 3)

```


Regards
Clem

---

### Post by darkod on 2016-05-28
Hmmm, I haven't used dhcp a lot, but I think the setting ddns-rev-domainname is doing the damage. The setting is called reverse domain name but you put the whole reverse IP, not just domain. Try commenting out that line, and restart both dhcp and bind service. You restarted bind after doing the zone modifications right?

After restarting dhcp and bind, you will also need to renew the dhcp lease from the client side, so that it gets a new lease with the new options.

Try that...

PS. According to this, don't disable the whole ddns-rev-domainname setting, instead just delete the numbers. Leave just the text because the dhcp knows to add the correct numbers from the IPs.
[http://www.unix.com/ip-networking/150551-ddns-rev-domainname-being-created-wrong.html](http://www.unix.com/ip-networking/150551-ddns-rev-domainname-being-created-wrong.html)

---

### Post by clemens2408 on 2016-05-29
Thanx a lot!
The following setting in dhcpd.conf did the trick:

ddns-rev-domainname          "in-addr.arpa";

---

