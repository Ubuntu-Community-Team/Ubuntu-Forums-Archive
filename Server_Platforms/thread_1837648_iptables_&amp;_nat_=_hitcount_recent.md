---
title: "iptables &amp; nat = hitcount recent"
date: 2011-09-02
forum: Server Platforms
---

### Post by 11notes on 2011-09-02
I have a problem setting up iptables with nat and -m recent hitcount, it just doesnt work, here an exampel without nat which works just fine:

```

$IPT -A INPUT -m recent --name FLOODHOST --set -p tcp --dport 22 -d $IP_FW
$IPT -A INPUT -m recent --name FLOODHOST --rcheck --seconds 600 --hitcount 4 -p tcp --dport 22 -d $IP_FW -j LOGFLOOD
```Which bans everyone for 10minutes who connects more than 3 times to ssh, now I want the same for PREROUTING, but it wont work:

```

$IPT --table nat -A PREROUTING -p tcp -m multiport --dports 25,110,443 -j DNAT --to $IP_EXCHANGE
$IPT -A FORWARD -m recent --name FLOODNAT --set -p tcp -m multiport --dports 25,110,443 -d $IP_EXCHANGE
$IPT -A FORWARD -m recent --name FLOODNAT --rcheck --seconds 20 --hitcount 4 -p tcp -m multiport --dports 25,110,443 -d $IP_EXCHANGE -j LOGFLOOD

```I can connect once via telnet to port 25, and then I get banned, so it doesnt work quiet well. How can I use --rcheck with PREROUTING and FORWARD so that let's say only 5 connections per 20 seconds are allowed?

---

