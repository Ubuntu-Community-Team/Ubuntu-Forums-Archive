---
title: "Redirect all network to squid"
date: 2010-04-28
forum: Server Platforms
---

### Post by teresaejunior on 2010-04-28
Hello!

I've been having a hard time googling and trying to get ALL network connection to be redirected to squid proxy. I couldn't find a proper configuration for ufw or iptables. The ideas are:

1. redirection rule should NOT depend on a specific network inteface, but should work with any connection type, ex.: ppp0 or eth0...
2. firewall rules can be for firehol, iptables, or ufw (the same as iptables, just tell me where to place them). Preferably ufw or gufw.
3. should not interfere on cups web interface and lighttpd server.

BTW: it's not a ubuntu server install

Thanks for your attention.

---

### Post by dragos2 on 2010-04-28
This is an Ubuntu forum :)

Can be done using iptables on the gateway by intercepting all trafic with port 80 destination
and redirect it to the squid machine - may be on the gateway on any port.

---

### Post by teresaejunior on 2010-04-28
Thanks for your attention!

```
This is an Ubuntu forum :)
```

:lolflag:
Let me explain better: "It's not an Ubuntu SERVER install", consider a desktop install, on which I installed lighttpd, squid...

```
Can be done using iptables on the gateway by intercepting all trafic with port 80 destination
and redirect it to the squid machine - may be on the gateway on any port.

```

That's exactly what I need, but how can I do that, taking into consideration what I mentioned, that I want the iptables rules to work for any network interface (not only ppp0...)

Thanks again

---

### Post by noway2 on 2010-04-28
Out of curiosity, are you the same poster as the person that is asking this on Tek-tips.com?

---

### Post by ghost_ryder35 on 2010-04-28
This article will walk you through it [http://www.faqs.org/docs/Linux-mini/TransparentProxy.html](http://www.faqs.org/docs/Linux-mini/TransparentProxy.html)

---

### Post by teresaejunior on 2010-04-29
```
Out of curiosity, are you the same poster as the person that is asking this on Tek-tips.com?
```

No

```
This article will walk you through it [http://www.faqs.org/docs/Linux-mini/...rentProxy.html]("http://www.faqs.org/docs/Linux-mini/TransparentProxy.html")
```

Going to have a look, thanks!

---

### Post by teresaejunior on 2010-04-29
Tried this, which is ppp0 specific:
sudo iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 80 -j REDIRECT --to-port 3128

But nothing is being redirected, actually...

Doesn't anibody have a system wide proxy?

---

