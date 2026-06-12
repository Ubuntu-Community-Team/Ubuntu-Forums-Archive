---
title: "DHCP server configuration with attached router?"
date: 2012-04-18
forum: Server Platforms
---

### Post by zkvvoob on 2012-04-18
Hello!

I am relatively new to the server management configuration and I would very much appreciate your help with this task I am faced with.

I have an HP server that I wish to use for various purposes, but mainly as a web server. However, the machine being at home, I would like to find its optimal place in the local network, which, so far, has consisted of two laptops, my cellphone and a wireless router to manage all of them. 

What I want to do is to plug the internet cable to one of the NICs of the server, so that it won't be slowed down by the router's poor performance, while at the same time using the second NIC to deliver internet connection to the router and via the router - the the rest of the not-so-speed-dependent devices.

I've followed several guides to set up DHCP3 server, but I encountered several problems, such as the .conf file being placed at a different directory. However, even after finding the configuration and setting it up, the dhcp service reported that there was no subnet configuration for the eth1 interface.

So, I am asking you for help: how should I configure it so that it functions in the way I described above?

Thank you!

---

### Post by sj1410 on 2012-04-18
installing and configuring DHCP server on ubuntu is pretty simple, go thru the below link which explains it in detail

[http://www.techpage3.com/2012/01/howto-install-configure-dhcp-server-on.html](http://www.techpage3.com/2012/01/howto-install-configure-dhcp-server-on.html)

---

### Post by darkod on 2012-04-18
dnsmasq is a very simple DHCP and DNS forwarding package.
[http://wiki.debian.org/HowTo/dnsmasq](http://wiki.debian.org/HowTo/dnsmasq)

You can give it a go if you find it easier to configure.

---

### Post by jason0 on 2012-04-18
Hello,

If this is to work you must be certain you can even network directly to your ISP from your server. 

My first thought is centered on this comment:

> **zkvvoob said:**
> What I want to do is to plug the internet cable to one of the NICs of the server, so that it won't be slowed down by the router's poor performance, 

First, it depends on the technology used.  Most ISP's provide a router that converts from something (like dsl, or cable) to ethernet.  The WAN or Internet jack on these boxes often look like a network jack, but that's a convenience only.  Your solution requires that your provider has given you TWO boxes, the first to only convert to ethernet and tcp/ip, and the second to be your router.

The second: Some of the routers that ISP's provide have bad built-in ethernet switches.  this could be bypassed by getting your own ethernet switch: Connect all of your servers, and clients to this separate switch and then only run one cable between the switch and your ISP's router.  This may seem counter-intuitive, but remember that switching ethernet and routing tcp/ip are two different things.


> **zkvvoob said:**
> while at the same time using the second NIC to deliver internet connection to the router and via the router - the the rest of the not-so-speed-dependent devices.


If your desire is not to connect directly to your ISP's uplink cable, but just have all of your other hosts traffic go through your server as if it were the router/bridge, then I recommend my solution above: network hubs/switches are cheap (relatively speaking).  That's the simplest way.

You can do any number of networking setups with your server: you can actually have your server act as an ethernet switch, with multiple ethernet cards itself.  You can have it act as your firewall.  However, you said that you were relatively new at the server management configuration.   I suggest you keep your network as simple as possible because if anything goes wrong with your server's configuration, you could make your entire network unusable.

--jason

---

### Post by newbie-user on 2012-04-19
> **zkvvoob said:**
> the dhcp service reported that there was no subnet configuration for the eth1 interface.


Have you already set up eth1 in the /etc/network/interfaces file? If you have, then check to see if you have a netmask listed for eth1. Should look like this:

```
auto eth1
iface eth1 inet static
   address [ip address]
   netmask [subnet mask]
   network [network address]
   broadcast [broadcast address]
```

---

### Post by zkvvoob on 2012-04-20
Guys, much obliged for the help!

I'll stick with me router for the time being, it's the simplest method, like Jason pointed out.

---

