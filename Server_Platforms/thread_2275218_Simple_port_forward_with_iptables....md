---
title: "Simple port forward with iptables..."
date: 2015-04-24
forum: Server Platforms
---

### Post by fizgig on 2015-04-24
I'd like to forward udp packets with port 4569 from my gateway ubuntu server (PUBLICIP) to my asterisk server inside (LOCALIP).

Here are the rules I've done:

```
$IPT -t nat -A PREROUTING -p udp --dport 4569 -j DNAT --to LOCALIP
$IPT -A FORWARD -p upd --dport 4569 -j ACCEPT
$IPT -t nat -A POSTROUTING -p udp -s LOCALIP -j SNAT --to PUBLICIP


```

I run tcpdump on my gateway computer and also on my asterisk server.  When the keep-alive heartbeat packet comes from a computer on the outside, I see it hit the ubuntu gateway but not the asterisk server.  If my asterisk server generates the heartbeat packet, I see it on both ends.

Also, forwarding is enabled under /proc/sys/net/ipv4/ip_forward

Anyone know why the ubuntu gateway isn't forwarding the packet on to my asterisk server?

---

### Post by Doug S on 2015-04-24
I think that this rule```
$IPT -t nat -A POSTROUTING -p udp -s LOCALIP -j SNAT --to PUBLICIP
```needs to specify an interface. Specifically your external interface.```
$IPT -t nat -A POSTROUTING -o EXTERNAL_INTERFACE -p udp -s LOCALIP -j SNAT --to PUBLICIP
```Similiarly for your PREROUTING rule. This:```
$IPT -t nat -A PREROUTING -p udp --dport 4569 -j DNAT --to LOCALIP
```should be this:```
$IPT -t nat -A PREROUTING -i EXTERNAL_INTERFACE -p udp --dport 4569 -j DNAT --to LOCALIP
```

---

### Post by fizgig on 2015-04-25
Well, it turns out the server needed to be rebooted. I guess you can only flush iptables so many times...

Thanks for your help!

---

