---
title: "Advice for IP Maquerading"
date: 2012-09-24
forum: Server Platforms
---

### Post by ubuuser777 on 2012-09-24
Hi,

As per the server guide for ufw masquerading -> [https://help.ubuntu.com/12.04/serverguide/firewall.html](https://help.ubuntu.com/12.04/serverguide/firewall.html), I've edited the necessary files and restarted the services/server.

However the clients devices are unable to grab an IP ADDR e.g.

> [UFW BLOCK] IN eth2 OUT= MAC=00:11:22:33:44:55:54:53:52:51:50:49 SRC=192.168.1.150 DST=192.168.1.254 LEN=65 TOS=0x00 PREC=0x00 TTL=255 ID=25250 PROTO=UDP SPT=63640 DTP=53 LEN=45

2 - Questions:

Do I need to install BIND9 since all the ports referenced in the UFW logs point to port 53 (DNS)? The server is used as a  router/dhcp server.

Do I need to do this -->  sudo ufw allow from 192.168.1.0/24 && sudo ufw allow to 192.168.1.0/24? (this is not shown in the above mentioned guide, so I would think it should not be necessary.)

Any insights much appreciated.

---

### Post by darkod on 2012-09-25
Depending how you did the iptables (ufw) rules, unless you specifically allow UDP port 53 (the DNS service) it gets blocked.

What you can do, is allow UDP port 53 to the router machine and make that machine DNS server for the machines on your LAN. You can make it easy DNS forwarder (it just forwards request to other outside DNS servers) without installing bind or anything with dnsmasq:
[http://wiki.debian.org/HowTo/dnsmasq](http://wiki.debian.org/HowTo/dnsmasq)

Be careful, if you make the router a DNS server, you need to allow UDP port 53 incoming to that machine.

If you decide your machines on the LAN to use outside DNS, you must allow UDP port 53 to pass through (forward).

So, it depends what you decide to do.

PS. I suggest you use iptables directly and not ufw. In a recent project I also used ufw because iptables looked too complicated at that time, but while investigating for ufw I actually realized how much easier (and cleaner) it would have been with iptables. After I finished the project unfortunately. :)

---

