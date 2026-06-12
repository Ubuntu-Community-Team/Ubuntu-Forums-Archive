---
title: "Shorewall Configuration"
date: 2007-04-05
forum: Server Platforms
---

### Post by novice1 on 2007-04-05
I have a question regarding the correct configuration for a Shorewall Firewall running behind a Linksys Wireless Router.  I have been retired for about 5 years from working as a computer network engineer. I am quite rusty and firewalls were never my area of expertise. I am building a small home network jus as a hobby. Currently I am attempting to build an Ubuntu server to function as Firewall and post office. I am using Shorewall on purpose since I know its more of a challenge to configure.  But I have yet to get it to route my internet requests to the internet. I know that I do not need a firewall when I am running the Linksys Router as it functions well as a firewall. Never-the-less I am trying to get this set up to work. 

My firewall server has two up and operating NICS eth0 and eth1. Eth0 is configured by DHCP and connects directly to my cable modem and does get an IP address, gateway and DNS configuration just fine. eth1 is Static with a properly assigned IP and mask but not a gateway. From the server I can ping the ISP DHCP assigned IP - but not other Internet IP's. If I configure my desktops gateway to the servers' eth1 IP and ping that IP I get a reply. But I can not get to the internet! From any desktop or from the server itself. Shorewall is configured like this:

Zones:
loc	ipv4
FW	firewall
NET	ipv4


Polices:
$FW	NET	ACCEPT
NET	all	DROP	info
all	all	REJECT	info

Rules:
ACCEPT	loc:192.168.1.0/24	$FW	all

So what am I over looking. My Linsksy Router's  IP is 192.168.1.1 which was the Gateway for all my computers -- but the computers have all been set to the Shorewall IP now.
I tried configuring the Firewall as a Bridge instead of a router but could not get that working either.  Any and all suggestions would be appreciated.

---

### Post by sparky-steve on 2007-04-06
Hiya,

I use shorewall on more than a dozen servers; It's great. Here's a few config pointers; I'll only paste the meat of the config - usually it all gets pasted before the last line in the standard configs.

```

zones:

LAN     LAN     Internal Network
WAN     WAN     Internet
VPN     VPN     VPN Network

```

```

interfaces:

WAN     eth0    -       dhcp
LAN     eth1    detect

```

```

policy:

LAN     WAN     ACCEPT
LAN     $FW     ACCEPT
LAN     LAN     ACCEPT
WAN     LAN     DROP    warning
WAN     $FW     DROP    warning
$FW     LAN     ACCEPT
$FW     WAN     ACCEPT
VPN     LAN     ACCEPT
WAN     WAN     ACCEPT

```

```

Some sample rules:

To open port tcp/143 (imap) on the server/router:
ACCEPT  WAN     $FW     tcp     143

To open port tcp/80 (http) and forward to another computer on the LAN:
DNAT    WAN     LAN:192.168.6.143       tcp     80


```


You've not posted any startup errors, so i'm assuming you've configured the main shorewall.conf file.

Hope this helps; Post back if you need anymore info.

Steve

---

### Post by novice1 on 2007-04-09
Steve:

Thank you for your advice and the information. I have configured my Shorewall exactly as you have suggested  - minus the vpn interface and related policy. I have no rules set and there are no startup errors. From the firewall server I can ping and name resolve both LAN and WAN successfully, however I can not do this from my desktop PC (Window XP Media Edition). I have the desktop IP configuration gateway pointing to the IP of the firewall. I also have my DNS server's gateway pointing to the firewall IP. I still can not browse the internet from my desktop Windows PC - I have not tried my Ubuntu desktop PC as it is a wireless connection and I have to go outside to my workshop to use it - so for now I am only concerned about the wired connections (2 Ubuntu Servers and and the XP pc).  I guess there are non-GUI browsers that could be used from the Shorewall server to test browsing - but I do not know what they are or how to use them. 

I turned off my XP's firewall and the firewall settings in the Linksys Router as well. This did not help at all. I also tried switching the Linksys setting from Gateway to router but that did not help either. Its like the Shorewall server is not allowing any routing between the LAN and the WAN.  I have to reconfigure my network cables and change the gateway information for the effected computers each time I test this out - and then switch back so that I can get to the Internet for information and assistance. I am sure there is some simple thing I am missing - a rule or rules, the Network configuration of the servers/desktop or something of that sort.  As I say I am in no particular hurry as this is just a hobby home network and its for fun not for business. I have learned a lot about Linux by setting these things up -- and I love it. So when you get a chance any further thoughts would be gratefully received. 

\\Chuck

---

