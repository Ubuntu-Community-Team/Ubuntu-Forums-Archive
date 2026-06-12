---
title: "best Linux Firewall/web proxy server?"
date: 2008-10-18
forum: Server Platforms
---

### Post by imax36581 on 2008-10-18
hi my friends
i need your help to find that what is the best firewall/web proxy server in linux?
let me explain better... in our company we have 500 clients .now we have MS ISA server 2006 ,but we want migrate to Linux Firewall/web Proxy.
so what's your choice to use as a Firewall / Web Proxy server?
it Must be **stable**,[COLOR="Red"]powerful[/COLOR],[COLOR="Magenta"]supple[/COLOR].
**tell me what is the best and why you choose it?**

ubuntu forums is the place that always i can find my answers :)
Thanks in advance

---

### Post by imax36581 on 2008-10-19
why no body don't answer me?
is my question agaist the role?

---

### Post by hyper_ch on 2008-10-19
maybe this helps:
[http://www.howtoforge.com/ubuntu6.06_firewall_gateway](http://www.howtoforge.com/ubuntu6.06_firewall_gateway)

---

### Post by lykwydchykyn on 2008-10-20
Linux has a firewall engine built in to the kernel, called netfilter.  Pretty much every "firewall" program on Linux is just a front-end for netfilter.  Depending on your requirements and what sort of interface you like, you can probably find a front end that fits your needs.  There are GUIs, Web-based interfaces, and high-level configuration languages if you prefer scripting.  

As for proxy, squid is usually the first choice from what I've seen, though it's not the only choice.

---

### Post by imax36581 on 2008-10-20
thanks mate
what about IPCOP?

---

### Post by TreeFinger on 2008-10-20
I built a server that acts as a router/firewall/proxy. I don't feel as though I can give you any answers to your questions because you stated that your business has 500 clients and my home network only consists of 2 desktops, web server, and the router/firewall/proxy server.

I use iptables to set firewall rules and forward packets, and squid as my proxy.

---

