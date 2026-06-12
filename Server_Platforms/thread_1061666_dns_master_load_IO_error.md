---
title: "dns_master_load: I/O error"
date: 2009-02-06
forum: Server Platforms
---

### Post by kylecorey on 2009-02-06
Hi I am getting this weird I/O error and have been unable to find a resoulution to it. Has any one seen this before??  I am sure it is not new under the sun. 
<code>named -g
05-Feb-2009 23:11:17.544 starting BIND 9.5.0-P2 -g
05-Feb-2009 23:11:17.545 found 1 CPU, using 1 worker thread
05-Feb-2009 23:11:17.549 loading configuration from '/etc/bind/named.conf'
05-Feb-2009 23:11:17.550 listening on IPv6 interfaces, port 53
05-Feb-2009 23:11:17.552 listening on IPv4 interface lo, 127.0.0.1#53
05-Feb-2009 23:11:17.553 listening on IPv4 interface eth0, 142.25.97.168#53
05-Feb-2009 23:11:17.557 default max-cache-size (33554432) applies
05-Feb-2009 23:11:17.560 automatic empty zone: 0.IN-ADDR.ARPA
05-Feb-2009 23:11:17.560 automatic empty zone: 127.IN-ADDR.ARPA
05-Feb-2009 23:11:17.560 automatic empty zone: 254.169.IN-ADDR.ARPA
05-Feb-2009 23:11:17.560 automatic empty zone: 2.0.192.IN-ADDR.ARPA
05-Feb-2009 23:11:17.561 automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
05-Feb-2009 23:11:17.561 automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.                         ARPA
05-Feb-2009 23:11:17.561 automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.                         ARPA
05-Feb-2009 23:11:17.561 automatic empty zone: D.F.IP6.ARPA
05-Feb-2009 23:11:17.562 automatic empty zone: 8.E.F.IP6.ARPA
05-Feb-2009 23:11:17.562 automatic empty zone: 9.E.F.IP6.ARPA
05-Feb-2009 23:11:17.562 automatic empty zone: A.E.F.IP6.ARPA
05-Feb-2009 23:11:17.562 automatic empty zone: B.E.F.IP6.ARPA
05-Feb-2009 23:11:17.564 default max-cache-size (33554432) applies: view _bind
05-Feb-2009 23:11:17.566 command channel listening on 127.0.0.1#953
05-Feb-2009 23:11:17.567 ignoring config file logging statement due to -g option
05-Feb-2009 23:11:17.568 dns_master_load: /etc/bind/zones/rev.kc.infotechnow.ca.in-addr.arpa:1: isc_lex_gettoken()                          failed: I/O error
05-Feb-2009 23:11:17.568 dns_master_load: /etc/bind/zones/rev.kc.infotechnow.ca.in-addr.arpa:1: I/O error
05-Feb-2009 23:11:17.569 zone 97.25.142.in-addr.arpa/IN: loading from master file /etc/bind/zones/rev.kc.infotechnow.ca.in-addr.arpa failed: I/O error
05-Feb-2009 23:11:17.571 dns_master_load: /etc/bind/zones/db.kc.infotechnow.ca:1: isc_lex_gettoken() failed: I/O error
05-Feb-2009 23:11:17.571 dns_master_load: /etc/bind/zones/db.kc.infotechnow.ca:1: I/O error
05-Feb-2009 23:11:17.571 zone kc.infotechnow.ca/IN: loading from master file /etc/bind/zones/db.kc.infotechnow.ca failed: I/O error
05-Feb-2009 23:11:17.573 running </code>

---

