---
title: "squid3 proxy issue about https"
date: 2015-10-30
forum: Server Platforms
---

### Post by madzombie on 2015-10-30
Hello,
I installed squid3 with ssl I can do set squid3 for http proxy is ok.
I created ca certificate for https and write following line in squid3.conf file;
```

ssl_bump allow all
https_port 3129 transparent ssl-bump key=/root/certson/son.pem cert=/root/certson/son.pem

```

son.pem file included key and certificate code. 

after restart squid3 and  I can telnet 3129 port.
however, browsers not reach to sites via proxy.

no show any error under the /var/log/syslog and /var/log/squid3/access.log log files.

normally, I can use https proxy with this settings. But, I restart ubuntu after then browser can't open https pages.

---

### Post by SeijiSensei on 2015-10-30
Did you install the certificate in the browser?  Did you set up an iptables rule to send traffic for remote port 443 through the proxy?  That's what "transparent" means.

```
/sbin/iptables -t nat -A PREROUTING -s 10.10.10.0/24 -p tcp -m tcp --dport 443 -j REDIRECT --to-ports 3129
```
Replace "10.10.10.0/24" with your local network subnet.

---

