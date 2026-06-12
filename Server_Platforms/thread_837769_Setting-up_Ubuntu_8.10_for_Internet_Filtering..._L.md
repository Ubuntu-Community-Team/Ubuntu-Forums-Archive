---
title: "Setting-up Ubuntu 8.10 for Internet Filtering... Little help?"
date: 2008-06-22
forum: Server Platforms
---

### Post by stevespam on 2008-06-22
Hi All!

I'm really new to Ubuntu, but I'm very attracted to Linux (for very well known reasons), and I'm trying to create/configurate a "Server" for my Small network at work (8 computers).

Basically, what are my needs:
- Somehow have control of internet access at work.
- Whitelist and Blacklist desired URL's.

I'm not looking for Firewalls or any other fancy options in the market let's start with the Basic and the easy ones.

Let me describe what I have right now:

- ADSL internet - this modem is already Routed, not Bridged.
- Linksys Router WRT54G
- One Pentium 4 - 2.8gHZ, 1GB Memmorym 60GB Hard Disk and 3 Ethernet cards (one of them is Onboard, so I'm not using it).
- Ubuntu Server 8.10 (Hard Heron) already set up, with GNOME Desktop.
- Squid + Dansguard installed (but I'm not sure on how to run them).
- Webmin installed, to give the "noobie" here a faster way to set up some features on the Squid and Dansguard (i got those modules installed, so I guess, I can control both softwares at Webmin).

I have a "few" questions to make, but I'd like to start this thread with one very specific... about the "configuration of my physic network".

I'm not sure on how should i put my stuff together in my network to things work properly.

I know that I need to "plug" ADSL first on the Ubuntu Server and use the second ethernet card to "plug" it into the Router. But I'm not sure about on wich router port I should "plug" the server... I mean, my router has 5 slots, named as following:

[ ] INTERNET - [ ] 1 - [ ] 2 - [ ] 3 - [ ] 4

On my tests, Ubuntu with direct connection to my ADSL modem is already surfing the internet, but when i try to connect the server into the router, the other computers can't access the internet... i mean, ubuntu server doesn't even pings the router.

Here's a couple of questions:

- Should UBUNTU be DHCP Server?
- Should I let the router to be DHCP server?

Am I thinking right?
Because I'm trying to do this:

[ADSL MODEM ] ---> [UBUNTU SERVER] ---> [LINKSYS WRT54G ROUTER] ---> [NETWORK CLIENTS]

Thanks all!
Sorry if some questions seems too obvious, but I'm really new into this.

Thanks in advance!

---

### Post by cariboo on 2008-06-23
Why not let the router do all the work, it has all the software in place to do what you are looking for. in other words go with what you know. The only reason I could see you using the server to do the same  thing is if you are planning to get rid of the router, or as a backup if the router ever fails. 

Jim

---

### Post by Aearenda on 2008-06-23
This is really quite an advanced use of Ubuntu. What I would do is:
[ADSL MODEM ] ---> [UBUNTU SERVER] ---> [SWITCH] ---> [NETWORK CLIENTS]
You don't need a router at the point in the network where you have it.

Or, better, this:
[ADSL MODEM ] ---> [LINKSYS WRT54G ROUTER] ---> [UBUNTU SERVER] ---> [SWITCH] ---> [NETWORK CLIENTS]
Which would give you an extra level of protection from the Internet, assuming your router has a firewall, or at least NAT.

On Ubuntu, with Squid and Dansguardian installed, I would do this:
1. Make Ubuntu the DHCP server for the local network - using a static address on eth1 for the local net, and DNSMasq for DHCP and DNS, configured to use the upstream DNS service for referrals, and an appropriate IP range on downstream such as 192.168.123.0/24. Don't use 192.168.0.x, since that is very common and causes difficulty later if you ever want to use VPNs and so on. 

2. Turn on packet forwarding on Ubuntu:
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
This needs to be made permanent, e.g. by adding it to /etc/rc.local - or uncomment the appropriate line in /etc/sysctl.conf.

3. Start Masquerading in Ubuntu (=NAT)
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```
This assumes eth0 is the upstream interface, and eth1 is attached to the switch. This allows your downstream workstations to use non-routeable addresses.

At this point, your workstations should be able to connect to the internet. 

4. To add Squid in to the mix, you need transparent proxying:
```
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 3128
```
This forces all http traffic to go via Squid. Make sure this works by looking at the access logs for Squid in /var/log/squid. Squid starts at boot, you don't have to start it.

5. Now add Dansguardian - it needs to be configured to use squid for its internet calls, and you need to modify the previous iptables command to read:
```
iptables -t nat -A PREROUTING i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080
```
since Dansguardian listens on port 8080 by default.
Check this works by looking at /var/log/dansguardian/access.log when workstations access websites. Make sure it blocks what you want by going to a few safe-ish 'bad' sites. DG starts automatically too.


Note that all the commands given here need to executed by root, and again, to be made permanent by need to be in /etc/rc.tables or in a script that is called when eth1 comes up.

Also, I haven't added any defensive stuff against intrusion from upstream; there are many howtos around that tell how to do that, and I'm no expert. What I am showing here is the upshot of hours of looking at howtos etc, and the resulting configuration in 3 installations, all of which go through a hardware firewall/router first.

Having said all that, why don't you use something like Smoothwall Express with a Dansguardian add-in? It's designed for this job.


Finally, on your router, the [INTERNET] port expects to be the upstream connection. In your scenario, Ubuntu should be connected to that socket, and the workstations would go on the other sockets. But, as I said, that's a waste of a router really - all you need there is a switch.

---

### Post by hyper_ch on 2008-06-23
maybe somethign like this (but I guess it's overkill): [http://www.howtoforge.com/ubuntu6.10_firewall_gateway](http://www.howtoforge.com/ubuntu6.10_firewall_gateway)

or something like this:  [http://www.howtoforge.com/perfect_linux_firewall_ipcop](http://www.howtoforge.com/perfect_linux_firewall_ipcop)

---

### Post by stevespam on 2008-06-23
First, I'd like to thank all the replies untill now.
Now, let me write my comments...

> Why not let the router do all the work, it has all the software in place to do what you are looking for. in other words go with what you know. The only reason I could see you using the server to do the same thing is if you are planning to get rid of the router, or as a backup if the router ever fails.

Jim

JIM,

Hi Jim, I wouldn't use only the router, because it's firmware (even the latest ones) can't give me advanced settings. I mean, or I block the entire internet for all users or don't... I can't specify  things like "alowing only websurfing for desired websites", I would have to block the "entire internet" except the ones I'd like people to have access to it... somehow, LINKSYS routers doesn't have a very nice Internet Filtering. You got a very interesting point when you say "stay with what you know", it really makes sense, but since UBUNTU is an amazing Linux Distro (and Free of Charge) and I had an "old-spare" computer at office I thinked: Why not give a try and expand some knowledge? hehehe.

====================================================

> This is really quite an advanced use of Ubuntu. What I would do is:
[ADSL MODEM ] ---> [UBUNTU SERVER] ---> [SWITCH] ---> [NETWORK CLIENTS]
You don't need a router at the point in the network where you have it.

Or, better, this:
[ADSL MODEM ] ---> [LINKSYS WRT54G ROUTER] ---> [UBUNTU SERVER] ---> [SWITCH] ---> [NETWORK CLIENTS]
Which would give you an extra level of protection from the Internet, assuming your router has a firewall, or at least NAT.
...


AEARENDA,

Thanks! Your reply is the best detailed one so far. You helped me understand that if I have a Ubunto Server running I don't actually need a Router, a simple Switch would do the Job. Simple information like, plug the Ubuntu Server cable on the [INTERNET] socket at my Router is very appreciated also (beside being obvious, but it wasn't for me until now).

I'll follow all the steps you described to me later (when I get some spare time at the office) and I'll let you guys know how did I suceeded or not.

I think even that I had Ubuntu "ready to go" I would still have somekind of conflict, because there would be 2 hardwares trying to do the same task, Routing... Hope it's possible to keep the ROUTER, since it's the best option I have to share the internet over wireless (all clients computers are Wireless) and give access to our ERP (hosted at a Windows Machine) system to all users... besides, we don't have a Wireless Switch and don't plan to spend some money (even though they are pretty cheap) on them.

====================================================

> maybe somethign like this (but I guess it's overkill): [http://www.howtoforge.com/ubuntu6.10_firewall_gateway](http://www.howtoforge.com/ubuntu6.10_firewall_gateway)

or something like this: [http://www.howtoforge.com/perfect_linux_firewall_ipcop](http://www.howtoforge.com/perfect_linux_firewall_ipcop)


HYPER_CH,

Great Howto, very detailed ones you provided me. I've read many howto's found over the internet but I must admit that none of them were too clear for "linux newbies" like me. The first link you gave me: [http://www.howtoforge.com/ubuntu6.10_firewall_gateway](http://www.howtoforge.com/ubuntu6.10_firewall_gateway) seems to be very detailed. I guess that reading this one and using a few tips from Aearenda I might succedd in this small "quest".

====================================================

Now I'd like to thank you all for your kind support.
Haven't mentioned this, (I don't even think this might be interesting to anyone) but I'm not a sysadmin for living, but I'm really into this and assuming that I'm the "most expertised" in this at my job (a small business office) I'm in charge of setting up the network, printers, internet, router, etc... lol. Knowledge can't be considered too much, so I'm here willing to learn and maybe someday, be able to help others just like you guys are doing.

Thanks Once again!

PS: This thread isn't closed yet, I'll keep you guys "updated" about my progress and I'd appreciate a lot if you could guide me untill I've reached my goal... to set up a small network internet control.

---

### Post by stevespam on 2008-06-23
One more question:

Assuming (reading the replies and checking other web howto's) that If i want to set up a Ubuntu Server to my small-network, I'll have to "get rid" of my actual Router (Linksys WRT54G) and acquire a new SWITCH. Because the combo [SERVER]+[SWITCH] is the basic hardware to set up this...

Is it possible to "transform" my Router in a SWITCH?
I mean, if I turn off features such as DHCP SERVER, FIREWALL, NAT, etc... will it act like a SWITCH and fill up my needs?

Please, don't "flame" me if this questions seems too dumb? :lolflag:

Thanks!

---

### Post by hyper_ch on 2008-06-23
No, you don't have to get rid of your router, just set it up as really, really permissive ;) What model of the wrt54g do you actually have? You may want to replace the default firmware with another one (I like tomato wrt meanwhile a lot).

---

### Post by Aearenda on 2008-06-23
Ah, didn't know about the wireless bit - so yes, you need that wireless box 'downstream' from the Ubuntu system. Some wireless routers can be made to work as a straightforward wireless access point (= a "wireless switch"). Even if it can't, and must be a router, it will work so long as Ubuntu is 'upstream' from it - in the Internet socket. I don't know that model so go with what hyper_ch is saying for more detail.

I still wonder whether you should be using a specialised distro such as IPCOP or Smoothwall for this job... they are free too.

---

### Post by stevespam on 2008-06-23
Well, I guess what "distro" i should use is not my primary concern. At least, it shouldn't.

I've checked the IPCOP before and at first sight it does meet my needs way more easy and quick than Ubuntu. I've saw it before, but didn't paid much attention. Thanks Aearenda for the usefull indication.

Right now, I need to know if my actual ROUTER (Linksys WRT54G) will be able to "act" like a switch, by "downstreaming" as the user Cariboo suggested... when you guys say "Downstream" my router, you mean to "turn off" features as DHCP Server, IP-Routing, Internet Connection, etc...?

Another question:
All "firmware" internet filtering (like Tomato) they are able to block internet entirely or a few domains... but they don't give the option to Block Everything unless exceptions. Basically I only need a list where I should provide the URL's that can be accessed, and if it's not on the list, it won't open.

And yes, I need to let "internet filtering" turned off for a few computers only, but this can be done by adding the MAC Address of the desired clients.

Careboo asked me, what's my version of WRT54G, i guess it's Version 5 (yes, I know, not the best one), but I'll check it for more accurate information... it's attached "above our heads" here in our main office... so, I'll need to ask for a ladder to see it.

Thanks once again!

---

### Post by Aearenda on 2008-06-23
I had a look at IPCop yesterday, since I am soon to upgrade a system that uses Smoothwall Express 2.0 with Dansguardian, and wanted to be sure going to Smoothwall Express 3.0 was better than going to IPCop. It seems to me that there is more community support for Smoothwall than for IPCop as far as DG is concerned - but maybe I just didn't dig deep enough.

If all you need is white/blacklisting, and no content filtering, you could perhaps use Squidguard instead of Dansguardian.

I have used the terms 'upstream' and 'downstream' frequently in my posts - 'upstream' simply means 'nearer the internet' and 'downstream' means 'nearer the workstations'.

Some wireless routers do have the ability to disable DHCP, NAT, routing, etc so that they act like a wireless access point. This would be useful in your scenario. On my router that does this, the 'Internet' socket becomes unused, and the server cable is plugged in to one of the four 'normal' sockets instead - exactly as if it was a switch.

---

### Post by stevespam on 2008-06-23
Aearenda, thanks once again for your reply and clean and detailed explanation :)

I'll try to follow your advices, since I already got Ubuntu 8.10 installed an running already, I'll give a chance with SquidGuard.
And I'll look to set up the router as a simple siwtch (Linksys WRT54G is cabaple of disabling NAT, DHCP, etc...).

If everything goes Ok (and if doesn't) I'll let you guys now. And I'll post a "resumee" of what I've done, it might be usefull to other users, just like me and save some time from users like you.

Thanks!

---

### Post by cariboo on 2008-06-24
If you are going to set things up the way you said. If you want to get your hands really dirty have a look at arnos-iptables-firewall, There is now a script included to do the basic setup, but if you want to take full advantage of its features you will need to do some manual config. I used it for quite a few years and once it was set, you could forget about it.

Arnos-iptable-firewall is available in the repositories and you can use synaptic to install it.

Jim

---

