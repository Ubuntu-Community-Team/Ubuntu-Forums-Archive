---
title: "Ubuntu 12.04  Squid redirection 443(https) problem"
date: 2015-07-18
forum: Server Platforms
---

### Post by secoonder on 2015-07-18
Hello 

i am using ubuntu 12.04 firewall.&#305; install squid prxoy server and iptables firewall.
&#305; redirected 80 port to squid server.it is working properly.

When i redirected 443 port to squid, it is not working properly for 443 port.Why ?
how do i run it properly.

Thank you very much for your help

---

### Post by SeijiSensei on 2015-07-19
SSL has features that make proxying difficult.

[http://wiki.squid-cache.org/Features/SslBump](http://wiki.squid-cache.org/Features/SslBump)

---

### Post by andrew102 on 2015-07-21
However, you can use it to transparently to allow HTTPS without decrypting&encrypting the traffic itself.

You'll need these lines:
```

acl SSL_ports port 443
acl Safe_ports port 443		# https
acl CONNECT method CONNECT
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
```

---

