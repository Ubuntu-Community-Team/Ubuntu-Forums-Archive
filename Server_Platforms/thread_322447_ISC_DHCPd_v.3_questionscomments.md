---
title: "ISC DHCPd v.3 questions/comments"
date: 2006-12-20
forum: Server Platforms
---

### Post by lubod on 2006-12-20
Hello, I'm running a Dapper 6.06 LTS Server with Webmin 1.300 and the DHCP Server module installed and running.

The way I have it set up is very specific to our network requirements, which are:

2 network cards, one with a public WAN IP address, one with a private LAN IP address. 
eth0 is the LAN address which is for example 10.x.y.z
eth1 is the WAN address which is for example 216.x.y.z

basically it has to act at least as a DHCP server, but in some cases also as a router/firewall/NAT gateway.

computers are hooked up to the LAN side, and assigned addresses manually. Before you say that defeats the purpose of DHCP, understand there is a valid administrative reason:
what is required is control of who gets on the network via MAC address filtering, and the way I accomplished this is with a direct one to one list, IP address <-> MAC address correspondence. Maybe it's not the most elegant solution, but it works.

My problem is I don't seem to be able to effect changes to the list of allowed computers simply by adding and saving their info and then clicking start DHCP in the Webmin GUI, which executes the equivalent of the CLI command **$/etc/init.d/dhcp3-server start**.

The changes seem to only take effect when I give the CLI command **$/etc/init.d/dhcp3-server restart**.

I know I can rig the Webmin GUI so it executes the second command (restart) instead of (start), and in a way that might do it. I'm hoping there is a way to make (start) do the right thing though.

As an aside, even **$/etc/init.d/dhcp3-server restart** seems to allow all currently connected computers to continue routing with no visible interruption to their traffic, so it is a tolerable solution, just not the ideal one.

---

