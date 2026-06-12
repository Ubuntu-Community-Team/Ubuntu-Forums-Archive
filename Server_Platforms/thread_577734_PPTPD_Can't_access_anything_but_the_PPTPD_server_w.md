---
title: "PPTPD: Can't access anything but the PPTPD server when connected"
date: 2007-10-16
forum: Server Platforms
---

### Post by schleppy on 2007-10-16
Here is the setup: 7.04 server, latest pptpd installed.

The VPN server is behind a sonicwall that is doing NAT/Firewall duty. VPN connections that come in from outside the network are forwarded to the VPN server (whose IP is 192.168.100.231).

When I connect (from a Vista client) I am assigned the proper IP address, but I can ONLY access the VPN machine itself. If I try and access anything else on the 192.168.100.* network I can't. I also cannot connect to the internet. I'm assuming I'm having a problem with routes, but I don't know what to do to fix it.

Here is my /etc/pptpd.conf file:
```

###############################################################################
# $Id: pptpd.conf 4255 2004-10-03 18:44:00Z rene $
#
# Sample Poptop configuration file /etc/pptpd.conf
#
# Changes are effective when pptpd is restarted.
###############################################################################

# TAG: ppp
#	Path to the pppd program, default '/usr/sbin/pppd' on Linux
#
#ppp /usr/sbin/pppd

# TAG: option
#	Specifies the location of the PPP options file.
#	By default PPP looks in '/etc/ppp/options'
#
option	/etc/ppp/pptpd-options

# TAG: debug
#	Turns on (more) debugging to syslog
#
#debug

# TAG: stimeout
#	Specifies timeout (in seconds) on starting ctrl connection
#
# stimeout 10

# TAG: noipparam
#       Suppress the passing of the client's IP address to PPP, which is
#       done by default otherwise.
#
#noipparam

# TAG: logwtmp
#	Use wtmp(5) to record client connections and disconnections.
#
logwtmp

# TAG: bcrelay <if>
#	Turns on broadcast relay to clients from interface <if>
#
############I CHANGED THIS######
bcrelay eth0

# TAG: localip
# TAG: remoteip
#	Specifies the local and remote IP address ranges.
#
#       Any addresses work as long as the local machine takes care of the
#       routing.  But if you want to use MS-Windows networking, you should
#       use IP addresses out of the LAN address space and use the proxyarp
#       option in the pppd options file, or run bcrelay.
#
#	You can specify single IP addresses seperated by commas or you can
#	specify ranges, or both. For example:
#
#		192.168.0.234,192.168.0.245-249,192.168.0.254
#
#	IMPORTANT RESTRICTIONS:
#
#	1. No spaces are permitted between commas or within addresses.
#
#	2. If you give more IP addresses than MAX_CONNECTIONS, it will
#	   start at the beginning of the list and go until it gets 
#	   MAX_CONNECTIONS IPs. Others will be ignored.
#
#	3. No shortcuts in ranges! ie. 234-8 does not mean 234 to 238,
#	   you must type 234-238 if you mean this.
#
#	4. If you give a single localIP, that's ok - all local IPs will
#	   be set to the given one. You MUST still give at least one remote
#	   IP for each simultaneous client.
#
# (Recommended)
localip	192.168.100.250-253
remoteip	192.168.200.250-253
# or
#localip 192.168.0.234-238,192.168.0.245
#remoteip 192.168.1.234-238,192.168.1.245


```

And here is my /etc/ppp/pptpd-options file:

```

###############################################################################
# $Id: pptpd-options 4643 2006-11-06 18:42:43Z rene $
#
# Sample Poptop PPP options file /etc/ppp/pptpd-options
# Options used by PPP when a connection arrives from a client.
# This file is pointed to by /etc/pptpd.conf option keyword.
# Changes are effective on the next connection.  See "man pppd".
#
# You are expected to change this file to suit your system.  As
# packaged, it requires PPP 2.4.2 and the kernel MPPE module.
###############################################################################


# Authentication

# Name of the local system for authentication purposes 
# (must match the second field in /etc/ppp/chap-secrets entries)
name pptpd

# Optional: domain name to use for authentication
# domain mydomain.net

# Strip the domain prefix from the username before authentication.
# (applies if you use pppd with chapms-strip-domain patch)
#chapms-strip-domain


# Encryption
# Debian: on systems with a kernel built with the package
# kernel-patch-mppe >= 2.4.2 and using ppp >= 2.4.2, ...
# {{{
refuse-pap
refuse-chap
refuse-mschap
# Require the peer to authenticate itself using MS-CHAPv2 [Microsoft
# Challenge Handshake Authentication Protocol, Version 2] authentication.
require-mschap-v2
# Require MPPE 128-bit encryption
# (note that MPPE requires the use of MSCHAP-V2 during authentication)
require-mppe-128
# }}}


# Network and Routing

# If pppd is acting as a server for Microsoft Windows clients, this
# option allows pppd to supply one or two DNS (Domain Name Server)
# addresses to the clients.  The first instance of this option
# specifies the primary DNS address; the second instance (if given)
# specifies the secondary DNS address.
# Attention! This information may not be taken into account by a Windows
# client. See KB311218 in Microsoft's knowledge base for more information.
ms-dns 208.67.222.222
ms-dns 208.67.220.220

# If pppd is acting as a server for Microsoft Windows or "Samba"
# clients, this option allows pppd to supply one or two WINS (Windows
# Internet Name Services) server addresses to the clients.  The first
# instance of this option specifies the primary WINS address; the
# second instance (if given) specifies the secondary WINS address.
#ms-wins 10.0.0.3
#ms-wins 10.0.0.4

# Add an entry to this system's ARP [Address Resolution Protocol]
# table with the IP address of the peer and the Ethernet address of this
# system.  This will have the effect of making the peer appear to other
# systems to be on the local ethernet.
# (you do not need this if your PPTP server is responsible for routing
# packets to the clients -- James Cameron)
proxyarp

# Debian: do not replace the default route
nodefaultroute

# Logging

# Enable connection debugging facilities.
# (see your syslog configuration for where pppd sends to)
debug

# Print out all the option values which have been set.
# (often requested by mailing list to verify options)
#dump


# Miscellaneous

# Create a UUCP-style lock file for the pseudo-tty to ensure exclusive
# access.
lock

# Disable BSD-Compress compression
nobsdcomp 
auth


```

Any ideas? Are my local IP/remote IP settings ok? I've tried making both the same and different and it didn't seem to do anything. 

Does some other config file need to be altered?

Thanks so much for looking!

-Sean

---

### Post by koenn on 2007-10-16
I didn't look at your pptp conf, but i do believe it is probably a routing problem. 
First, on (Vista ?) your client, look for an option that says 'everything through tunnel" so you're reasonably sure that test packets (ping, traceroute, ...) will go through the tunnel. 

Then, with vpn up and running, do ```
tracert ipaddress.on.remote.lan
``` and see where it stops. Also try 
```
ping -c 5 ipaddress.on.remote.lan
``` and hope for a "reply from vpn server : destination unreachable" or something along those lines.

If I'm not mistaking, your (remote) vpn gateway should have a route to the remote LAN (192.168.100.0) AND to your local LAN (to send replies back through the tunnel). You can check with ```
route -n 
```
You should also see some additional routes on your client system when its connected to the vpn server

---

### Post by schleppy on 2007-10-16
Here is what a sudo route -n outputs:

```

Kernel IP routing table
Destination       Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.100.1   0.0.0.0         UG    0      0        0 eth0


```

So what should I have in there? Should I add the network's gateway (255.255.255.0) to the first route? Do both of those entries have to be in there for the machine's basic network functions to work?

Thanks for your help!

---

### Post by schleppy on 2007-10-17
Anyone else had any ideas?

---

### Post by Cohh on 2007-10-17
I may be having this same issue!

I can connect to my PTPPD linux box and browse files on it, but none of the other machines on my network are detected when I connect from outside my network!

I CAN see the machine thats running PTPPD however, and even access the HD through Samba. But I canno't get to my windows machine through it and it's driving me nuts!

Any ideas?

---

### Post by schleppy on 2007-10-17
I tried logging in last night from another Vista machine and I couldn't even get connected. Something is definitely screwed up in my config and/or the route table.

Hopefully someone has an idea. I searched a lot on here and didn't find anything specific.

---

### Post by koenn on 2007-10-17
2nd thought - i assume this is a ms-style pptp vpn, in which case the client gets an IP address in the same range as the remote network - so no routing is required. 

Your routing table looks OK for normal operations, although i would have expected a ppp device (ppp0 or so) to represent the remote connection. 

Since these are inbound connections (from the viewpoint of your firewall), could it be you've allowed connections with destination=your vpn server, but destination=other hosts on lan is blocked (explicitely, or implicitely because 'all' incoming connections are blocked or can't pass through the NAT ? )

---

### Post by schleppy on 2007-10-17
I don't think it has to do with any firewall permissions. The VPN machine has no trouble seeing other machines on the network.

---

### Post by lonetree on 2007-10-18
I was trying to get this solved years back, but I stil haven't got a clue, was hoping for someone to come out with a solution and maybe a mini howto.

regard,

---

### Post by koenn on 2007-10-19
> **schleppy said:**
> I don't think it has to do with any firewall permissions. The VPN machine has no trouble seeing other machines on the network.
A firewall can easily allow packets with destination=192.168.100.1 but block all packets with destination=192.168.100.2 or destination=192.168.100.3 so no matter what the VPN can or can not see, those connections will never get established. But if you don't think it's worth checking, fine.
Here's another suggestion for you to ignore : as your tunnel ends at the VPN-server, that server my need to have ip-forwarding turned on for packets to be forwarded to the other hostst on the LAN.

---

### Post by lonetree on 2007-11-10
> **koenn said:**
> A firewall can easily allow packets with destination=192.168.100.1 but block all packets with destination=192.168.100.2 or destination=192.168.100.3 so no matter what the VPN can or can not see, those connections will never get established. But if you don't think it's worth checking, fine.
Here's another suggestion for you to ignore : as your tunnel ends at the VPN-server, that server my need to have ip-forwarding turned on for packets to be forwarded to the other hostst on the LAN.

Hi koenn,

care to share your experience, when you say ip-forwarding. any additional packages to be installed? 


thanks

---

### Post by koenn on 2007-11-10
> **lonetree said:**
> Hi koenn,

care to share your experience, when you say ip-forwarding. any additional packages to be installed? 

thanks
No, it's just a kernel feature that needs to be enabled. you can check with
```
cat /proc/sys/net/ipv4/ip_forward 
```
if it returns 1, ip-forwarding is on. if it's not, you can set it with
```
 echo "1" > /proc/sys/net/ipv4/ip_forward 
```

---

### Post by dupski on 2008-07-21
> **koenn said:**
> ```
 echo "1" > /proc/sys/net/ipv4/ip_forward 
```

NOTE: the above only enabled IP forwarding until the machine is rebooted!!

To enable it permanently, the best way to do it is using the file **/etc/sysctl.conf**. You need to uncomment (or add) the line 

```
net.ipv4.ip_forward = 1
```

To enable the changes made in sysctl.conf without rebooting, you can run the command:

```
/etc/init.d/procps.sh restart
```

---

