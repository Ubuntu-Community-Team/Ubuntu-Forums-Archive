---
title: "how to set an outbound firewall that prevents some applications to access to internet"
date: 2008-02-13
forum: Security Discussions
---

### Post by maugud on 2008-02-13
hi
I'm using Ubuntu 7.10, and I've already installed firestarter. But is there a software firewall that can limit outbound connections so that only the applications I want can access to the internet (for example only firefox or xmms and not  all other applications that are installed)?

---

### Post by bernied on 2008-02-13
This might be possible through iptables, though I am not certain.
[Here is a tutorial](http://iptables-tutorial.frozentux.net/iptables-tutorial.html#IPFILTERGENERALTERMS).

---

### Post by bernied on 2008-02-13
It looks like you can match outgoing packets based on their owner. I found this in the [same tutorial mentioned above](http://iptables-tutorial.frozentux.net/iptables-tutorial.html#OWNERMATCH).

I use [Shorewall](http://www.shorewall.net/), which isn't all that much easier than controlling iptables directly, but I still don't know exactly how to implement what you're asking for.

---

### Post by k_grdn on 2008-02-13
Hi,

IPtables is installed by default.

Set your default polict to drop on all chains, then explicitly ACCEPT inbound, outgoing connections, also don't forget to allow connections to the loopback interface.

example rules:

iptables -A OUTPUT -o eth0 \
      -s $INT-IP --sports $UNPRIV_PORTS \  
      -m state ESTABLISHED,RELATED -j ACCEPT

iptables -A INPUT -i eth0 \
      -d $INT-IP  \  
      -m state ESTABLISHED,RELATED -j ACCEPT

iptables -A OUTPUT -o eth0 -p tcp \
      -s $INT-IP --sports $UNPRIV_PORTS \
      -m multiport --dports 80,443 \
      -m state --state NEW -j ACCEPT

Regards,

k_grdn

---

### Post by HermanAB on 2008-02-14
What you want to do can partially be done by tcpwrappers, but is best done with squid-cache.

Cheers,

Herman

---

