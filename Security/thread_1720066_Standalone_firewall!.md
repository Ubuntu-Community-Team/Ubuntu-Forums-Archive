---
title: "Standalone firewall!"
date: 2011-04-02
forum: Security
---

### Post by Fr33K1e on 2011-04-02
After having a wonder round on the net today and viewing a few video's on youtube I came across something about running an old pc as a firewall and using Smoothwall express.

on my network at home I have 2 windows PC's and 2 Ubuntu PC's and I have a spare PC collecting dust (which could be used for the firewall).

My question is this...

Would it actually be worth while setting up a hardware firewall?

---

### Post by BkkBonanza on 2011-04-02
Maybe if your net facing router isn't very adequate, or if you have other things you want to run as well. But in a typical home situation, given you already have a router that should have a firewall, I don't see it as being that useful. It will mostly just cost you more money/month for electricity and just filter what your normal router should already have done.

---

### Post by handy on 2011-04-03
I agree with BkkBonanza, he IS absolutely correct.

That said, I've been running a headless IPCop box - a PIII 700Mhz, 256MB RAM & 20GB HDD (used to be 2GB but it died) for over 2 years now.

IPCop is easy to install & setup (via client side browser interface), reliable & secure, has add-ons available for it. Though as all firewall/routers should be, it is limited as to just what you can do with it due to security, security & security.

You *can* pick up noticeable speed increases using a Linux based router, as the common adsl modem/routers that people buy are basically Windows centric & therefore don't handle IP packets as efficiently as Linux does. You also may notice no difference in speed whatsoever...

@ 19.2 cents/Oz /kW , it costs me $53-/year to run. I tested it over a period of weeks so I know it was an accurate figure.

We run profitably on PV solar panels, so we're a bit different than most in that regard.

---

### Post by Fr33K1e on 2011-04-04
I have a linksys wag54gs and when i checked to see if the firewall was enabled neither enable or disable were marked and when i selected enable and saved it, when the page reloaded it reverted back to having none of them marked!

---

### Post by fela on 2011-04-04
> **handy said:**
> We run profitably on PV solar panels, so we're a bit different than most in that regard.

I wish there were more people like you in the world.

OP: stick with your router, unless it's for the thrill of running a custom setup ;)

---

### Post by gallaau on 2011-04-04
The router will most likely allow any outbound connection from your machine or machines. Inbound it will do most of the filtering based on PAT, Port Address Translation. So if you did not initiate the connection outbound, it has no idea what machine to send the connection to inbound, therefore it is dropped.

So lets say you external address is 208.2.4.6
and you PC or PCs on the inside are 192.168.1.100 and 192.168.1.101

Now someone on the internet tries to attack your machine. Lets say it is windows and this guy is going to try a dictionary attack on you for remote desktop. So he sends yo a TCP connection on port 3389. Now you router gets the packet and tries to forward it, but how will it know what machine he wants? is it .100 or .101 so it gets dropped.

The firewall would prevent you machine from outbound connections on any TCP/UDP port or IP address that you did not allow.
So if an intruder did get in, he would only have outbound access to say 80 or 443, whatever you configured. Of course he will use port 80 cause he knows it is open.

You could put a special machine on your network that is behind a firewall and is only allowed to talk to a specific DNS server, your bank or credit card company on specific ports and only powered up when needed. That is by far the best for security at home. 

If you want me to babel any more just ask :)

---

### Post by Fr33K1e on 2011-04-05
> **gallaau said:**
> The router will most likely allow any outbound connection from your machine or machines. Inbound it will do most of the filtering based on PAT, Port Address Translation. So if you did not initiate the connection outbound, it has no idea what machine to send the connection to inbound, therefore it is dropped.

So lets say you external address is 208.2.4.6
and you PC or PCs on the inside are 192.168.1.100 and 192.168.1.101

Now someone on the internet tries to attack your machine. Lets say it is windows and this guy is going to try a dictionary attack on you for remote desktop. So he sends yo a TCP connection on port 3389. Now you router gets the packet and tries to forward it, but how will it know what machine he wants? is it .100 or .101 so it gets dropped.

The firewall would prevent you machine from outbound connections on any TCP/UDP port or IP address that you did not allow.
So if an intruder did get in, he would only have outbound access to say 80 or 443, whatever you configured. Of course he will use port 80 cause he knows it is open.

You could put a special machine on your network that is behind a firewall and is only allowed to talk to a specific DNS server, your bank or credit card company on specific ports and only powered up when needed. That is by far the best for security at home. 

If you want me to babel any more just ask :)

Please continue...

---

