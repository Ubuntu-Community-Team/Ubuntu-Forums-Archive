---
title: "rndc reload failed - bad zoen"
date: 2012-02-06
forum: Server Platforms
---

### Post by lbayerlein on 2012-02-06
Hi there,

as i installed bind9 as service on my server, theres one problem. Everytime when i run the command, i get an error:
root@gosa:/#rndc reload test-domain.de
rndc: 'reload' failed: bad zone

I tried something and i googled, but i can't find any reason. The outpout of the command `named` tells me, that the address 127.0.0.1#953 is already in use. But is this the problem? I don't understand the reaseon of this fault. I post some configs:

root@gosa:/etc/bind# named -p 53 -g
06-Feb-2012 15:38:56.805 starting BIND 9.7.0-P1 -p 53 -g
06-Feb-2012 15:38:56.805 built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-dlz-postgres=no' '--with-dlz-mysql=no' '--with-dlz-bdb=yes' '--with-dlz-filesystem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS='
06-Feb-2012 15:38:56.805 adjusted limit on open files from 1024 to 1048576
06-Feb-2012 15:38:56.805 found 1 CPU, using 1 worker thread
06-Feb-2012 15:38:56.805 using up to 4096 sockets
06-Feb-2012 15:38:56.811 loading configuration from '/etc/bind/named.conf'
06-Feb-2012 15:38:56.811 reading built-in trusted keys from file '/etc/bind/bind.keys'
06-Feb-2012 15:38:56.812 using default UDP/IPv4 port range: [1024, 65535]
06-Feb-2012 15:38:56.812 using default UDP/IPv6 port range: [1024, 65535]
06-Feb-2012 15:38:56.814 listening on IPv6 interfaces, port 53
06-Feb-2012 15:38:56.815 binding TCP socket: address in use
06-Feb-2012 15:38:56.815 listening on IPv4 interface lo, 127.0.0.1#53
06-Feb-2012 15:38:56.815 binding TCP socket: address in use
06-Feb-2012 15:38:56.815 listening on IPv4 interface eth0, 192.168.0.183#53
06-Feb-2012 15:38:56.816 binding TCP socket: address in use
06-Feb-2012 15:38:56.816 generating session key for dynamic DNS
06-Feb-2012 15:38:56.819 automatic empty zone: 254.169.IN-ADDR.ARPA
06-Feb-2012 15:38:56.819 automatic empty zone: 2.0.192.IN-ADDR.ARPA
06-Feb-2012 15:38:56.819 automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
06-Feb-2012 15:38:56.819 automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
06-Feb-2012 15:38:56.819 automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
06-Feb-2012 15:38:56.819 automatic empty zone: D.F.IP6.ARPA
06-Feb-2012 15:38:56.819 automatic empty zone: 8.E.F.IP6.ARPA
06-Feb-2012 15:38:56.819 automatic empty zone: 9.E.F.IP6.ARPA
06-Feb-2012 15:38:56.819 automatic empty zone: A.E.F.IP6.ARPA
06-Feb-2012 15:38:56.819 automatic empty zone: B.E.F.IP6.ARPA
06-Feb-2012 15:38:56.823 /etc/bind/named.conf:19: couldn't add command channel 127.0.0.1#953: address in use
06-Feb-2012 15:38:56.823 ignoring config file logging statement due to -g option
06-Feb-2012 15:38:56.824 zone 0.in-addr.arpa/IN: loaded serial 1
06-Feb-2012 15:38:56.824 zone 127.in-addr.arpa/IN: loaded serial 1
06-Feb-2012 15:38:56.825 zone 0.168.192.in-addr.arpa/IN: NS '192.168.0.183.0.168.192.in-addr.arpa' has no address records (A or AAAA)
06-Feb-2012 15:38:56.825 zone 0.168.192.in-addr.arpa/IN: not loaded due to errors.
06-Feb-2012 15:38:56.825 zone 255.in-addr.arpa/IN: loaded serial 1
06-Feb-2012 15:38:56.827 zone test-domain.de/IN: NS '192.168.0.183.test-domain.de' has no address records (A or AAAA)
06-Feb-2012 15:38:56.827 zone test-domain.de/IN: not loaded due to errors.
06-Feb-2012 15:38:56.827 zone localhost/IN: loaded serial 2
06-Feb-2012 15:38:56.828 running
06-Feb-2012 15:39:57.358 no longer listening on ::#53
06-Feb-2012 15:39:57.358 no longer listening on 127.0.0.1#53
06-Feb-2012 15:39:57.358 no longer listening on 192.168.0.183#53
06-Feb-2012 15:39:57.365 exiting




/etc/bind/test-domain.de.

$TTL 300
@        IN    SOA    192.168.0.183 gosa.test-domain.de. (
                2012020210 ; Serialnumber
                3600    ; Refresh
                1800    ; Retry
                720000    ; Expire
                6400 )    ; Minimum TTL
            NS    192.168.0.183
            MX    20 mail.test-domain.de
tux07            A    192.168.0.17
ldap            A    192.168.0.183
gosa            A    192.168.0.183


/etc/bind/0.168.192.in-addr.arpa.
$TTL 300
@        IN    SOA    192.168.0.183 gosa.test-domain.de. (
                2012020210 ; Serialnumber
                3600    ; Refresh
                1800    ; Retry
                720000    ; Expire
                6400 )    ; Minimum TTL
            NS    192.168.0.183
            MX    20 mail.test-domain.de.
17            PTR    tux07.test-domain.de.
183            PTR    ldap.test-domain.de.
            PTR    gosa.test-domain.de.
3            PTR    mail.test-domain.de.

/etc/bind/named.conf
include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
#include "/etc/bind/named.conf.ldap2zone";

 key "rndc-key" {
       algorithm hmac-md5;
       secret "y2Tkhbr7i8V8A4UBm8ZBHA==";
 };
 controls {
       inet 127.0.0.1 port 953
               allow { 127.0.0.1; } keys { "rndc-key"; };
 };


/etc/named.conf.local
zone "test-domain.de" {
        type master;
        file "/etc/bind/test-domain.de.";
};

zone "0.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/0.168.192.in-addr.arpa.";
};


Ich hoffe ihr könnte mir weiterhelfen. Danke!

Gruß,
Ludwig

---

