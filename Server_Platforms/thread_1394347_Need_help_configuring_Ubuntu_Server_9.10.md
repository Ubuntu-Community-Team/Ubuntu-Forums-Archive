---
title: "Need help configuring Ubuntu Server 9.10"
date: 2010-01-30
forum: Server Platforms
---

### Post by intermentals on 2010-01-30
I'm trying to get my set up to provide internet to my LAN through a squid proxy. I have DHCP set up and working and I think squid is configured right, my question is what else do I need to configure for the server to function and how do I do it?

Also the server I'm replacing is running OpenBSD 4.5 and uses a wpad.dat file for automatic configuration for squid, how would I go about using this same set up in Ubuntu?

Thanks

---

### Post by ICEB3AR on 2010-01-30
You had to enable IP-Forwarding:
```
sysctl -w net.ipv4.ip_forward=1
```
and give a Rule in ip-tables
```
iptables -A POSTROUTING -t nat -o eth0 -j MASQUERADE
```
Check out iptables to make it save.

---

### Post by intermentals on 2010-01-30
thank you very much how can I make the system run that each time it boots? - can anyone advise me on the wpad.dat issue?

---

### Post by Vegan on 2010-01-30
One the NAT rules are set, you do not need to load them over and over.

---

