---
title: "Questions about IP assignment (and DHCPD)"
date: 2006-06-23
forum: Server Platforms
---

### Post by Kurt` on 2006-06-23
Hi,

Before I delve into my problem, here is my desired network setup:

[img]http://xs102.xs.to/xs102/06256/network-diagram.png[/img]

I want this setup so that I can keep clients coming in over wireless from being able to access anything but the internet, keep unwanted traffic (e.g. scans/probes from taiwan, china, brazil, etc.) from entering my network at all, and things like that.

The 'Router machine' (Ubuntu server) will run nothing but DHCPD and BIND9 (and iptables or another firewall).

Now to my problem. :)

If I plug a Windows machine **directly** into my cable modem and activate its "LAN connection", it receives my normal IP address from my ISP via DHCP. This is desirable.

When I plug the 'Router machine' **directly** into the cable modem and turn it on, it sends out a ton of DHCPDISCOVERs, then fails to bring up the interface.

How should I go about debugging this? I would prefer to receive the IP address from my ISP via DHCP. On occasion (every 6 months or so), my ISP assigns me a different address.

I will probably have some questions about DHCPD and the 5 possible interfaces it can use, so I figured I'd title this thread accordingly. ^^

---

### Post by Ptero-4 on 2006-06-23
Call your ISP and tell them that you need a static IP so that a non-Windoze box can connect. If they doesn't respond in a short period or come with a lame excuse for not accepting your request, change to another ISP. Most boradband ISP's are very Windoze-centric these days.

---

### Post by jgoguen on 2006-06-23
As desirable as that may be, it's neither necessary or, in some cases, even feasible.

Chances are your cable modem has tied the IP to your Windows machine's MAC address.  Mine does this, I had to swap NICs from one machine to my gateway to get everything working.  OpenBSD gateway/firewall though, so I'm afraid I can't provide much help with configuring daemons and firewall rules.  If you plug your Windows machine in, get an IP, then issue "ipconfig /release" on the command line and plug in the Ubuntu server, that *should* do it.  If not, and it's a desktop/rack server (and you're comfortable doing so) you could just move the NIC to the gateway and replace it with one of those NICs.  Then set things up so that your gateway interface is that NIC, whatever it happens to be called.

---

### Post by tymanthius on 2006-06-23
[QUOTE=Kurt`]
Now to my problem. :)

If I plug a Windows machine **directly** into my cable modem and activate its "LAN connection", it receives my normal IP address from my ISP via DHCP. This is desirable.

When I plug the 'Router machine' **directly** into the cable modem and turn it on, it sends out a ton of DHCPDISCOVERs, then fails to bring up the interface.

How should I go about debugging this? I would prefer to receive the IP address from my ISP via DHCP. On occasion (every 6 months or so), my ISP assigns me a different address.

I will probably have some questions about DHCPD and the 5 possible interfaces it can use, so I figured I'd title this thread accordingly. ^^[/QUOTE]

I work for a cable company, and some, not all, modems will remember what device they were plugged into last, as long as they are constantly powered & connected to cable.  

Motorolla's sometimes do this, and Arris's almost always do, here where I work.

So, when you switch to the ubuntu machine, unplug power from the cable modem first, then make the switch.  Then bring power up the cable modem, then 'ifup ethX'. 

There's a good chance that will.  I know that we charge huge rates for static IP's, so that's not a viable solution for most.

---

### Post by Kurt` on 2006-06-23
[QUOTE=jgoguen]Chances are your cable modem has tied the IP to your Windows machine's MAC address.[/QUOTE]
I'm pretty sure this is the case now. After restarting my modem and attaching it to the router machine, it got a totally new IP. I reattached it to this PC directly, and it gave me the old IP again. I guess the issue was having to restart the modem every time the MAC address (attached device) changed.

Well, now that that is sorted out, I need to figure out how this DHCPD works.

I followed this guide when installing/doing initial configuration: [http://ubuntuguide.org/wiki/Dapper#DHCP_Server](http://ubuntuguide.org/wiki/Dapper#DHCP_Server) (replacing their DNS servers/domain with mine)

Now a few more questions :)

1.a. When I attach my modem directly to the router machine and get that other IP, I am assuming that my 3 DNS servers are different. How do I display them? ifconfig doesn't show them. (server installation, command-line only!)

1.b. Later on, if I want to setup my router machine to act as a caching DNS server for the local network, would I simply replace the "option domain-name-servers" with the "address" of my router machine? (See next question)

2. Will "option routers 192.168.0.1;" make my router machine have the address of 192.168.0.1 relative to hosts on my local network, or is that set elsewhere somehow?

3. Since my other NICs are simply acting as paths for network traffic to travel through, I don't need to enter any information for them in /etc/network/interfaces do I? I just "ifconfig eth1 up", "ifconfig eth2 up", etc.?

4. If I wanted to force hosts connecting over a certain interface (say, the wireless interface) to have a certain range of addresses (say, 192.168.0.50 through 192.168.0.100), would that require extreme networking knowledge or just a simple configuration file change? (I'm a programmer not a Cisco specialist, although I do undertstand how TCP and everything works for the most part)

Edit:

@tymanthius: Yes, it's a Motorola SB5100. Thanks

---

### Post by tymanthius on 2006-06-23
No problem.  

You might want to look at dnsmasq too.  It works nicely for dhcp, and can handle multiple subnets easily.

You do need to set static ip's for the nics.

The only problem I'm having with dnsmasq is I can't get it to serve up dns entries properly.  

If I type 'ping kidsputer' at the server, it returns 'unknown host'

---

### Post by Kurt` on 2006-06-24
I think I can figure out *most* of this on my own now. :p 

But, just for clarification, 2 questions :)

1. Let's say eth2 goes out to my wifi router, and I statically assign eth2 to be 192.168.1.3 on my router machine. If I am on the network via wifi, and I wanted to ping the router machine, I would ping 192.168.1.3?

2. I know that to do a machine <-> machine connection, you need a crossover cable. I activated eth1 as an interface for DHCP assignment. I plugged one end of a standard ethernet cable into eth1 and the other end into the "internet" port of a [Linksys BESFR41](http://xs102.xs.to/xs102/06256/befsr41_v3.jpg) (a few years old). I went into the administration panel, and told it to renew its address, but it didn't receive a new one (just showed 0.0.0.0 still). Do I need a crossover cable to do the eth1 <-> internet port connection as well?

---

### Post by tymanthius on 2006-06-24
[QUOTE=Kurt`]I think I can figure out *most* of this on my own now. :p 

But, just for clarification, 2 questions :)

1. Let's say eth2 goes out to my wifi router, and I statically assign eth2 to be 192.168.1.3 on my router machine. If I am on the network via wifi, and I wanted to ping the router machine, I would ping 192.168.1.3?
[/QUOTE]

Yes, that should work just fine.

[QUOTE=Kurt`]
2. I know that to do a machine <-> machine connection, you need a crossover cable. I activated eth1 as an interface for DHCP assignment. I plugged one end of a standard ethernet cable into eth1 and the other end into the "internet" port of a [Linksys BESFR41](http://xs102.xs.to/xs102/06256/befsr41_v3.jpg) (a few years old). I went into the administration panel, and told it to renew its address, but it didn't receive a new one (just showed 0.0.0.0 still). Do I need a crossover cable to do the eth1 <-> internet port connection as well?
[/QUOTE]

You shouldn't need a crossover cable.  What you described **should** work.  But I played havoc w/ my dhcp for a while too.  I finally had to install Breezy, set up dnsmasq, which worked for dhcp, still doesn't for local dns, then dist-upgrade to dapper.

---

