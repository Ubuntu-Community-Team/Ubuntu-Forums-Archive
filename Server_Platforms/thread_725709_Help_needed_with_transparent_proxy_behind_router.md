---
title: "Help needed with transparent proxy behind router"
date: 2008-03-15
forum: Server Platforms
---

### Post by notanumber67890 on 2008-03-15
With tons of help from reading these forums I have managed to build my first transparent Squid proxy on LTS 6.06 Dapper.

I would like to keep the proxy behind my firewall/router device and have clients use it transparently by giving them the proxy's IP (10.0.0.19) as the default gateway via DHCP. 

This works well for port 80 but all other traffic goes into a black hole (as you'd expect). I would like to use IPtables to redirect everything to the real gateway (10.0.0.1) other than TCP port 80 which is currently handled as follows:

 iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

There is only one NIC on the box and I need to keep receiving traffic sent to the local IP for SSH, Webmin etc.

I'm in way over my head with IPtables, can anyone suggest the rules needed to redirect all external traffic to my gateway, and any rules needed to get the response back to the client?

---

