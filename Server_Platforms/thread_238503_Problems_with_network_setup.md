---
title: "Problems with network setup"
date: 2006-08-17
forum: Server Platforms
---

### Post by Guimas on 2006-08-17
Hello all!

I'm having a problem with a server I'm running with Ubuntu 6.06. This machine has two NIC's, eth0 and eth1. eth0 is connected to a ADSL Router, eth1 is connected to my hub, and my internal network.

Everything is working great: my internal machines, using WinXP and Ubuntu, all can see my server, and can connect to the internet. DHCP, Samba, Apache and MySQL all run fine, No problems there.

The config is like this: eth0 is 192.168.1.3, eth1 is 192.168.1.4, and the adsl modem is 192.168.1.1. The internal machines recieve dynamic addresses ranging from 192.168.1.20 to 192.168.1.25.

The problem is that I cannot access the configuration page on the modem: The browser can't access it, and nobody (including the server) can ping 192.168.1.1 (it gives a "Destination Host Unreachable" error).

What is wrong in my setup? I know the modem is accessible, because it is serving the internet for everyone (including DNS). Why can't I ping it or reach it with a browser?

Thanks in advance, 

Guimas

---

### Post by wieman01 on 2006-08-17
Just a thought: Have you got a firewall? Or are you using "Firestarter" by chance?

---

### Post by Guimas on 2006-08-17
I have iptables set up to do NAT to my internal machines, and some port forwarding also. It seems to be working fine. Everything works OK, with the exception of not being able to access the modem setup page with any machine.

---

### Post by wieman01 on 2006-08-18
> **Guimas said:**
> I have iptables set up to do NAT to my internal machines, and some port forwarding also. It seems to be working fine. Everything works OK, with the exception of not being able to access the modem setup page with any machine.

Do you access the router through HTTP or HTTPS? HTTPS' port is different than the HTTP one.

Can you access the Internet or do you have the same problem?

---

### Post by lvanderree on 2006-08-18
As far as I know you cannot have two nic's on the same network-addresses, unless you setup your server as a bridge. You've got bridge tools package for that on Ubuntu, and you have to give both your nics the same IP.

you can try this, but  be aware it gave me a lot of problems!

I used the following setup (adjusted for your situation):
```

auto br0
iface br0 inet static
        address 192.168.1.3
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        dns-nameservers 192.168.1.1
        bridge_ports eth1 eth2

```

problems I encountered where:
-I had to try this a couple of times, before the bridge finally worked, still not sure why... But when you type ifconfig and see that you haven't got the br0 device, edit your config file a little (/etc/network/interfaces) and try it again. (restart your system, because /etc/init.d/network restart doesn't work very well with bridges)
-when this finally works ones, it works OK every reboot, except that it went to "learning mode" ones in a while (a couple of times a day) for a minute. During this minute you can't reach your server! So Samba fails for a minute and no internet for a minute.... Still don't know why this happened.

Maybe it all had to do with my hardware configuration and you won't have any problems, so you can of course try it.

I only hope that your ADSL-router has a firewall in it, because when you setup your server as a bridge, it can't scan the traffic which it passes through anymore (as far as I know).

-----

So an other solution is, to give your ADSL router an other IP-address placing it on an other network, like 192.168.0.1
Then also the NIC connected to the ADSL router should change it's IP, E.G. to 192.168.1.3. And to let the internet work, you should setup your server as a router, I installed shorewall for this (lots of howto you can find on that) and set it up for masquerading.

Some tips:
in /etc/shorewall/shorewall.conf set IP_FORWARDING to On (KEEP does not work, in some tuts this is done in an other way with ip-tables and extra scripts which is totally unnecesairy)

then setup zones like this:
```

fw      firewall
net     ipv4
loc     ipv4

```

interfaces like this
```

net     eth2    detect  dhcp,routefilter,tcpflags
loc     eth1    192.168.1.255   dhcp

```

policy like this
```

loc     all     ACCEPT
net     all     DROP
all     all     ACCEPT

```
NOTE: for some reason I have to use all all ACCEPT, but in most howto's this isn't the case. I did a test and because net all is on DROP my firewall is working, but I think this can be done nicer.

masq like this
```

eth2    eth1

```
or the other way around, and maybe you have got eth0 eth1, instead of eth2, so change this everywhere....

then you can have rules for accepting, like
```

ACCEPT  net     all     tcp     ftp,222,smtp,www,imap2

```
and for forwarding
```

DNAT    net     loc:192.168.0.33        tcp     6881
DNAT    net     loc:192.168.0.33        udp     6881

```

When your ADSL router is forwarding all traffic to your server, this should be it.

Even nicer is if you can disable the router function on your ADSL and set that up as a bridge, and your server as a router, with firewall (with shorewall)

---

### Post by Guimas on 2006-08-18
Thanks for your replies.

I guess I could set the NIC of the modem to use the 192.168.1.* address space, and my internal network to use the 192.168.2.* address space, also, and avoid the bridge solution.

Since I don't know shorewall, is it a replacement for iptables, or just a wrapper for it?

---

### Post by lvanderree on 2006-08-18
I can't say it better myself, so:

*The Shoreline Firewall, more commonly known as "Shorewall", is a high-level tool for configuring Netfilter. You describe your firewall/gateway requirements using entries in a set of configuration files. Shorewall reads those configuration files and with the help of the iptables utility, Shorewall configures Netfilter to match your requirements*

[http://www.shorewall.net/](http://www.shorewall.net/)

it even has a webmin interface, but it is really easy and powerfull. Examples are also included in /usr/share/doc/shorewall/examples/two-interfaces

I'm not sure if you can configure your ADSL-router from a workstation, but from your server shouln't be a problem anymore.

---

### Post by Guimas on 2006-08-18
Thanks for your replies, I will try shorewall.

---

