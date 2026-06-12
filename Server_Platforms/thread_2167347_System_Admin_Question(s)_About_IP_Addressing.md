---
title: "System Admin Question(s) About IP Addressing"
date: 2013-08-13
forum: Server Platforms
---

### Post by jiangshi on 2013-08-13
My tiny heterogeneous network consists of four machines including the network server running Ubuntu Server 10.04 headless, a Vista desktop, an Ubuntu desktop, and an XP laptop. IP addresses are currently being assigned by my DSL router/switch using its built-in DHCP server. As I am just getting into the nuts and bolts of Linux server admin, I am concerned about the fact that I am hard-coding IP addresses in some of the network server config files for various server-provided functions. If IP addresses are dynamic, then they can change. I really want to do two things - Is there a way to use names for the host machines in config files, and keep dynamic IP addressing? I am not asking for specific steps, but more about what services/packages/configurations I might want to use to achieve my two goals. Thank you.

---

### Post by TheFu on 2013-08-13
There are a few ways to manage IP addresses.
1) Router firmware that supports DHCP with "reservations"
2) manually by using /etc/hosts and /etc/networking/interfaces (servers). Desktops have a different way to set static IPs. I don't use those.
3) Run a dhcp server "somewhere" on the network and setup reserved IPs for each client. If this isn't your router, then that machine will always need to be on to answer the call.

There you have it.  I do DHCP reservations in my **dd-wrt** running router.  Most router firmwares from the vendor are woefully non-secure, so replacing them with dd-wrt, tomato, open-wrt is a good idea to get more features AND for better security. A router that I own has a known back door added by the vendor - don't want that, right?
[http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) explains more.

---

### Post by jiangshi on 2013-08-13
TheFu, thank you for your answer! My router does have reservations, but I am going to look into your suggestion about dd-wrt.

---

### Post by SeijiSensei on 2013-08-13
Ultimately you may decide to set up a BIND server to provide DNS services to your local network.  Some wifi routers also have software that enables them to become the DNS server for the network.  In this case the router gets the hostname from the client workstation during the DHCP negotiation and creates the IP/hostname pairing in its DNS server.

---

### Post by hawkmage on 2013-08-13
I will second the recommendation to manage your IP addresses through DHCP/BOOTP.  On my home network I use the DHCP server on my firewall (SonicWall NSA series) to configure static DHCP reservations for the systems I have.  I stay away from using DHCP for dynamic addressing on everything except a Guest wireless segment since I want to know who/what is on my network.  The only place I use static IP addresses are my networking gear like switches and firewall since they need to be accessible even if other parts of the network are not.  

I have a pair of Linux based NAS devices that I got root access to that I run BIND on them for DNS on my network.

---

### Post by newbie-user on 2013-08-13
> **jiangshi said:**
> Is there a way to use names for the host machines in config files, and keep dynamic IP addressing? I am not asking for specific steps, but more about what services/packages/configurations I might want to use to achieve my two goals. Thank you.

Yes, you can use hostnames with dynamic ip addresses, but you'll have to set up DHCP and bind for dynamic DNS. Basically what happens is that DHCP updates DNS whenever the IP address of a host changes. Thus you can always refer to computers by their hostname, even if their ip addresses change.

Since you already have an Ubuntu server, why not install bind and isc-dhcp-server? Then you can statically assign IP's from your DHCP config and you won't have to worry about setting up dynamic DNS.

---

### Post by TheFu on 2013-08-14
> **newbie-user said:**
> Yes, you can use hostnames with dynamic ip addresses, but you'll have to set up DHCP and bind for dynamic DNS. Basically what happens is that DHCP updates DNS whenever the IP address of a host changes. Thus you can always refer to computers by their hostname, even if their ip addresses change.

Since you already have an Ubuntu server, why not install bind and isc-dhcp-server? Then you can statically assign IP's from your DHCP config and you won't have to worry about setting up dynamic DNS.

A few opinions.
* running bind (granddaddy DNS server) for a home network is overkill.  Use the built-in solution for your router for DHCP reservations. Most home router firmware is very non-secure. Replace with an alternate firmware if you can. Each of the alternative firmwares has a how-to for static DHCP reservations.
* Bind is a highly-hacked service, so if you do elect to run it, run it in a chroot environment.
* If you run Bind, do not make it available on the internet. A friend is under attack right now because his "follow the how-to Bind" setup wasn't secure.
* Of the two times that I've been hacked, once was through bind. That was the last successful hack against any of my systems ... back in 2002.
* I DO NOT RUN Bind anymore. I pay professionals to run it for my internet properties. With all the changes to DNS recently, I don't have time to stay current. I let the pros handle that for $20/yr.
If you plan to become a DNS expert, then perhaps running a Bind server makes sense. If not, let the telephone people manage the phone book.

Again, just some opinions.

---

### Post by Lars Noodén on 2013-08-14
If you go the dd-wrt route, you can use dnsmasq.  It can be set to assign certain ip numbers to specific machines, insofar as that can ever be done dynamically.  dnsmasq is easy to work with.

---

### Post by jiangshi on 2013-08-14
Some really great answers here, and I thank each of you for your suggestions. I checked the dd-wrt site, but mine is not listed. However, I have some other networking hardware that was given to me, and I will now pay closer attention to what is in that box of stuff. After all, this is all one big experiment to learn about networking and server configurations, at least on a home networking scale. Thank you for all your help!

---

### Post by TheFu on 2013-08-14
> **jiangshi said:**
> Some really great answers here, and I thank each of you for your suggestions. I checked the dd-wrt site, but mine is not listed. However, I have some other networking hardware that was given to me, and I will now pay closer attention to what is in that box of stuff. After all, this is all one big experiment to learn about networking and server configurations, at least on a home networking scale. Thank you for all your help!

dd-wrt, openWRT and tomato are amazing.  For the last 10 yrs, I've always bought hardware that was compatible with these.  They all started out as firmware for the blue WiFi-G Linksys routers that ran Linux. These days, we need to be extremely careful, since there are 10 different sub-models for most routers and not all of them are compatible.  Being listed isn't always enough to ensure an easy install either, so I'd recommend more than just checking that list in your research.  I've been burned, but the results are amazing.
[http://lifehacker.com/344765/turn-your-60-router-into-a-user+friendly-super+router-with-tomato](http://lifehacker.com/344765/turn-your-60-router-into-a-user+friendly-super+router-with-tomato)
[http://lifehacker.com/178132/hack-attack-turn-your-60-router-into-a-600-router](http://lifehacker.com/178132/hack-attack-turn-your-60-router-into-a-600-router)
do a good job of the "why".  Lots of sites talk about the "how" too.

---

