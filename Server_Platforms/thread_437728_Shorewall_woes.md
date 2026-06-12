---
title: "Shorewall woes"
date: 2007-05-09
forum: Server Platforms
---

### Post by mojoman on 2007-05-09
Hi,

I've been trying to set up shorewall on one of my computers and I really need some help.

First off, I got a desktop running on 64-bit feisty xubuntu, a ftp server running on 32-bit dapper using glFTPd and a laptop running on 32-bit Debian Etch with fluxbox. My connection is a VDSL modem connected to Netgear router. The netgear router has IP 192.168.0.1 and the modem does not have any IP of its own (a lot of the DSL-modems get an own IP starting on, I think, 10) so the external IP is forwarded straight through the modem.

The server and the laptop uses a wireless connection and the desktop is wired, all with static IP. My idea is to install shorewall on all computers, thus ensuring that if someone gets past the router firewall there will still be good protection.

As the desktop and server is in daily use I started dabbling with the laptop first, figuring that once I got that up and running I could use that to confugure the other but I've already hit the proverbial wall. But this is what I tried to do before hitting the wall.

First off, the interfaces I should configure is eth0 as ip route ls gives this:

```
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.2 
default via 192.168.0.1 dev eth0 
```

The zones I would use (for all computers) is the firewall (fw), the local network (loc) and the Internet (net). As the server has very little traffic on it (only about fifteen accounts) I see no idea to have a DMZ but rather give the permission to the IP of those with accounts. Thus, in zones I have this:
```

#ZONE	TYPE	OPTIONS			IN			OUT
#					OPTIONS			OPTIONS
fw	firewall
net	ipv4
loc	ipv4
```

Because eth0 is the only interface and I use it both for net and loc I need to edit hosts as well, and it looks like this:
```

#ZONE	HOST(S)					OPTIONS
loc	eth0:192.168.0.4,192.160.0.7		tcpflags,detectnets,nosmurfs
#net	eth0:
```

I commentented out net as it gave me an error that it was defined twice. Also, the two IP are for the server and desktop as they, together with the laptop, are what constitutes loc. Or should the router be included here as well?

Interfaces look like this:

```
#ZONE	INTERFACE	BROADCAST	OPTIONS
net     eth0            detect          dhcp,tcpflags,routefilter,nosmurfs,logmartians #norfc1918 deleted
#loc     eth0            detect          tcpflags,detectnets,nosmurfs
```

I deleted the option norfc1918. The howto for having this enabled seemed to presuppose that the modem had an IP and mine does not, at least according to my ISPs tech support. I also commented out loc, as it is defined in hosts. Right or wrong?

As for rules and policy, I haven't made any changes whatsoever in those files. I reckon I need this configured properly before fine tuning it. I did dabble a bit with rcf1918, trying to come to grips with that error and tried to use the router IP but it didn't help and with that option enabled the firewall doesn't start. However, here's how rcf1918 looks:

```
rcf1918
#SUBNETS		TARGET
192.168.0.1		RETURN		# ADDED to fix norfc error
172.16.0.0/12		logdrop		# RFC 1918
192.168.0.0/16		logdrop		# RFC 1918
10.0.0.0/8		logdrop		# RFC 1918
```

As it is now, I can get the firewall to start (after having commented out a few lines and deleted rcf1918 option as stated above). Boy, is it a good firewall! I can't even ping the damn laptop!  Forget about logging in via ssh from another computer or getting out on the Internet from the laptop. It is secure!

Anyway, I've gone over the howto's and the examples more then once and I still think it's very cloudy (no doubt due to my severe intellectual limitations though I  would argue that the shorewall man pages and howto are not a monument to lucidity and clarity). So, could anyone help me out here? Are there any obvious errors in my configuraton files? I should also add that I haven't made any changes in the shorwall.conf file but kept the default configuration.

Thanks for any and all help.
/mojoman

---

