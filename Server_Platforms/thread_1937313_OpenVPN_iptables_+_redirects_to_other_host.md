---
title: "OpenVPN iptables + redirects to other host"
date: 2012-03-07
forum: Server Platforms
---

### Post by Wouter_DS on 2012-03-07
Hello,

I have finally managed to install OpenVPN on my server and works good.
But the only problem is that when I run the iptables for OpenVPN it breaks my other rules that are forwarding incoming traffic on port 443 and port 444 to another host.

Anyone who can help me combining them so they'll work together?

These are my iptable rules for the OpenVPN
```
iptables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -s 10.8.0.0/24 -j ACCEPT   
iptables -A FORWARD -j REJECT
iptables -t nat -A POSTROUTING -o venet0 -j SNAT --to-source 199.180.129.110

echo 1 > /proc/sys/net/ipv4/ip_forward
```

And these are my iptable rules to forward the traffic to my other server
```
iptables -t nat -A POSTROUTING -d 173.0.57.230 \
-p tcp --dport 443 -j SNAT --to 199.180.129.110

iptables -t nat -A PREROUTING -d 199.180.129.110 \
-p tcp --dport 443 -j DNAT --to 173.0.57.230


iptables -t nat -A POSTROUTING -d 173.0.57.230 \
-p tcp --dport 444 -j SNAT --to 199.180.129.110

iptables -t nat -A PREROUTING -d 199.180.129.110 \
-p tcp --dport 444 -j DNAT --to 173.0.57.230


echo 1 > /proc/sys/net/ipv4/ip_forward
```

Thanks in advance,
WouterDS

---

### Post by Wouter_DS on 2012-03-09
Anyone who can help?

---

### Post by SeijiSensei on 2012-03-09
What happens if you disable 

```
iptables -A FORWARD -j REJECT
```

---

