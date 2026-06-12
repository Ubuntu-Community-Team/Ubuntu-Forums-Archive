---
title: "SSLH as Transparent Proxy"
date: 2018-05-03
forum: Server Platforms
---

### Post by acascianelli on 2018-05-03
Has anybody ever run SSLH as a transparent proxy under Ubuntu Server?  They have instructions on how to do it on their site, but they are for iptables and not UFW.

Here are the require iptables rules:
```
# iptables -t mangle -N SSLH
# iptables -t mangle -A  OUTPUT --protocol tcp --out-interface eth0 --sport 22 --jump SSLH
# iptables -t mangle -A OUTPUT --protocol tcp --out-interface eth0 --sport 4443 --jump SSLH
# iptables -t mangle -A SSLH --jump MARK --set-mark 0x1
# iptables -t mangle -A SSLH --jump ACCEPT
# ip rule add fwmark 0x1 lookup 100
# ip route add local 0.0.0.0/0 dev lo table 100
```

[http://www.rutschle.net/tech/sslh/README.html](http://www.rutschle.net/tech/sslh/README.html)

---

