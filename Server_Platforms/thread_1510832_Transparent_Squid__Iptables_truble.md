---
title: "Transparent Squid / Iptables truble"
date: 2010-06-16
forum: Server Platforms
---

### Post by StarF on 2010-06-16
Hi

I am trying to set up a transparent proxy. The squid part is working fine, how ever i seem to have some truble with my iptables rules, this is what i have done.

eth0 - management
eth1 - eth3 is made into a bridge br0

i then add these rules to take the trafic from the br0 and throw it through the squid:

```
bash# ebtables -t broute -A BROUTING -p IPv4 --ip-protocol 6 \
        --ip-destination-port 80 -j redirect --redirect-target ACCEPT

bash# iptables -t nat -A PREROUTING -i br0 -p tcp --dport 80 \
        -j REDIRECT --to-port 8090
```

then i do a iptables --list

and i only get this:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
fedtmule@squid-adm-01:~$
```

same with ebtables
```

Bridge table: filter

Bridge chain: INPUT, entries: 0, policy: ACCEPT

Bridge chain: FORWARD, entries: 0, policy: ACCEPT

Bridge chain: OUTPUT, entries: 0, policy: ACCEPT
fedtmule@squid-adm-01:~$
```

also if i delete all my rules, i for some odd reason cant browse through the bridge, as far i know, i should be able to do that?
I used some of this guide for the bridge/iptables stuff:
[http://freshmeat.net/articles/configuring-a-transparent-proxywebcache-in-a-bridge-using-squid-and-ebtables](http://freshmeat.net/articles/configuring-a-transparent-proxywebcache-in-a-bridge-using-squid-and-ebtables)

my squid is on 8090

---

