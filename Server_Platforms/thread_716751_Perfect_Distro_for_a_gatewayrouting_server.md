---
title: "Perfect Distro for a gateway/routing server"
date: 2008-03-06
forum: Server Platforms
---

### Post by ulver on 2008-03-06
I have a private internal network with two seperate internet connections and i want to setup a server that would act as a gateway/firewall with NAT&PAT  and enable NIC bonding on it. 

Now I need your much appriciated help on three questions.

What would be the perfect distro for this problem? Some network/security oriented one please.

Is there any open source solution which I could implement on that gateway server that would monitor user bandwidth consumption from the internal network and slow their speed if they reach a certain limit?

The two internet connections are ADSL and cable, ADSL has a max limit of 9GB and cable has a limit of 12GB. Is it possible with or without NIC bonding to setup the server so it has load balancing but doesn`t use each connection over its limit?

Any suggestions are welcome, ty

---

### Post by cheapstyle on 2008-03-06
DId you have a look a pfsense?

[www.pfsense.org](www.pfsense.org)

It can at least do the nic bonding.

---

### Post by FakeOutdoorsman on 2008-03-06
BSD is often used for firewalling at least.  I'm not sure if these have all of the features you would like, but also check out: [m0n0wall]("http://m0n0.ch/wall/") (pfsense forked from m0n0wall), [SmoothWall]("http://smoothwall.org/"), and of course [OpenBSD]("http://www.openbsd.org/") or [FreeBSD]("http://www.freebsd.org/").

---

### Post by koenn on 2008-03-06
Debian.
It's a general purpose distro, but rock solid, and with a huge software collection you can use for your requirements beyoud routing and firewalling. 
If you do a custom install and install no additional software during initial setup, you end up with a basic 250 MB installation to which you can add whatever you need, eg
* iptables for firewall
* dnsmasq or bind as a caching DNS + forwarder (so your LAN hosts don't need to access the internet for DNS - simplifies firewall rules & strenghtens security
* web proxy (eg squid) - same reasoning as for DNS cache + saves bandwith and allows granular web filtering / access control
* other proxies (for the same reasons as above) - e.g. apt-proxy, ...

* nagios - extensive network monitoring - probably has something to monitor bandwith usage

* iptables can do some traffic shaping / bandwith throttling - but there may other software specifically designed for this task

* you can probably work out some static routing to use both internet connections, and have one as a fail-over for the orher. 
[http://en.wikipedia.org/wiki/Virtual_Router_Redundancy_Protocol](http://en.wikipedia.org/wiki/Virtual_Router_Redundancy_Protocol) may be also something you want to try. 
Alternatively, installing a routing protocol such as BGP might be usefull to use both routes without any static configuration. 
However, making routing / network access / ... aware of arbitrary values such as maximum volumes per month is going to be hard. I'm not aware of any application that handles such thing.

---

### Post by chris.zeman on 2008-03-10
Take a look at BrazilFW [http://brazilfw.com.br]("http://brazilfw.com.br"). This is exactly what you're looking for if all you're looking for is a router/firewall that just works.

I've tried a number of router/firwall distros and always ended up back at BrazilFW. It handles both of my internet connections with minimum configuration and does it well!

Chris

---

### Post by jonabyte on 2008-03-10
I use IPCOP at work and have had no problems with it.

[http://ipcop.org/]("http://ipcop.org/")

---

### Post by Brazen on 2008-03-10
I like all my servers to be Ubuntu, just to keep things simple, however for a firewall/router appliance, I like pfsense or would also use ipcop if I wanted extra features and maturity.

---

### Post by netlogic on 2008-03-10
If you don't need a wireless adapter that supports WPA and WPA2 on your firewall for your wireless devices or if you already have a wireless router (configure as a bridge mode), get Monowall and use CF to IDE converter to boot the system. You can make a fanless system that way. The cost is around $6. You can easily find it on Ebay. I believe Monowall is a 16meg image. 64meg CF card is only $5.  If you need WPA and WPA2, get Pfsense. You will need least 1 gig drive. PFsense has more features. If you need Antivirus and Malware plugins to protect Windows box, get IPCOP.

---

### Post by chris.zeman on 2008-03-10
> **netlogic said:**
> There is a simple rule for choosing an OS. Linux is harder to setup than Windows, but once you got things running, it will stay running. Setting up a Winbox is simple, but keeping it running requires precise surgeon's hands.

Love that sig! lol

---

### Post by ulver on 2008-03-11
Thank you for your insightful replys, I dont know now what to try first, but I`ll think I go with IPCop or pfSense.

---

### Post by chris.zeman on 2008-03-11
If choosing IPCop or pfSense, go with pfSense as it supports MultiWAN (which I believe was one of your requirements). Last I checked (a couple months ago), IPCop did not. That was THE reason I went with BrazilFW rather than IPCop.

Good luck!
Chris

---

