---
title: "Setting up a router/webserver."
date: 2008-12-17
forum: Server Platforms
---

### Post by audreykitching on 2008-12-17
First i like to say hi to all here since i just registered =)
And now to my situation, i've got a Dell Poweredge 2400 server with these specs:
CPU: 2x733mhz P3
RAM: 1gb
HDD: 3x36gb scsi
OS: Debian 4.04 Stable (current OS).
NIC: It got 3 nics installed (1 on the motherboard, 2 pci).

What i want to do is that i want to use it as a router and webserver.
I've used linux (slack/deb/ubuntu) for some time (running ubuntu 8.10 on my laptop for example).

But now when it comes to routing i'm a complete newbie =)
It's going to share internet to my other computers in the apartment using my D-Link gigabit switch.

So if anyone knows any good beginners guide or so it would be great.

Although i dont know if i should stick to debian on this or install Ubuntu Server instead.

Thnx for reading.

---

### Post by devonps on 2008-12-18
It would be easier and more secure if you were to purchase a dedicated router and configured your Poweredge to be a dedicated webserver.

You can go to any of the online retailers and purchase a hardware router - they aren't that expensive, my favourites are Netgear - as I find them easy to configure and maintain.

As for the O/S it won't really matter as you may/will probably end up installing Apache as your web server.

Hope this helps,

Steve.

---

### Post by audreykitching on 2008-12-18
Well, i dislike normal hardware routers because i had a few problems with them before.

I have a 100/100mbit fiberlink and do not want to throttle that because of a cheap "homerouter".

If i want the throughput i need its gonna cost me but if i build my own router it has more power and will hopefully not throttle.

Thnx anyway for your input.

Edit: seems like i found i needed, stumbled upon EnGarde Linux.
It's a linuxrouterdist with LAMP built in =)

[http://engardelinux.org/modules/index/features.cgi](http://engardelinux.org/modules/index/features.cgi)

Might be some more people here who wants this or even has tried it.

---

### Post by devonps on 2008-12-18
> **audreykitching said:**
> If i want the throughput i need its gonna cost me but if i build my own router it has more power and will hopefully not throttle.

It will be your ISP that throttles your bandwidth not your router, either software or hardware.

Good luck with the build.

Steve.

---

### Post by MJN on 2008-12-18
> **devonps said:**
> It will be your ISP that throttles your bandwidth not your router, either software or hardware.Not in the case of a 100/100Mbps connection. Few, if any, boxed 'home routers' would be capable of that sort of LAN-WAN throughput.
 
Mathew

---

### Post by sdnelson on 2008-12-18
True. However, some routers can provide QOS based on IP or MAC addresses. Audrey, try this software.. It's linux based. I will require an old PC and two ethernet cards.

[http://www.devil-linux.org/home/index.php](http://www.devil-linux.org/home/index.php)

---

### Post by audreykitching on 2008-12-18
The EnGarde linux didnt go well :P
Booted a little then Kernel Panic :/

So i guess i need to do this manually anyway.

---

### Post by iponeverything on 2008-12-18
It sounds like you already know how to do everything ;)

for the web server snag apache.

Pop a dhcp server on to your box using apt-get. Google will have you handing out IP's to roomies in about 20 minutes. IP your box as .1 and it will be the default gateway for the others.

edit your rc.local and add:

```

iptables -t nat -A POSTROUTING -s  10.0.0.0/24-j MASQUERADE
echo 1 > /proc/sys/net/ipv4/conf/all/forwarding
exit 0

```

Assuming that the addresses that your handing out are in the 10.0.0.0/24 range.

---

### Post by kustomjs on 2008-12-18
if you looking to do a cheap homemade router just get a old PIII with 512mb memory and 20gb hard drive and 4 nic cards then install smoothwall. then for the webserver I would get something P4 or better with 1GB pr 2GB memory with 160 gb sata hard drive with 1GB nic and install ubuntu 8.10 server edition. my Idea is just for a thought.

---

