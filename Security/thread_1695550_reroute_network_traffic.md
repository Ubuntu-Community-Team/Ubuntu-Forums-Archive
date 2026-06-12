---
title: "reroute network traffic"
date: 2011-02-26
forum: Security
---

### Post by nloewen on 2011-02-26
I would like to capture all network traffic and send it through a proxy (dansguardian). I can successfully capture and analyze packets using arp poisoning, but I haven't been able to route the traffic through socks and dansguardian. Any suggestions?

Thanks.

---

### Post by HermanAB on 2011-02-26
Howdy,

Go to [http://google.com/linux](http://google.com/linux) and look for "transparent proxy squid-cache".

---

### Post by SeijiSensei on 2011-02-26
He wants to run Dan's Guardian which already has a version of squid. I'm guessing he has it running on a separate box on the local network behind a router.

You have two choices.  You can either configure all the browsers to use the proxy directly, or you can redirect port 80 requests to the DG box at the router.  If you have a Linux router, you can use iptables like this:

Suppose the DG box is 192.168.1.100.  Then you'd add a rule to iptables like

```
iptables -t nat -A PREROUTING -p tcp -s ! 192.168.1.100 -d 0/0 --dport 80 -j DNAT --to-destination 192.168.1.100:3128
```

This should redirect all HTTP requests not coming from the DG box ("-s ! 192.168.1.100") to port 3128 (the squid port) on the DG box. 

If you're not running a Linux router, you might be able to do this with the router's tools, or it may not be an available option.  In that case I'd put the DG box between the local network and the Internet and use transparent proxying as Herman suggests.

---

