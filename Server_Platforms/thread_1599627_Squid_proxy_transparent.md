---
title: "Squid proxy transparent"
date: 2010-10-18
forum: Server Platforms
---

### Post by hohoangluan on 2010-10-18
I have already configured squid + iptables. After config, i can't access to every site because it inform me "ACCESS DENY". Please help me.
```

echo "1" > /prot/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 3128

```
```

acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
acl localnet src 10.0.0.0/8     # RFC1918 possible internal network
acl localnet src 172.16.0.0/12  # RFC1918 possible internal network
acl localnet src 192.168.0.0/16 # RFC1918 possible internal network
 
acl home_network src 192.168.1.0/24
 
http_access allow manager localhost
http_access deny manager
# Only allow purge requests from localhost
http_access allow purge localhost
http_access deny purge
# Deny requests to unknown ports
http_access deny !Safe_ports
# Deny CONNECT to other than SSL ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
 
######################LAN NETWORK##########
http_access allow home_network
 
# And finally deny all other access to this proxy
http_access deny all
 
http_port 3128 transparent
 

```

---

### Post by SeijiSensei on 2010-10-18
Try reversing the order of the iptables rules.  You need to push the web traffic through the proxy before it's masqueraded.

---

### Post by srinu.mca5 on 2011-02-16
These ip tables rules are enough for transparent proxy

iptables --table nat --append POSTROUTING --out-interface $INTERNET -j MASQUERADE
iptables --append FORWARD --in-interface $LAN_IN -j ACCEPT

iptables -t nat -A PREROUTING -i $LAN_IN -p tcp --dport 80 -j DNAT --to $SQUID_SERVER:$SQUID_PORT
# if it is same system
iptables -t nat -A PREROUTING -i $INTERNET -p tcp --dport 80 -j REDIRECT --to-port $SQUID_PORT

---

