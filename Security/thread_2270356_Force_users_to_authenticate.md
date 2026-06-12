---
title: "Force users to authenticate"
date: 2015-03-22
forum: Security
---

### Post by jjablonsky on 2015-03-22
I have set up an Ubuntu server as a firewall/gateway router following the article here:
[https://rbgeek.wordpress.com/2012/05/14/ubuntu-as-a-firewallgateway-router/](https://rbgeek.wordpress.com/2012/05/14/ubuntu-as-a-firewallgateway-router/)

Everything seems to work fine, but I would like the Windows clients to have to enter a username and password in order to gain access to the internet.

Can/how could I accomplish this?

Thanks in advance

---

### Post by SeijiSensei on 2015-03-22
Install **Squid** in transparent mode and require authentication.  

For the first, you need to add the keyword "transparent" to the http_port directive in squid.conf.  Then edit /etc/rc.local and add this iptables rule:
```
/sbin/iptables -t nat -A PREROUTING -s ip.addr.of.subnet/mask  -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
```
Replace ip.addr.of.subnet/mask with the CIDR address of the clients' network like 192.168.1.0/24.  This rule takes all traffic bound for remote web sites on port 80 and pushes it through Squid's listening port of 3128.

For authentication, read this: [http://wiki.squid-cache.org/Features/Authentication](http://wiki.squid-cache.org/Features/Authentication)

---

