---
title: "how to block all ports except pop and smtp in NAT through iptables"
date: 2010-01-20
forum: Security
---

### Post by smjd7 on 2010-01-20
how to block all ports except pop,pop3,smtp in nat using iptables in squid on redhat A3

---

### Post by Sarmacid on 2010-01-20
Check this out [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by Lars Noodén on 2010-01-20
Also, be sure to allow [ICMP](http://www.iana.org/assignments/icmp-parameters).  In particular echo-request and traceroute to your machine, especially if you are hosting any services.  

But even if you are not hosting, some ICMP is required anyway for networking and if you block it by accident, the network is broken and some problems will be much harder to diagnose.

For example,

```

# echo
   iptables  -A INPUT -p icmp --icmp-type echo-request \
         -m limit --limit 1/s -i eth0 -j ACCEPT

   ip6tables -A INPUT -p icmpv6 --icmpv6-type echo-request \
         -m limit --limit 1/s -i eth0 -j ACCEPT

# traceroute
   iptables  -A INPUT -p icmp --icmp-type 30 \
         -m limit --limit 1/s -i eth0 -j ACCEPT

   ip6tables -A INPUT -p icmpv6 --icmpv6-type 30 \
         -m limit --limit 1/s -i eth0 -j ACCEPT

# YMMV

```

---

