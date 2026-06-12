---
title: "Problem Configuring DNS"
date: 2012-07-27
forum: Server Platforms
---

### Post by cybercity@localhost on 2012-07-27
i am having the same issue. named -p 53 -g outputs...
```

27-Jul-2012 20:36:08.033 starting BIND 9.7.3 -p 53 -g
27-Jul-2012 20:36:08.033 built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-dlz-postgres=no' '--with-dlz-mysql=no' '--with-dlz-bdb=yes' '--with-dlz-filesystem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS='
27-Jul-2012 20:36:08.033 found 2 CPUs, using 2 worker threads
27-Jul-2012 20:36:08.033 using up to 4096 sockets
27-Jul-2012 20:36:08.039 loading configuration from '/etc/bind/named.conf'
27-Jul-2012 20:36:08.039 reading built-in trusted keys from file '/etc/bind/bind.keys'
27-Jul-2012 20:36:08.040 using default UDP/IPv4 port range: [1024, 65535]
27-Jul-2012 20:36:08.040 using default UDP/IPv6 port range: [1024, 65535]
27-Jul-2012 20:36:08.042 listening on IPv6 interfaces, port 53
27-Jul-2012 20:36:08.042 could not listen on UDP socket: permission denied
27-Jul-2012 20:36:08.042 listening on all IPv6 interfaces failed
27-Jul-2012 20:36:08.042 listening on IPv4 interface lo, 127.0.0.1#53
27-Jul-2012 20:36:08.042 could not listen on UDP socket: permission denied
27-Jul-2012 20:36:08.043 creating IPv4 interface lo failed; interface ignored
27-Jul-2012 20:36:08.043 listening on IPv4 interface eth0, 10.16.73.65#53
27-Jul-2012 20:36:08.043 could not listen on UDP socket: permission denied
27-Jul-2012 20:36:08.043 creating IPv4 interface eth0 failed; interface ignored
27-Jul-2012 20:36:08.043 listening on IPv4 interface ppp0, 111.92.130.233#53
27-Jul-2012 20:36:08.043 could not listen on UDP socket: permission denied
27-Jul-2012 20:36:08.043 creating IPv4 interface ppp0 failed; interface ignored
27-Jul-2012 20:36:08.043 not listening on any interfaces
27-Jul-2012 20:36:08.043 could not open file '/var/run/named/named.pid': Permission denied
27-Jul-2012 20:36:08.043 unlink '/var/run/named/named.pid': failed
27-Jul-2012 20:36:08.043 generating session key for dynamic DNS
27-Jul-2012 20:36:08.043 could not open file '/var/run/named/session.key': Permission denied
27-Jul-2012 20:36:08.043 could not create /var/run/named/session.key
27-Jul-2012 20:36:08.043 failed to generate session key for dynamic DNS: permission denied
27-Jul-2012 20:36:08.046 set up managed keys zone for view _default, file 'managed-keys.bind'
27-Jul-2012 20:36:08.046 automatic empty zone: 254.169.IN-ADDR.ARPA
27-Jul-2012 20:36:08.046 automatic empty zone: 2.0.192.IN-ADDR.ARPA
27-Jul-2012 20:36:08.046 automatic empty zone: 100.51.198.IN-ADDR.ARPA
27-Jul-2012 20:36:08.046 automatic empty zone: 113.0.203.IN-ADDR.ARPA
27-Jul-2012 20:36:08.046 automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
27-Jul-2012 20:36:08.046 automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
27-Jul-2012 20:36:08.046 automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
27-Jul-2012 20:36:08.046 automatic empty zone: D.F.IP6.ARPA
27-Jul-2012 20:36:08.046 automatic empty zone: 8.E.F.IP6.ARPA
27-Jul-2012 20:36:08.046 automatic empty zone: 9.E.F.IP6.ARPA
27-Jul-2012 20:36:08.046 automatic empty zone: A.E.F.IP6.ARPA
27-Jul-2012 20:36:08.046 automatic empty zone: B.E.F.IP6.ARPA
27-Jul-2012 20:36:08.046 automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA
27-Jul-2012 20:36:08.049 /etc/bind/named.conf:15: couldn't add command channel 127.0.0.1#953: permission denied
27-Jul-2012 20:36:08.049 the working directory is not writable
27-Jul-2012 20:36:08.049 ignoring config file logging statement due to -g option
27-Jul-2012 20:36:08.049 listening on IPv6 interfaces, port 53
27-Jul-2012 20:36:08.049 could not listen on UDP socket: permission denied
27-Jul-2012 20:36:08.049 listening on all IPv6 interfaces failed
27-Jul-2012 20:36:08.049 additionally listening on IPv4 interface lo, 127.0.0.1#53
27-Jul-2012 20:36:08.049 could not listen on UDP socket: permission denied
27-Jul-2012 20:36:08.049 creating IPv4 interface lo failed; interface ignored
27-Jul-2012 20:36:08.049 additionally listening on IPv4 interface eth0, 10.16.73.65#53
27-Jul-2012 20:36:08.049 could not listen on UDP socket: permission denied
27-Jul-2012 20:36:08.049 creating IPv4 interface eth0 failed; interface ignored
27-Jul-2012 20:36:08.049 additionally listening on IPv4 interface ppp0, 111.92.130.233#53
27-Jul-2012 20:36:08.049 could not listen on UDP socket: permission denied
27-Jul-2012 20:36:08.050 creating IPv4 interface ppp0 failed; interface ignored
27-Jul-2012 20:36:08.050 zone 0.in-addr.arpa/IN: loaded serial 1
27-Jul-2012 20:36:08.050 zone 73.16.10.in-addr.arpa/IN: loaded serial 2007011502
27-Jul-2012 20:36:08.051 zone 127.in-addr.arpa/IN: loaded serial 1
27-Jul-2012 20:36:08.051 zone 255.in-addr.arpa/IN: loaded serial 1
27-Jul-2012 20:36:08.053 zone cybercity.com/IN: loaded serial 1340049979
27-Jul-2012 20:36:08.053 zone qambrani.com/IN: loaded serial 1340120328
27-Jul-2012 20:36:08.053 zone localhost/IN: loaded serial 2
27-Jul-2012 20:36:08.054 managed-keys-zone ./IN: loaded serial 0
27-Jul-2012 20:36:08.055 zone 73.16.10.in-addr.arpa/IN: sending notifies (serial 2007011502)
27-Jul-2012 20:36:08.055 running

```

can anybody tell me what is the solution for this?

---

### Post by cariboo on 2012-07-27
Moved to a thread of it's own, as server setup has changed quite a bit in the two years since the thread this was originally in was created.

**A Note to the OP**: adding a post to a solved thread will almost guarantee that it will be ignored.

---

### Post by papibe on 2012-07-28
Hi cybercity@localhost.

At first glance looks like you're trying yo start bind as a regular user, thus it has no permissions to create any required file (like var/run/named/named.pid or /var/run/named/session.key).

Try staring bind using sudo:
```
sudo service bin9 start 
```
Let us know how it goes.
Regards.

---

