---
title: "Internet Sharing"
date: 2009-02-01
forum: Server Platforms
---

### Post by Dark_Fire on 2009-02-01
I just moved into a commune and we are about 20 - 50 people who would want internet.

I was thinking of setting up a wireless network and buy one ADSL line and account and sell it to the other guys.

So I want a server that will share the internet. Also it must give everyone an account which will monitor the amount of internet they use so I can give them a limit, eg 1GB cap. Also a cache server that would help me save some bw by reading images and things like that from the server instead of downloading it again.

I live in South Africa so our connection speeds are really slow in comparison to other contries. Also we are limited to a certain ammount of downloads a month. So you buy a cap like a 1GB or in my case a 10GB. Uncapped is really expensive. Thats why I want as much software to help me overcome this problem.

Im not sure if I should use Ubuntu Server or what as I have never worked on a server platform before.

Any help would be greatly appreciated.

Thanks in adcance.

Dark_Fire

---

### Post by TenPlus1 on 2009-02-01
Installing Firestarter from the Synaptic Package Manager will give you a nice firewall tool that has an Internet Sharing option...  From there it's up to you to make your main Internet Computer the HUB wit ha static IP (192.168.0.1) and point the rest to that as the gateway...

This might help: [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by Dark_Fire on 2009-02-01
Thanks for the reply.

Does this have a cache server too? Can I create "internet accounts" on it and monitor their usage and cut off their internet when a certain ammount of bandwidth is exceded? I would also like to block certain sites and be able to monitor what they access if that is possible, but thats an extra feature thats not heigh on my list.

Or can it only share internet?

Thanks once again

---

### Post by sanemanmad on 2009-02-01
Hey I am running a wireless accesspoint with DHCP/DNS and Squid proxy server to accomplish the same concept. ( I have multiple gamers and also share my internet with other family members who live close by (within 100yards).

1. DHCP server to control the pc's that connect and much more (place users in subnets based on MAC address etc...)

2. DNS - hand in hand with DHCP

3. Squid - Caches internet usage and helps increase bandwidth.

4. There are a few programs, but squid, along with extra modules will allow for a cap.

I use various reports to oversee the usage etc... which can all be automated and e-mailed. Possibilities are endless.

Firestarter may be nice... But I am all about DIY :P

Let me know if you need some help setting this up.

You can see the specs for my server in my signature... My average load usage is 00:00:00 :)

---

### Post by sanemanmad on 2009-02-01
[Squid Proxy Server]("http://www.squid-cache.org/Misc/related-software.dyn")

[DHCP Server]("http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html")

These are some good references

---

### Post by Dark_Fire on 2009-02-02
This seems to be what im looking for. Im going to set up a PC with the new Ubuntu Server asap and then try to set everything up.

Thanks allot for your help. :)

---

### Post by koenn on 2009-02-02
I suggest you install dnsmasq in stead of bind + dhcpd. dnsmasq offers both dns and dhcp, is simple to set up, and can do everything you need for a small network like yours requires. And because it combines dns and dhcp, it can automatically do a lot of things that otherwise you'd have to configure by hand. 

if the only service you're going to offer is web browsing (or anything squid can proxy for), you can use the proxy to share the internet connection. Otherwise, you'll need iptables to actually share the internet connection.

if you use iptables to share your internet connection, you may want to prevent your users from bypassing the proxy/cache, or everything that depends on it (bandwidth savings, monitoring, content filtering and access control, billing, ...) is also bypassed. So you'll need additional firewall (iptables) rules to implement that. You might also consider automatic proxy discovery or a 'transparent proxy' configuration.

---

### Post by sanemanmad on 2009-02-02
Very true, I also considered using dnsmasq, but i do not believe it is capable of dns updates for the hosts? anyway mine is setup identical (almost) as this fella's

[Ubuntu at it's best]("http://www.wyckedone.net/2008-01-01/the-ubuntu-home-server/")

So basically this is how it works, a device connects and soon thereafter my dns records are updated with their local IP address. Works for me since I do remote backups for most of the hosts, (my network is much smaller, but growing :P ),

As far as squid goes, > You might also consider automatic proxy discovery or a 'transparent proxy' configuration.
 yes. koenn is also right, you will need a combo of iptables to accomplish this which isnt difficult to setup. (it's really only 2 lines, aside from basic rules)

---

### Post by koenn on 2009-02-03
> **sanemanmad said:**
> Very true, I also considered using dnsmasq, but i do not believe it is capable of dns updates for the hosts? anyway mine is setup identical (almost) as this fella's

dnsmasq's dns will let you lookup host addresses for hosts that its dhcp server assigned an address lease to, provided the hosts announced their name during the dhcp discover/request. Windows hosts do this by default, some linux distro's also, and with some other linuxes, you have to configure the dhcp client to send the hostname.

for non-dhcp hosts, dnsmasq reads the /etc/hosts file of the machine it's running on, so if you keep that updated with the static addresses on your network, dnsmasq knows your entire network. For hosts outside the network, it will query a dns server from /etc/resolv.conf (and cache the results).

---

