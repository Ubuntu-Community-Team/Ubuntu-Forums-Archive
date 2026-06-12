---
title: "Multiple Gateways"
date: 2006-03-21
forum: Server Platforms
---

### Post by LKRaider on 2006-03-21
This may sound strange to some, but I have a connection to my Ubuntu box like this:

```

                                     +-----ISP1 (gateway 192.168.1.x)
subnet----(eth1)-UbuntuBox-(eth0)----|
                                     +-----ISP2 (gateway 192.168.1.y)

```

As you can see, I have two internet exits as gateways on my eth0 connection (through a hub), and I want to be able to use them both (preferably load balanced + fail-over). There's no DHCP, all networks are fixed IP.

Computers on the subnet should define my UbuntuBox as their gateway, and the box should automatically SNAT them throught the available gateways.

Is this possible? I know I can do this in Windows(XP), but can't figure how to add more gateways for the same interface in Linux and define an automatic metric for them.

I found (very few) links relating to this:
-> routes with multiple gateway : [1](http://www.ussg.iu.edu/hypermail/linux/net/9805.1/0139.html) [2](http://www.ussg.iu.edu/hypermail/linux/net/9805.1/0143.html)
-> [Routing for multiple uplinks/providers](http://www.ssi.bg/~ja/nano.txt)

Do I need to recompile the kernel to support this, or does Ubuntu already do?
How do I go about configuring this?

---

### Post by Horndog on 2006-03-21
This is some thing hat I was looking at a while back. A twin wan router made for load balancing through two ISP's and is platform independent. As far as doing it in one computer with software I can't help you.

[http://www.xincom.com/]("http://www.xincom.com/")

---

