---
title: "ufw port forwarding"
date: 2012-10-03
forum: Security
---

### Post by Fragarach87 on 2012-10-03
I'm running a ubuntu server and just upgraded it from 10.04 to 12.04. I had port forwarding using working fine on it before the distribution upgrade but now after it is no longer working. So I'm now trying to figure out what has gone wrong with the configuration. These files were not changed since the distribution upgrade... any thoughts on how to get it working again?

before.rules (above *filter)
```
*nat
:PREROUTING - [0:0]

# DNAT rules
# -A PREROUTING -i eth0 -p tcp --dport 3690 -j DNAT --to-destination 192.168.133.111:3690
# -A PREROUTING -i eth0 -p udp --dport 3690 -j DNAT --to-destination 192.168.133.111:3690
# -A PREROUTING -i eth0 -p tcp --dport 3389 -j DNAT --to-destination 192.168.133.111:3389
# -A PREROUTING -i eth0 -p udp --dport 3389 -j DNAT --to-destination 192.168.133.111:3389

# -A PREROUTING -i br0 -p tcp --dport 3690 -j DNAT --to-destination 192.168.133.111:3690
# -A PREROUTING -i br0 -p udp --dport 3690 -j DNAT --to-destination 192.168.133.111:3690
# -A PREROUTING -i tun0 -p tcp --dport 3389 -j DNAT --to-destination 192.168.133.111:3389
# -A PREROUTING -i tun0 -p udp --dport 3389 -j DNAT --to-destination 192.168.133.111:3389

-A PREROUTING -p tcp --dport 3690 -j DNAT --to-destination 192.168.133.111:3690
-A PREROUTING -p udp --dport 3690 -j DNAT --to-destination 192.168.133.111:3690

COMMIT
```


before.rules (at end of file before last commit)
```
# Open VPN Bridge Forward
-A INPUT -i tap0 -j ACCEPT
-A INPUT -i br0 -j ACCEPT
-A INPUT -i eth0 -j ACCEPT
-A FORWARD -i br0 -j ACCEPT
-A FORWARD -i eth0 -j ACCEPT
-A FORWARD -p tcp -d 192.168.133.161 --dport 3690 -j ACCEPT
-A FORWARD -p udp -d 192.168.133.161 --dport 3690 -j ACCEPT
```


rc.local
```
/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
/sbin/iptables -t nat -A POSTROUTING -o br0 -j MASQUERADE

route add default gw 192.168.133.1
```

---

### Post by Fragarach87 on 2012-10-03
I should also mention that net.ipv4.ip_forward=1 is commented in sysctl.conf

---

### Post by Fragarach87 on 2012-10-03
Ended up using rinetd, much simpler and seems to be working as advertised.

[http://www.ubuntugeek.com/rinetd-redirects-tcp-connections-from-one-ip-address-and-port-to-another.html](http://www.ubuntugeek.com/rinetd-redirects-tcp-connections-from-one-ip-address-and-port-to-another.html)

---

