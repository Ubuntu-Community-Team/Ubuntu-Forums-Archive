---
title: "Bind 9 rndc error"
date: 2010-04-07
forum: Server Platforms
---

### Post by fortune2008 on 2010-04-07
while setting up zones in bind9 i got this error restarting bind 

```
rndc: connect failed: 127.0.0.1#953: connection refused

```

Here is my daemon log 

```
Apr  7 18:00:31 server-1 named[1601]: starting BIND 9.6.1-P2 -u bind -t /var/lib/named
Apr  7 18:00:31 server-1 named[1601]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-dlz-postgres=no' '--with-dlz-mysql=no' '--with-dlz-bdb=yes' '--with-dlz-filesystem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CXXFLAGS=-g -O2' 'FFLAGS=-g -O2'
Apr  7 18:00:31 server-1 named[1601]: adjusted limit on open files from 1024 to 1048576
Apr  7 18:00:31 server-1 named[1601]: found 2 CPUs, using 2 worker threads
Apr  7 18:00:31 server-1 named[1601]: using up to 4096 sockets
Apr  7 18:00:31 server-1 named[1601]: loading configuration from '/etc/bind/named.conf'
Apr  7 18:00:31 server-1 named[1601]: /etc/bind/named.conf:5: open: /etc/rndc.key: file not found
Apr  7 18:00:31 server-1 named[1601]: loading configuration: file not found
Apr  7 18:00:31 server-1 named[1601]: exiting (due to fatal error)

```

---

