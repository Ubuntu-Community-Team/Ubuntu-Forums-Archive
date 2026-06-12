---
title: "Use old PC as a firewall?"
date: 2020-03-23
forum: Security
---

### Post by deluxe180 on 2020-03-23
Hi,
 
I have a reoccurring problem with my ISPs router/modem.  Some *bleep* keeps crashing it not sure what exactly they are doing as it does not have a firewall log.
 
But I am a 100% sure that is the case.
 
I have an older PC if I installed Ubuntu Server or other distro and connected everything to the internet via the Server so….
 
ISP Router -> Ubuntu server -> My PC
 
Would I be able to set up a firewall with the server to protect the router or is this not possible with a home setup? Or because the first point of entry is the router would server be behind the router?
 
If it possible could i have some advice?
 
Thank you!

---

### Post by EuclideanCoffee on 2020-03-23
Your assumption that this wouldn't work because the server is behind the router is correct.

Recommended reading: [https://openwrt.org/](https://openwrt.org/)

Sorry that some *bleep* is hazing you. :)

I'll leave this here in the case you ever thought about developing some investigation skills.

[https://trustfoundry.net/honeypi-easy-honeypot-raspberry-pi/](https://trustfoundry.net/honeypi-easy-honeypot-raspberry-pi/)

---

### Post by deluxe180 on 2020-04-08
> **EuclideanCoffee said:**
> Your assumption that this wouldn't work because the server is behind the router is correct.

Recommended reading: [https://openwrt.org/](https://openwrt.org/)

Sorry that some *bleep* is hazing you. :)

I'll leave this here in the case you ever thought about developing some investigation skills.

[https://trustfoundry.net/honeypi-easy-honeypot-raspberry-pi/](https://trustfoundry.net/honeypi-easy-honeypot-raspberry-pi/)

hi,

thx for the advice..

do you know if i got my isp to change my ip and i used a vpn with a strong firewall would that protect the router?

thx

---

### Post by EuclideanCoffee on 2020-04-08
Combining a decent router with an application firewall for your primary computer may be enough.

Routers:
[https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux](https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux)

[https://help.ubuntu.com/lts/serverguide/firewall.html](https://help.ubuntu.com/lts/serverguide/firewall.html)

---

### Post by deluxe180 on 2020-04-08
> **EuclideanCoffee said:**
> Combining a decent router with an application firewall for your primary computer may be enough.

Routers:
[https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux](https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux)

[https://help.ubuntu.com/lts/serverguide/firewall.html](https://help.ubuntu.com/lts/serverguide/firewall.html)

hi,

i dont really have that option i have to use my isps modem at least in modem mode, its part the their tos. even going that and having a third party router does not stop the problem.

so do you think that a vpn with a firewall may help the issue?

also do you know will any fibre (dsl) capable modem / router work on a cable docsis connection?

thx

---

### Post by TheFu on 2020-04-08
if the isp's equipment is failing, call them, have it replaced.  it isn't your problem.  Use the consumer protection laws for your country/province.  Take careful notes for every time you call, everything they say, who does what, when, until it is resolved.

if the normal team fails, contact the office of the president for the isp with a reasonable letter. Briefly state the issue. What has been attempted to correct it and what you'd like.  Be reasonable.  And be brief.

A modem that is failing for any reason is unacceptable.  That has to be corrected first.

DSL is different from fibre and both those are different from DOCSiS.

---

### Post by EuclideanCoffee on 2020-04-09
Before you can blame the ISP or some hacker, you'd need evidence that this is the case and not simply a protocol crashing the router with a flood of packages due to the faulty protocol. Certain NIC cards have the reputation to do this, but there is little on how this occurs.

It's also very possible you have malware that is causing the problem.

---

### Post by The Cog on 2020-04-09
It might be something like this: [https://arstechnica.com/information-technology/2020/04/meet-dark_nexus-quite-possibly-the-most-potent-iot-botnet-ever/](https://arstechnica.com/information-technology/2020/04/meet-dark_nexus-quite-possibly-the-most-potent-iot-botnet-ever/)
in which case it's coming in from outside. All you can do is make sure the password is hard, and if possible disable admin access to the router from the internet. And maybe ask your ISP to update or replace the router.

---

### Post by EuclideanCoffee on 2020-04-09
If you are a target for a botnet, there is not much you can do with your ISP to protect you. The ISP should already have controls to block bot nets. If it's the case, I would go with a new ISP, which will provide you with a new IP and equipment anyways.

Bot nets typically want to break into to stuff, not permanently take the down or DDOS them unless for a temporarily amount of time. Attacks like this are easily blocked long term, but they are costly because when they're done against large corporations, the corporations lose money per minute, sometimes millions of dollars per minute.

If someone is intentionally doing this to you, you would've heard from them by now. There aren't many people in the world willing to commit a crime for fun.

---

### Post by kevdog on 2020-04-11
Just some thoughts you ponder.

I like you are trying to make use of your PC and repurpose it.  If you can put your ISP's device into bridge mode, then what you want to do is possible.  You can use Ubuntu for this purpose if you want, but there are specialized distributions such as pfSense which sole purpose is to act as a router and firewall.  I would highly advise you first start with such a distribution since firewall management is very tricky.

In terms of what's crashing your internet or modem, it's honestly very hard to know.  You haven't posted enough information for us to make any decisions.

---

