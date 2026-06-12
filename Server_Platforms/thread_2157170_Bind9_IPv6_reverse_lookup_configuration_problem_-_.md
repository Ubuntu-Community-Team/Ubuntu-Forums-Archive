---
title: "Bind9 IPv6 reverse lookup configuration problem - fixed"
date: 2013-06-24
forum: Server Platforms
---

### Post by jeajea on 2013-06-24
My home network has two physical networks (LAN1 and LAN2) connected to a Zyxel USG50 router. The USG50 connects to the Internet via a cable modem. For IPv6 I use a Hurricane Electric IPv6-in-IPv4 tunnel and have a routed /48. The USG 50 handles the tunnel, DHCP and DHCPv6 for each network, and IPv4 routing to the internet and between the networks. I have assigned a different /64 subnet of my /48 to each network. Hosts have either static or reserved (by MAC address in the USG) IPv4 addresses. At this time only the USG50 and my DNS server have static IPv6 addresses. All other hosts (that are dual stack) get there address via DHCPv6 from the USG50. The USG50 doesn’t support IPv6 reservations. The server is running Ubuntu 13.04 32 bit on an Athlon II x2 with 8GB memory and a 64GB SSD. The servers FQDN is 2ns1.home.test.

Some of my hosts have two NICs and are connected to both subnets (two different IP addresses. I have created two acls (lan1 and lan2) and two views (lan1 and lan2) so that bind will provide the correct IP address for these hosts based on the requesters subnet. The DNS server is only connected to LAN1 and has only 1 static IPv6 address and 1 static IPv4 address. 

Both views are working for IPv4 and IPv6 local and global (by forwarder) name requests and IPv4 reverse lookups. However, IPv6 reverse lookup fails for the DNS server (the only entry in the zone1/lan1 IPv6 reverse zone file and the only AAAA entry in the forward zone).

This is the first time I have used views and the first time I have setup DNS for both IPv6 and Ipv4 so my educated guess is I have one or more errors in the IPv6 reverse zone file.

I used this guide and Google to get to this point

[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

Prior to creating the files from scratch I tried using Gadmin-bind but the zones it created didn’t work and I didn’t know how to fix them. The IPv6 reverse files that I am using were created by Gadmin-bind and the edited by me to make the header look more like the IPv4 reverse files.

Named.conf

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
// include "/etc/bind/named.conf.default-zones";




```

named.conf.options


```
options {
        directory "/var/cache/bind";
        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)
        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.
forwarders {
        2001:470:20::2;
        2001:4860:4860::8844;
        65.32.5.111;
        65.32.5.112;
 };
        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See [https://www.isc.org/bind-keys](https://www.isc.org/bind-keys)
        //========================================================================
        dnssec-enable no;
        dnssec-validation no;
        auth-nxdomain no;    # conform to RFC1035
        recursion yes;
        allow-query { any; };
        listen-on-v6 { any; };
};
 


```

named.conf.local

```
//
// Do any local configuration here
//
acl "lan1" {
        2001:470:bddf:1::/64;
        192.168.1.0/24;
        192.168.17.0/24;
        127.0.0.1;
        127.0.0.0/8;
};
acl "lan2" {
        2001:470:bddf:2::/64;
        172.30.30.0/24;
        172.20.20.0/24;
};
view "lan1" {
        match-clients { lan1; };
        recursion yes;
        include "/etc/bind/named.conf.default-zones";
zone "1.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/db.192";
};
zone "30.30.172.in-addr.arpa" {
        type master;
        file "/etc/bind/db.172";
};
zone "1.0.0.0.f.d.d.b.0.7.4.0.1.0.0.2.ip6.arpa" {
        type master;
        file "/etc/bind/reverse.zone1.ipv6";
};
zone "2.0.0.0.f.d.d.b.0.7.4.0.1.0.0.2.ip6.arpa" {
        type master;
        file "/etc/bind/reverse.zone2.ipv6";
};
        zone "home.test" {
                type master;
                file "/etc/bind/lan1/db.home.test";
        };
};
view "lan2" {
        match-clients { lan2; };
        recursion yes;
        allow-query { any; };
        include "/etc/bind/named.conf.default-zones";
zone "1.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/db.192";
};
zone "30.30.172.in-addr.arpa" {
        type master;
        file "/etc/bind/db.172";
};
zone "1.0.0.0.f.d.d.b.0.7.4.0.1.0.0.2.ip6.arpa" {
        type master;
        file "/etc/bind/reverse.zone1.ipv6";
};
zone "2.0.0.0.f.d.d.b.0.7.4.0.1.0.0.2.ip6.arpa" {
        type master;
        file "/etc/bind/reverse.zone2.ipv6";
};
        zone "home.test" {
                type master;
                file "/etc/bind/lan2/db.home.test";
        };
};
// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";


```

cat reverse.zone1.ipv6

```
;
; Reverse zone1 IPv6->DNS
;
$TTL 3D
@       IN      SOA     2ns1.home.test. hostmaster.home.test. (
                        2013062304      ; Serial
                        8H              ; Refresh
                        2H              ; Retry
                        1W              ; Expire
                        1D )            ; Negative Cache TTL
@       IN      NS      2ns1.
7.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.1.0.0.0.f.d.d.b.0.7.4.0.1.0.0.2 IN      PTR    2ns1.home.test.



```

---

### Post by lemming465 on 2013-06-24
You don't have a $ORIGIN directive in your reverse.zone1.ipv6 file; I can't remember if those are still used.  I'm wondering if the default origin for the file is the zone rather than the root.  If so, the PTR record would need to be relative to the zone rather than absolute, e.g.

7.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0 IN      PTR    2ns1.home.test.

What happens if you try that?

---

### Post by jeajea on 2013-06-24
:D:DI fixed it - it was the IPv6 reverse zone file
gadmin-bind is broken:(:(
The $ORIGIN apparently is required
It is also a little easier to read
```

cat reverse.zone1.ipv6
;
; Reverse zone1 IPv6->DNS
;
$TTL 3D
$ORIGIN 1.0.0.0.f.d.d.b.0.7.4.0.1.0.0.2.ip6.arpa.
@       IN      SOA     2ns1.home.test. hostmaster.home.test. (
                        2013062306      ; Serial
                        8H              ; Refresh
                        2H              ; Retry
                        1W              ; Expire
                        1D )            ; Negative Cache TTL
;
@       IN      NS      2ns1.
7.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0 IN      PTR     2ns1.home.test.
;
 

```

---

