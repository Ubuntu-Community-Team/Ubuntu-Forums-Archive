---
title: "Masquerading side effect"
date: 2011-10-08
forum: Server Platforms
---

### Post by Sock! on 2011-10-08
Hi Guys,
I have a little problem with iptables masquerading. All my house's traffic is going though my ubuntu 11.04 box but cant connect to some sites. e.g. connect.facebook.com and cisco.com to name a few. iptables is not blocking anything and I'm not quite sure where to start looking with this. I have connected directly into my modem and these sites are reachable and DNS is not a problem.

Masquerading rule if needed:
```
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -o eth0 -j MASQUERADE
iptables-save

```

Any help/suggestions would be greatly appreciated.

---

### Post by bbqroast on 2011-10-08
I think those are SSL sites???
Maybe Ubuntu has been set up to block the SSL port (443).

---

### Post by Sock! on 2011-10-08
> **bbqroast said:**
> I think those are SSL sites???
Maybe Ubuntu has been set up to block the SSL port (443).

I wouldn't think so because I can't open this website ([http://www.juniper.net/as/en/products-services/security/srx-series/srx210/](http://www.juniper.net/as/en/products-services/security/srx-series/srx210/)) and it is clearly not https. :sad:

---

### Post by Doug S on 2011-10-08
Without broader exposure to your iptable rules, it is hard to make suggestions. Perhaps use some temporary log statements in your iptables rules to figure out where packets are travsering and/or tcpdump or wireshark to see if packets are leaving or not coming back or whatever.
You could also try:```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```or (which, according to my notes (cann't recall the reference), is the stricter form of the above):```
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to $EXTIP
```where $EXTIP is your external IP address.

---

