---
title: "Internet Facing, Some advice needed?"
date: 2013-01-23
forum: Server Platforms
---

### Post by chrisguk on 2013-01-23
On my network I have the following:

2 servers, 1 configured as a DNS and the other as NAS.
Desktop PC

Physical machines above connected through cisco switch which is connected to the router.

Laptop (connected directly to the router wireless)

I have been reading this article below about just having 1 server internet facing and the other machines connect to the internet through the server(gateway)

[http://codeghar.wordpress.com/2012/05/02/ubuntu-12-04-ipv4-nat-gateway-and-dhcp-server/]("http://codeghar.wordpress.com/2012/05/02/ubuntu-12-04-ipv4-nat-gateway-and-dhcp-server/")

The problem is the laptop is connected directly to the router via wireless protocol so if I am thinking right it wont be able to connect to the NAS because it will be outside the LAN.

My server by the way does have 2 NICs, its a proliant.

If you can see what I am trying to achieve here any detailed advice will be warmly welcomed.

---

### Post by darkod on 2013-01-23
Is there a specific reason to leave out the router and use one server as router/gateway? Or just to try it?

It can definitely work, I have one ubuntu server configured as router/gateway/firewall for a web server connected to it. But I did it because we needed total control of the firewall and the servers are hosted at a provider.

If you do throw out the wi-fi router you would have to connect the laptop with a cable, or use a wi-fi access point connected to the LAN and create a wi-fi network with it. Sometimes you can use wi-fi routers for this, so you might be able to use your router. Otherwise buying the access point will be an investment you will have to make.

---

### Post by Doug S on 2013-01-23
My home network is connected to internet via my main Ubuntu server. How I handled the wireless devices in my house was to configure my wireless router as a switch on my LAN. So that I could still access its admin/config web pages, I gave it a static IP address outside of the DCHP pool, but on the same sub-net. On my Ubuntu server, I did not have to think about wireless at all, even though several wireless devices are on my LAN. the wireless devices get their IP address from the Ubuntu DHCP server, but do the WEP or WEP2 or whatever stuff on the wireless switch.
Hope this helps.
 
Edit: I was typing when Darko replied. I just want to add, that I do it also because I wanted total control of my firewall / iptables rule set and because I like to study internet traffic and hacking attempts and such. I.E. I am always running tcpdump on my external interface and analyzing what is going on. This may not be the best approach for everybody.
 
Edit 2: Now if by "router" you actually meant "modem/router", then you might still be able to access your NAS via some special iptables rules. Or do as darko suggested and buy another access point.

---

### Post by chrisguk on 2013-01-23
Both of your explanations and advice seem to work well.  I have a different problem though.

I live in Germany and for some reason they think its a good idea to have an integrated hub with phone and broadband services.  In hind sight I think the wireless access point would suit this situation.

Why do I want to do it?

Control over the IP tables etc of course and have more control over the network etc.

---

### Post by darkod on 2013-01-23
And what exactly is the problem? What type of connection (if you know) are you getting from this broadband hub exactly? Is it like PPPoE connection that your modem/router uses and gives you internet?

If it is, and you are worried about that, the server that you connect to the broadband socket can be configured with PPPoE easily.

---

### Post by chrisguk on 2013-01-23
> **darkod said:**
> And what exactly is the problem? What type of connection (if you know) are you getting from this broadband hub exactly? Is it like PPPoE connection that your modem/router uses and gives you internet?

If it is, and you are worried about that, the server that you connect to the broadband socket can be configured with PPPoE easily.


There is no real problem.  The hub has integrated telephony built in so the telephone is connected to it.  I have gone for the wireless access point option and just purchased the hardware.  So my setup will no go like this:

ISP Router/phone hub
Hardware Firewall (old pc)
Cisco Switch - with the following devices connected:

DNS Server - will be the gateway
NAS
Wireless access point
Desktop PC
Laptop Wireless connection

---

### Post by chrisguk on 2013-01-25
I decided to bump this thread because I just need some clarification on the following tutorial:

[http://codeghar.wordpress.com/2012/05/02/ubuntu-12-04-ipv4-nat-gateway-and-dhcp-server/]("http://codeghar.wordpress.com/2012/05/02/ubuntu-12-04-ipv4-nat-gateway-and-dhcp-server/")

I need to clarify that this is the right way to do it and it wont mess my server config up.

Also I would prefer to use Static IPs behind the server as some of the devices are NAS.  Any advice regarding that would be great ?

---

### Post by darkod on 2013-01-25
Looks good to me. If you have specific questions, ask.

If you use all static IPs on the local LAN, you can drop the dhcp server part of the tutorial. But don't forget you will need to assign correct static IP, netmask, gateway and DNS servers to any device on the LAN so that it can have internet access.

Even if you use dhcp for some of the devices, I would always put static IPs that are outside of the dhcp range on NAS devices.

In your previous post where you suggested your setup, you have the firewall as a first device and then the DNS server to be the gateway. Usually the firewall is the first point of entry and is the gateway at the same time.

You can have the DNS on another server, but the gateway would have to be the firewall/router.

---

### Post by chrisguk on 2013-01-25
> **darkod said:**
> Looks good to me. If you have specific questions, ask.

If you use all static IPs on the local LAN, you can drop the dhcp server part of the tutorial. But don't forget you will need to assign correct static IP, netmask, gateway and DNS servers to any device on the LAN so that it can have internet access.

Even if you use dhcp for some of the devices, I would always put static IPs that are outside of the dhcp range on NAS devices.

In your previous post where you suggested your setup, you have the firewall as a first device and then the DNS server to be the gateway. Usually the firewall is the first point of entry and is the gateway at the same time.

You can have the DNS on another server, but the gateway would have to be the firewall/router.

Some great advice there Darkod:

Just to clarify then, my firewall is an old PC and I was gonna run something like IPCOP on it and then have the servers behind that is that what you mean?

The one server is setup for DNS because I have a fully functional webserver running on it and the clients can just browse to any given site by using [http://mysite.home](http://mysite.home) for example.

---

### Post by Doug S on 2013-01-25
If I might just add something...
I use a dhcp server on my local lan, even though I always give out the same IP address to each client, based on MAC. I do that for a few reasons: First, so that I know which client is involved if there is some issue and I am looking at tcpdump traffic or whatever; Second, there are several LapTops and such devices involved, and then they don't have to make any changes when they take them to the office or school or whatever.
Yes, and as mentioned above, I keep my IP address via MAC outside of the dynamic pool of addresses, but on the same sub-net. The dynamic pool is only used for guests and for a new device until I get around to assigning an address via MAC.
I also use a local DNS, so don't always have to remember IP addresses.

---

### Post by darkod on 2013-01-25
I haven't used IPCOP but they are all only frontend for iptables. You can do the same with a core ubuntu server install and iptables rules. However, if IPCOP is more convenient for you, go ahead.

Yes, all servers and clients would be on the LAN behind the firewall/router, and that machine will be their gateway to the internet.

---

