---
title: "bind9 at boot time"
date: 2010-04-02
forum: Server Platforms
---

### Post by radubcrisan on 2010-04-02
Hi,

I have installed and configured bind9 and when it's booting up the following error is shown in logs. I have bolded the error lines.

```
Apr  2 10:56:05 ns named[886]: starting BIND 9.6.1-P2 -u bind -t /var/lib/named
Apr  2 10:56:05 ns named[886]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-dlz-postgres=no' '--with-dlz-mysql=no' '--with-dlz-bdb=yes' '--with-dlz-filesystem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CXXFLAGS=-g -O2' 'FFLAGS=-g -O2'
Apr  2 10:56:05 ns named[886]: adjusted limit on open files from 1024 to 1048576
Apr  2 10:56:05 ns named[886]: found 1 CPU, using 1 worker thread
Apr  2 10:56:05 ns named[886]: using up to 4096 sockets
Apr  2 10:56:05 ns named[886]: loading configuration from '/etc/bind/named.conf'
Apr  2 10:56:05 ns named[886]: using default UDP/IPv4 port range: [1024, 65535]
Apr  2 10:56:05 ns named[886]: using default UDP/IPv6 port range: [1024, 65535]
Apr  2 10:56:05 ns named[886]: listening on IPv6 interfaces, port 53
Apr  2 10:56:05 ns named[886]: listening on IPv4 interface lo, 127.0.0.1#53
Apr  2 10:56:05 ns named[886]: listening on IPv4 interface eth4, 192.168.0.8#53
Apr  2 10:56:05 ns named[886]: automatic empty zone: 254.169.IN-ADDR.ARPA
Apr  2 10:56:05 ns named[886]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Apr  2 10:56:05 ns named[886]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Apr  2 10:56:05 ns named[886]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Apr  2 10:56:05 ns named[886]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Apr  2 10:56:05 ns named[886]: automatic empty zone: D.F.IP6.ARPA
Apr  2 10:56:05 ns named[886]: automatic empty zone: 8.E.F.IP6.ARPA
Apr  2 10:56:05 ns named[886]: automatic empty zone: 9.E.F.IP6.ARPA
Apr  2 10:56:05 ns named[886]: automatic empty zone: A.E.F.IP6.ARPA
Apr  2 10:56:05 ns named[886]: automatic empty zone: B.E.F.IP6.ARPA
Apr  2 10:56:05 ns named[886]: command channel listening on 127.0.0.1#953
Apr  2 10:56:05 ns named[886]: command channel listening on ::1#953
Apr  2 10:56:06 ns named[886]: zone 0.in-addr.arpa/IN: loaded serial 1
Apr  2 10:56:06 ns named[886]: zone 127.in-addr.arpa/IN: loaded serial 1
Apr  2 10:56:06 ns named[886]: zone 0.168.192.in-addr.arpa/IN: loading from master file /var/lib/bind/192.168.0.rev failed: file not found
Apr  2 10:56:06 ns named[886]: zone 255.in-addr.arpa/IN: loaded serial 1
Apr  2 10:56:06 ns named[886]: zone localhost/IN: loaded serial 2
**Apr  2 10:56:06 ns named[886]: zone domain1.com/IN: loading from master file /var/lib/bind/domain1.com.hosts failed: file not found**
**Apr  2 10:56:06 ns named[886]: zone domain2.com/IN: loading from master file /var/lib/bind/domain2.com.hosts failed: file not found**
Apr  2 10:56:06 ns named[886]: running
```

Interesting bind9 shown as not started, when I start it manually it says:

```
Apr  2 11:02:07 ns named[1586]: starting BIND 9.6.1-P2 -c /etc/bind/named.conf
Apr  2 11:02:07 ns named[1586]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-dlz-postgres=no' '--with-dlz-mysql=no' '--with-dlz-bdb=yes' '--with-dlz-filesystem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CXXFLAGS=-g -O2' 'FFLAGS=-g -O2'
Apr  2 11:02:07 ns named[1586]: adjusted limit on open files from 1024 to 1048576
Apr  2 11:02:07 ns named[1586]: found 1 CPU, using 1 worker thread
Apr  2 11:02:07 ns named[1586]: using up to 4096 sockets
Apr  2 11:02:07 ns named[1586]: loading configuration from '/etc/bind/named.conf'
Apr  2 11:02:07 ns named[1586]: using default UDP/IPv4 port range: [1024, 65535]
Apr  2 11:02:07 ns named[1586]: using default UDP/IPv6 port range: [1024, 65535]
Apr  2 11:02:07 ns named[1586]: listening on IPv6 interfaces, port 53
Apr  2 11:02:07 ns named[1586]: binding TCP socket: address in use
Apr  2 11:02:07 ns named[1586]: listening on IPv4 interface lo, 127.0.0.1#53
Apr  2 11:02:07 ns named[1586]: binding TCP socket: address in use
Apr  2 11:02:07 ns named[1586]: listening on IPv4 interface eth4, 192.168.0.8#53
Apr  2 11:02:07 ns named[1586]: binding TCP socket: address in use
Apr  2 11:02:07 ns named[1586]: automatic empty zone: 254.169.IN-ADDR.ARPA
Apr  2 11:02:07 ns named[1586]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Apr  2 11:02:07 ns named[1586]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Apr  2 11:02:07 ns named[1586]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Apr  2 11:02:07 ns named[1586]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Apr  2 11:02:07 ns named[1586]: automatic empty zone: D.F.IP6.ARPA
Apr  2 11:02:07 ns named[1586]: automatic empty zone: 8.E.F.IP6.ARPA
Apr  2 11:02:07 ns named[1586]: automatic empty zone: 9.E.F.IP6.ARPA
Apr  2 11:02:07 ns named[1586]: automatic empty zone: A.E.F.IP6.ARPA
Apr  2 11:02:07 ns named[1586]: automatic empty zone: B.E.F.IP6.ARPA
**Apr  2 11:02:07 ns named[1586]: none:0: open: /etc/bind/rndc.key: permission denied**
**Apr  2 11:02:07 ns named[1586]: couldn't add command channel 127.0.0.1#953: permission denied**
**Apr  2 11:02:07 ns named[1586]: none:0: open: /etc/bind/rndc.key: permission denied**
**Apr  2 11:02:07 ns named[1586]: couldn't add command channel ::1#953: permission denied**
Apr  2 11:02:07 ns named[1586]: zone 0.in-addr.arpa/IN: loaded serial 1
Apr  2 11:02:07 ns named[1586]: zone 127.in-addr.arpa/IN: loaded serial 1
Apr  2 11:02:07 ns named[1586]: zone 0.168.192.in-addr.arpa/IN: loaded serial 1270053515
Apr  2 11:02:07 ns named[1586]: zone 255.in-addr.arpa/IN: loaded serial 1
Apr  2 11:02:07 ns named[1586]: zone localhost/IN: loaded serial 2
Apr  2 11:02:07 ns named[1586]: zone domain1.com/IN: loaded serial 1269440203
Apr  2 11:02:07 ns named[1586]: zone domain2.com/IN: loaded serial 1269440738
Apr  2 11:02:07 ns named[1586]: running
Apr  2 11:02:07 ns named[1586]: zone domain1.com/IN: sending notifies (serial 1269440203)
Apr  2 11:02:07 ns named[1586]: zone domain2.com/IN: sending notifies (serial 1269440738)
Apr  2 11:02:07 ns named[1586]: client 82.77.xxx.xxx#50698: received notify for zone 'domain1.com'
Apr  2 11:02:07 ns named[1586]: client 82.77.xxx.xxx#35245: received notify for zone 'domain2.com'
```

I think this is not normal, what can I do to fix it?

---

### Post by Bachstelze on 2010-04-02
What are the permissions on this file? Here it gives

```
firas@itsuki ~ % ls -l /etc/bind/rndc.key 
-rw-r----- 1 bind bind 77 2010-03-06 05:42 /etc/bind/rndc.key
```

---

### Post by radubcrisan on 2010-04-02
Thanks for the replay. 

Here are the permissions:
```
root@ns:/home/ekk# ls -l /etc/bind/rndc.key
-rw-r----- 1 bind bind 77 2010-03-25 15:17 /etc/bind/rndc.key/
```

But the error 
```
Apr  2 11:02:07 ns named[1586]: none:0: open: /etc/bind/rndc.key: permission denied
Apr  2 11:02:07 ns named[1586]: couldn't add command channel 127.0.0.1#953: permission denied
Apr  2 11:02:07 ns named[1586]: none:0: open: /etc/bind/rndc.key: permission denied
Apr  2 11:02:07 ns named[1586]: couldn't add command channel ::1#953: permission denied
```

is happening only when I manually start bing9 after reboot, strange...

---

