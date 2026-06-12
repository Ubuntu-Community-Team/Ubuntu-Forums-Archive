---
title: "Default gateway with two ethernet cards"
date: 2008-02-05
forum: Server Platforms
---

### Post by mgarcia-val on 2008-02-05
Hi, I have a server with two ethernet cards.

eth0 is connected to my home network (ip=192.168.2.1 gw=192.168.2.1)
eth1 is connected to the router (ip=192.168.1.95 gw=192.168.1.1)

As you can see, both have static ip addresses.

eth1 is the default gateway (I did this through GUI System > Administration > Networking, and them selecting eth1 as the default gateway)

And it works: my box and everyone in my network can connect to the internet. However, sometimes, when I restart the computer the default gateway unexpectedly switches to eth0 for reasons that I don't know.

Does anyone know a CLI way of telling the system that it should take eth1 as the default gateway?

Thanks.

---

### Post by zooper on 2008-02-05
have you tried:
route add default gw 192.168.1.1 -i eth1
you might have to remove the gw assigned to eth0 with route -del default gw 192.168.2.1 before you issue the route add default gw command.

I'am not so familiar with Ubuntu, so there might be another and better way to do it.

---

### Post by mgarcia-val on 2008-02-05
Well, I'll post the output of route -n if this helps:

```
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
```

I am not familiar with the command route, so before doing what you suggest I'd like to know what route add default gw 192.168.1.1 -i eth1 does and how to reverse it in case it brings the network to a halt. Does it tell the incoming traffic from eth0 to find its way always through eth1?

Thanks.

---

### Post by kirsche on 2008-02-06
hmmm, it would be interesting to see how your routing table looks when it "works" as to compared when it fails.

generally speaking, if you remove a route, you can either add it manually again, reboot the system, or ifdown/ifup your interfaces.

One thing I could think of would be changing the metric, for example:

```

route add default gw 192.168.1.1 metric 1 dev eth1
route add default gw 192.168.2.1 metric 10 dev eth0

```

(make sure your ip's fit the interface)

---

### Post by astrotech226 on 2008-02-06
I like to do this configuration in the /etc/networking/interfaces file.  Make sure there is a line like...

        gateway 192.168.1.1

... under the eth1 interface.  Make sure there is no gateway for eth0.  This will  work because anything destined for the 192.168.2 network will go out eth0 automatically and anything destined for the 192.168.1 network will go out the eth1 interface.

Then, any IP addresses not in those two ranges will go to the default gateway of 192.168.1.1.

To activate it without a reboot, do a:

$ sudo /etc/init.d/networking restart

This is exactly what kirsche and zooper explained to do, but makes it active on reboot.

---

### Post by mgarcia-val on 2008-02-07
Thanks for the replies.

Yes, there is a line gateway 192.168.1.1 under the eth1 interface.

I just removed the gateway for eht0 and seems to be working.

What I didn't know is that that was enough for what you say, namely, that > any IP addresses not in those two ranges will go to the default gateway of 192.168.1.1. That is probably the crucial thing, because then the machine will probably know on reboot that eht1 is the only gateway.

But if that change still doesn't work, I suppose I could always include in /etc/network/interfaces, in place of eth0 gateway (which I just removed), something like this:```
up route add -net 192.168.2.0 netmask 255.255.255.0 gw 192.168.1.1

```
which can be a bit tentative but which I could  easily undo if necessary.

---

