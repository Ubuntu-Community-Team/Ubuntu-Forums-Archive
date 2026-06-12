---
title: "Help with Ubuntu Server setup"
date: 2013-01-17
forum: Server Platforms
---

### Post by Basurci on 2013-01-17
Hello everyone , my problem is that I don't know how to setup one so I could use it remotely from school.
I did everything what installation guide said but I still can't connect (It shows LAN IP that goes 192.168.0.x)
So maybe someone can help me with this? I'd like to have it with Domain name that i bought long time ago or with No-ip.org name or with IP that it gets (random numbers that router generates).

---

### Post by soundsfromsound on 2013-01-17
Can you tell us what you setup? So you have an Ubuntu Server at your home that you wish to access from outside the LAN? (i.e. school)

Please confirm.

---

### Post by papibe on 2013-01-17
Hi Basurci.

There are several steps to accomplish that.

If you're unfamiliar with that concepts mention below, take a look at this is a very helpul [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

This would be the main steps:
[LIST]
[*]Set your server with a LAN static IP.
[*]Install openssh-server on your server.
[*]Test LAN ssh access to your server.
[*]Optional: change the standar ssh port (22) to a different, preferable higher value.
[*]Subscribe to a Dynamic DNS service. There are free and pay options. For example: DynDNS, no-ip, zoneedit, etc (check [here]("http://dnslookup.me/dynamic-dns/") for a longer list).
[*]Either install and setup the package ddclient, or (better if available) set your DDNS client in your router.
[*]Forward the ssh port in your router to your server.
[/LIST]
Now you are ready to test accessing your server over the internet.

Important: do not try to access your server using its public IP, or dynamic name from inside your own LAN. The proper way to test access is from outside your network. For example, an internet café, public library, a friend house, or using your phone or tablet's 3G service (be sure to NOT being connected to your LAN's WiFi though).

I hope that points you in the right direction, and tell us how it goes.
Regards.

---

### Post by Basurci on 2013-01-19
Well it seems that I won't be able to access my computer from outside because of "Set your server with a LAN static IP." I'm using router and "server" is connected to it not directly to WAN. (Router D-link Dir-615)

---

### Post by lisati on 2013-01-19
> **Basurci said:**
> Well it seems that I won't be able to access my computer from outside because of "Set your server with a LAN static IP." I'm using router and "server" is connected to it not directly to WAN. (Router D-link Dir-615)

The setting of a static IP on your LAN is only a starting point. The reason I would recommend taking care of this and getting it working *before* worrying about a WAN connection is to make the task of directing connections from the WAN to your server (e.g. port forwarding) easier.

---

### Post by papibe on 2013-01-19
> **Basurci said:**
> Well it seems that I won't be able to access my computer from outside because of "Set your server with a LAN static IP." I'm using router and "server" is connected to it not directly to WAN...

That is actually my set up, and also, the most common configuration for a typical household. It does not limit the ability to connect to your home server from outside (school for instance).

BTW, AFAIK, you can't set a static IP, or reservation on that particular router. What you need to do is define it in the server itself. Just make sure the address you choose is outside the DHCP range (found in the router).

Let us know how it goes.
Regards.

---

### Post by Basurci on 2013-01-24
Hello again.
SO i checked my DHCP IP range it's from 192.168.0.100 to 192.168.0.199.
I did setup my "home server" with static Lan IP (ADD/EDIT DHCP RESERVATION option in router) that is 192.168.0.101 , I did portfoward on router too (used google for ports) but I still can't connect to server.

---

### Post by papibe on 2013-01-24
I'd gladly continue offer you more directions, but I'm afraid I'm going to need more details.
[LIST]
[*]What service are you trying to access on your server?
[*]Does accessing the service work from a client connected locally to the LAN?
[*]Which port did you forward to the server?
[*]Could you post the error messages you are getting while trying to access the server?
[/LIST]
Regards.

---

