---
title: "iptables port redirection problem"
date: 2007-01-09
forum: Server Platforms
---

### Post by horvatj on 2007-01-09
Hello ubuntu networking people!

I have the following configuration:

**Gateway:**
  eth0 (WAN) with something like 83.9.9.9
  eth1 (LAN) with 10.1.1.1
  running sshd on port 22
[B]
Server 1 (internal):[/B]
  eth0 with 10.1.1.2
  running sshd on port 22

**Server 2 (internal):**
  eth0 with 10.1.1.3
  running sshd on port 22

I want my firewall script (using iptables) to redirect the following
ports on the getway eth0:
*2222 to 10.1.1.2:22*
*2223 to 10.1.1.3:22*

I've tried the following lines, but this gives me just the login to the
gateway server:
```
[...]
LAN_IP=$(ifconfig eth1 | head -n 2 | tail -n 1 | cut -d: -f2 | cut -d"
" -f 1)
[...]
iptables -A INPUT -i eth0 -m state --state NEW -p tcp --dport 2222 -j
ACCEPT
iptables -I FORWARD -s 0/0 -d 10.1.1.2 -p tcp --dport 22 -i eth0 -j
ACCEPT
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 2222 -j DNAT
--to-destination 10.1.1.2:22
iptables -t nat -A POSTROUTING -o eth1 -p tcp --dport 22 -j SNAT
--to-source $LAN_IP
[...]
```

What am I doing wrong???

Thank you
Johann

---

