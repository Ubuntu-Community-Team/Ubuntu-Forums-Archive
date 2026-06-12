---
title: "TinyProxy as a transparent proxy"
date: 2009-02-25
forum: Server Platforms
---

### Post by sylock on 2009-02-25
Hi here,

I used to install Squid but I have one tiny hardware on which squid is too hudge. Squid makes the net much slower than before (unusable).

So I installed and configured TinyProxy some days ago. Everything works well because when I configure my browser to use it, the filtering is working and we can have access to the www.

The next point was to install it as a transparent proxy not to configure each browser of each computer now and in the future. So I added an iptables rule that redirect (on the tinyproxy port) every tcp packet that comes from eth1 (lan) and which the destination port is 80:
iptables -t NAT -A PREROUTING -p tcp -m tcp -i eth1 --dport 80 -J REDIRECT --to-ports 8888

When I do that, nobody can surf on the web anymore.

This rule had worked with Squid but I had to add the "transparent" keyword in its config file ; I didn't found a similar keyword for tinyproxy.

-> my question is : is there a way to configure tinyproxy as a transparent proxy or not? And did I make it the right way?

Thank you so much for your help.
Nicolas Michel

---

### Post by ajaypulipra on 2010-12-28
You got any solution for this? If yes please help me..:cry:

---

### Post by sylock on 2010-12-29
No. Tinyproxy don't work in transparent mode. You have to configure every desktop to use the proxy (could be done with GPO if you are in a windows domain).

---

### Post by Tybion on 2011-11-20
I have installed tinyproxy on Ubuntu 11.10.

Showing a snippet of changelog.Debian (in /usr/share/doc/tinyproxy) ..

> tinyproxy (1.6.3-3.2) unstable; urgency=low
         :      :       :
  * Pass --enable-filter --enable-transparent-proxy --enable-upstream
    to configure to explicitly enable some missing features.
    ( closes: #400931, LP #42598 ).


This means that the debian (/Ubuntu) package has been enabled for transparency ever since 1.6.3-3.2.  I have confirmed this with the Debian package maintainer.

I have not yet confirmed this with a working system - waiting on some hardware.

---

