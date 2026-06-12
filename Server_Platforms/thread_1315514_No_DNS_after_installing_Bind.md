---
title: "No DNS after installing Bind"
date: 2009-11-05
forum: Server Platforms
---

### Post by TheForumTroll on 2009-11-05
I have just installed Bind9 on Karmic server for a caching dns server from the repo and now for some reason I cannot get dns to work on the server at all. I have no idea why so I'm hoping someone can point me in the right direction. Even if i dig another external nameserver i get a *"connection timed out; no servers could be reached"* message. Pinging IPs internal and external works fine and everything else on the network has access to dns (from the router).

Here's what I have tried so far:
[LIST]
[*] Telnet to the server on port 53 works fine
[*] All bind config files shows no errors
[*] Ping from server to google does not work
[*] Ping from server to google IP works
[*] Dig cannot connect to any servers
[*] Removing the servers IP from resolv.conf and using another dns server doesn't work
[*] Restarting the server and the network does not help
[/LIST]

All I have changed is /etc/bind/named.conf.options
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
                193.162.153.164;
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```
The DNS in the file is the same as the router uses. I have tried a few other servers too with no luck.

Any ideas? :confused:

---

### Post by TheForumTroll on 2009-11-05
I forgot the logs. Here is from syslog:


```

Nov  5 15:49:33 server named[4234]: starting BIND 9.6.1-P1 -u bind
Nov  5 15:49:33 server named[4234]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-dlz-postgres=no' '--with-dlz-mysql=no' '--with-dlz-bdb=yes' '--with-dlz-filesystem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CXXFLAGS=-g -O2' 'FFLAGS=-g -O2'
Nov  5 15:49:33 server named[4234]: adjusted limit on open files from 1024 to 1048576
Nov  5 15:49:33 server named[4234]: found 4 CPUs, using 4 worker threads
Nov  5 15:49:33 server named[4234]: using up to 4096 sockets
Nov  5 15:49:33 server named[4234]: loading configuration from '/etc/bind/named.conf'
Nov  5 15:49:33 server named[4234]: using default UDP/IPv4 port range: [1024, 65535]
Nov  5 15:49:33 server named[4234]: using default UDP/IPv6 port range: [1024, 65535]
Nov  5 15:49:33 server named[4234]: listening on IPv6 interfaces, port 53
Nov  5 15:49:33 server named[4234]: listening on IPv4 interface lo, 127.0.0.1#53
Nov  5 15:49:33 server named[4234]: listening on IPv4 interface eth0, 192.168.0.100#53
Nov  5 15:49:33 server named[4234]: listening on IPv4 interface eth1, 192.168.0.253#53
Nov  5 15:49:33 server named[4234]: automatic empty zone: 254.169.IN-ADDR.ARPA
Nov  5 15:49:33 server named[4234]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Nov  5 15:49:33 server named[4234]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Nov  5 15:49:33 server named[4234]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Nov  5 15:49:33 server named[4234]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Nov  5 15:49:33 server named[4234]: automatic empty zone: D.F.IP6.ARPA
Nov  5 15:49:33 server named[4234]: automatic empty zone: 8.E.F.IP6.ARPA
Nov  5 15:49:33 server named[4234]: automatic empty zone: 9.E.F.IP6.ARPA
Nov  5 15:49:33 server named[4234]: automatic empty zone: A.E.F.IP6.ARPA
Nov  5 15:49:33 server named[4234]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Nov  5 15:49:33 server named[4234]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Nov  5 15:49:33 server named[4234]: automatic empty zone: D.F.IP6.ARPA
Nov  5 15:49:33 server named[4234]: automatic empty zone: 8.E.F.IP6.ARPA
Nov  5 15:49:33 server named[4234]: automatic empty zone: 9.E.F.IP6.ARPA
Nov  5 15:49:33 server named[4234]: automatic empty zone: A.E.F.IP6.ARPA
Nov  5 15:49:33 server named[4234]: automatic empty zone: B.E.F.IP6.ARPA
Nov  5 15:49:33 server named[4234]: command channel listening on 127.0.0.1#953
Nov  5 15:49:33 server named[4234]: command channel listening on ::1#953
Nov  5 15:49:33 server named[4234]: zone 0.in-addr.arpa/IN: loaded serial 1
Nov  5 15:49:33 server named[4234]: zone 127.in-addr.arpa/IN: loaded serial 1
Nov  5 15:49:33 server named[4234]: zone 255.in-addr.arpa/IN: loaded serial 1
Nov  5 15:49:33 server named[4234]: zone localhost/IN: loaded serial 2
Nov  5 15:49:33 server named[4234]: running
Nov  5 15:49:37 server named[4234]: received control channel command 'reconfig'
Nov  5 15:49:37 server named[4234]: loading configuration from '/etc/bind/named.conf'
Nov  5 15:49:37 server named[4234]: using default UDP/IPv4 port range: [1024, 65535]
Nov  5 15:49:37 server named[4234]: using default UDP/IPv6 port range: [1024, 65535]
Nov  5 15:49:37 server named[4234]: reloading configuration succeeded
Nov  5 15:49:37 server named[4234]: any newly configured zones are now loaded
Nov  5 15:49:37 server dhclient: receive_packet failed on eth0: Network is down
Nov  5 15:49:37 server kernel: [21945.137124] r8169: eth0: link up
Nov  5 15:49:37 server named[4234]: received control channel command 'reconfig'
Nov  5 15:49:37 server named[4234]: loading configuration from '/etc/bind/named.conf'
Nov  5 15:49:37 server named[4234]: using default UDP/IPv4 port range: [1024, 65535]
Nov  5 15:49:37 server named[4234]: using default UDP/IPv6 port range: [1024, 65535]
Nov  5 15:49:37 server named[4234]: reloading configuration succeeded
Nov  5 15:49:37 server named[4234]: any newly configured zones are now loaded
Nov  5 15:49:48 server kernel: [21955.750018] eth0: no IPv6 routers present
Nov  5 15:50:58 server ntpdate[4296]: name server cannot be used, reason: Temporary failure in name resolution





```

---

### Post by TheForumTroll on 2009-11-05
Well purging bind and reinstalling seems to have fixed it for some reason :confused:

---

