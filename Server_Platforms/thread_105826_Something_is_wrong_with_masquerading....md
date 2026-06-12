---
title: "Something is wrong with masquerading..."
date: 2005-12-19
forum: Server Platforms
---

### Post by mxa055 on 2005-12-19
Hello there,

I am using an old PC running Ubuntu 5.10 as a gateway for another 3 windows PCs. I am using shorewall to configure iptables. The ubuntu installation is relatively fresh on this machine (1 week with no restart). After setting up shorewall everything worked fine... all PCs had internet etc... This morning though I just stop having internet access on the rest of the PCs, but still have internet access on the server. Tried restarting server - clearing and refilling shorewall settings... but nothing worked so far. It is really weird and I can't find what's wrong. Any help would be greatly appreciated.

Shorewall zones:
```
#
# 	Shorewall 2.0 -- Sample Zone File For Two Interfaces
# 	/etc/shorewall/zones
#
# This file determines your network zones. Columns are:
#
#	ZONE		Short name of the zone (5 Characters or less in length).
#	DISPLAY		Display name of the zone
#	COMMENTS	Comments about the zone
#
# THE ORDER OF THE ENTRIES IN THIS FILE IS IMPORTANT IF YOU HAVE NESTED OR
# OVERLAPPING ZONES DEFINED THROUGH /etc/shorewall/hosts.
#
# See http://www.shorewall.net/Documentation.html#Nested
#
#ZONE	DISPLAY		COMMENTS
net	Net		Internet
loc	Local		Local Networks
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE
```

```
#	
#	Shorewall 2.0 -- Sample Interface File For Two Interfaces
#
# 	/etc/shorewall/interfaces
#
#	You must add an entry in this file for each network interface on your
#	firewall system.
#
#
##############################################################################
#ZONE	INTERFACE	BROADCAST	OPTIONS
loc	eth1	detect   #THIS IS THE NIC LOOKING IN THE INTERNAL LAN
net	eth0	detect	dhcp,routefilter,tcpflags #NIC CONNECTED TO ADSL MODEM
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE

```

Policy configuration
```

###############################################################################
#SOURCE		DEST		POLICY		LOG LEVEL	LIMIT:BURST
# If you want open access to the Internet from your Firewall 
# remove the comment from the following line.
# THE FOLLOWING POLICY MUST BE LAST
all	all	DROP
loc	$FW	ACCEPT
$FW	loc	ACCEPT
loc	net	ACCEPT
$FW	net	ACCEPT
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE

```

Masquerading configuration
```

##############################################################################
#INTERFACE		SUBNET		ADDRESS
eth0	eth1
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE

```

All PCs are set to automatically acquire IP and DNS settings (servers runs dnsmasq) and all ping to all successfully

---

### Post by mxa055 on 2005-12-19
Located the problem, after reading the manual more carefully for small letters...

> If you are using the Debian package, please check your shorewall.conf file to ensure that the following is set correctly; if it is not, change it appropriately:

    *

      IP_FORWARDING=On

In my case it was IP_FORWARDING=KEEP

---

