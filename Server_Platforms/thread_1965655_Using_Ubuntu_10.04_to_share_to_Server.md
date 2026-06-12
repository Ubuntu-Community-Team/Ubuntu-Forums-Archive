---
title: "Using Ubuntu 10.04 to share to Server"
date: 2012-04-26
forum: Server Platforms
---

### Post by thinktyler on 2012-04-26
My router went splat in a nasty storm, so I'm trying to find a way to connect the wireless connection from my neighbors house through ethernet to my server, so that I can ssh.

I've gone to the wired tab under 12.04 beta2 and switched to share with other computers, but the ip address is 10.0.42.1 - and I'm unable to connect to the server over SSH.

---

### Post by newbie-user on 2012-04-29
First of all, have you checked with your neighbor if it's okay to use their network?

Anyway, are you asking how to use your server as a gateway/router for your lan? If so, you need to do at least two things:

1) set up forwarding on your server in /etc/sysctl.conf by uncommenting the line:
```
#net.ipv4.ip_forward=1
```
2) set up iptables
```
iptables -t nat -A POSTROUTING -s [internal network address CIDR] -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth1 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
```

---

### Post by thinktyler on 2012-05-04
Yes, I live in a college town, and my neighbor is leting me use their internet. Thank you very much it worked perfectly. Not sure what it does, but thank you.

---

