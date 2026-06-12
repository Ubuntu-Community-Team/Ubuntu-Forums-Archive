---
title: "How do I create a forward proxy of any sort"
date: 2016-12-15
forum: Server Platforms
---

### Post by samm4 on 2016-12-15
Ok.   So I have a variable number of application servers that sit behind an AWS load balancer.  AWS load balancers do not have static addresses.  Our users can authenticate to our service using their LDAP implementations within their organization.

Our application servers then, make outbound LDAP calls to their LDAP servers.  So the destination varies by customer.  

I need to build a forwarding proxy/gateway.

My application servers will forward LDAP traffic to this proxy like so:

```

iptables -t nat -A OUTPUT -p tcp --dport 389 -j DNAT --to-destination x.x.x.x:3128

iptables -A FORWARD -p tcp -d x.x.x.x --dport 3128 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

```

the x.x.x.x box initially ran SQUID.   Tcpdump on that box showed the LDAP traffic getting to that port, but then Squid would never pick it up.    Most of my configs in Squid were complete guesswork as I can't find any working examples of anyone proxying LDAP on Squid.

Then I moved on to HAProxy.  And it's kind of the same deal.  I see plenty of tutorials, FAQs, examples and docs on using HAProxy as a reverse proxy and as a load balancer.  But not as a forward proxy.    

Am I looking at the wrong products for this goal?  Or am I misunderstanding how to set either of them up?

---

### Post by SeijiSensei on 2016-12-15
Your first rule was close, but you need to use the PREROUTING chain.

```
iptables -t nat -A PREROUTING -d ip.addr.of.server -p tcp -m tcp --dport 389 -j DNAT --to-destination ip.addr.of.target:389
```

That takes traffic arriving on port 389 of ip.addr.of.server and forwards it to port 389 on ip.addr.of.target.

Squid is intended for HTTP proxying; it's not a general proxy.

You can also use SOCKS for this purpose, but I haven't tried that.

---

### Post by samm4 on 2016-12-15
Thanks for the response and it's possible that might work for me, but it's possible it won't.

Some out of users, would have different destinations, but the same port.  Others different destination AND different port.  Though it's all the same protocol.

---

### Post by SeijiSensei on 2016-12-15
If you know the source addresses for each of the originators of the LDAP requests, you can create multiple rules by adding "-s ip.addr.of.source" and specifying the appropriate target destinations.  Something like this:
```

iptables -t nat -A PREROUTING -s 10.10.10.1 -d 10.10.10.254 -p tcp -m tcp --dport 389 -j DNAT --to-destination 10.100.100.1:389
iptables -t nat -A PREROUTING -s 10.10.10.2 -d 10.10.10.254 -p tcp -m tcp --dport 389 -j DNAT --to-destination 10.100.100.2:389
iptables -t nat -A PREROUTING -s 10.10.10.3 -d 10.10.10.254 -p tcp -m tcp --dport 389 -j DNAT --to-destination 10.100.100.3:389
[etc.]

```

---

