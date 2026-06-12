---
title: "iptables routing through proxy"
date: 2011-09-09
forum: Security
---

### Post by Frozen Forest on 2011-09-09
I'm trying to get iptables to route some traffic through a proxy if I'm connected to a specific subnet, I did setup PREROUTING but nothing happen, all counters show zeros (iptables -t nat -vn -L). Before using the proxy should an ssh tunnel be setup like this [http://embraceubuntu.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://embraceubuntu.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)
[PHP]
iptables -t nat -A PREROUTING -p tcp -s $subnet-proxy --dport 80  -m state --state NEW,ESTABLISHED -j DNAT --to 127.0.0.1:9999
[/PHP]Is there something I'm missing, default nat policy for PREROUTING, INPUT, OUTPUT, FORWARD, POSTROUTING is ACCEPT. Should more thing be added, haven't made any more changes to iptables except the one above. The normal iptables (iptables -vn -L) allow loopback so  it should accept the packages.

---

### Post by HermanAB on 2011-09-09
Maybe you should look at the REDIRECT target.

Anyhoo, in my experience, the easiest ways to route traffic is with 'route' (surprise!) and 'socat'.

---

### Post by regala on 2011-09-09
> **Frozen Forest said:**
> I'm trying to get iptables to route some traffic through a proxy if I'm connected to a specific subnet, I did setup PREROUTING but nothing happen, all counters show zeros (iptables -t nat -vn -L). Before using the proxy should an ssh tunnel be setup like this [http://embraceubuntu.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://embraceubuntu.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)
[PHP]
iptables -t nat -A PREROUTING -p tcp -s $subnet-proxy --dport 80  -m state --state NEW,ESTABLISHED -j DNAT --to 127.0.0.1:9999
[/PHP]Is there something I'm missing, default nat policy for PREROUTING, INPUT, OUTPUT, FORWARD, POSTROUTING is ACCEPT. Should more thing be added, haven't made any more changes to iptables except the one above. The normal iptables (iptables -vn -L) allow loopback so  it should accept the packages.

you must never use state ESTABLISHED in nat table rules, or more precisely, it is useless: connections marked as ESTABLISHED or RELATED in the conntrack tables never go thru the NAT table rules again, and then your rule can never match on ESTABLISHED connections. After a connection thru nat or not is ESTABLISHED, the conntrack table remembers all nat transformations back and forth pertaining to that connection and apply them and let the packets only thru the "filter" table.

so that your rule does not need any state match test.

```

iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --redirect-to proxy_address:proxy_port

```

---

