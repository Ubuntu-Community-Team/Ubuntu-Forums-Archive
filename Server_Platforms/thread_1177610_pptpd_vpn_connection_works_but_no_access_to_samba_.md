---
title: "pptpd vpn connection works but no access to samba shares"
date: 2009-06-03
forum: Server Platforms
---

### Post by Foeburner on 2009-06-03
Hello, 

I create a PPTPD VPN server and am able to connect to it but once inside, it cannot find the paths to the shares. 

I enabled iptables forwarding and opened the port to 1723 (which arent all ports already opened by default?) and when the client pings the vpn server, I can see it on the server with tcpdump. 

When the client tries to ping the shared server, it fails to ping but I can still see it on the server with tcpdump so it must be the server not forwarding the traffic, right? 

Also, when the client connects, its subnet is 255.255.255.255 instead of the .192 that the office network runs on. 

Let me know if you need more info.

---

### Post by samosamo on 2009-06-04
Please post the routing table of your gateway and your PPTPD server.  You sure you turned on ipv4 forwarding on the PPTPD server, right?

edit: Wait a second, 255.255.255.255 indicates a single-host subnet!!!  Set it to a larger subnet like 255.255.255.0 for example and make sure your gateway reflects the same change

---

### Post by Foeburner on 2009-06-04
I cannot change the subnet 255.255.255.255. When the client connects to the vpn server, it automatically receives that subnet. I checked google and there are lots of reports of this case. I still havent found how to force a client to a specific subnet. 

My vpn server is not NATd. It is connected directly to the ISP managed router (the ISP manages it) so there's nothing blocking anything from it.


That is I get when I cat. 
```
 afuentes@ARTHAS:~$ cat /proc/sys/net/ipv4/ip_forward
1
afuentes@ARTHAS:~$

```



This is my pptpd conf file.
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
option /etc/ppp/pptpd-options

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
#bcrelay eth1

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
#localip 192.168.0.1
#remoteip 192.168.0.234-238,192.168.0.245
# or
localip 172.30.11.1
remoteip 172.30.11.100-238
```



This is my pptpd-options conf file

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
#ms-dns 10.0.0.1
#ms-dns 10.0.0.2

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
#debug

# Print out all the option values which have been set.
# (often requested by mailing list to verify options)
#dump


# Miscellaneous

# Create a UUCP-style lock file for the pseudo-tty to ensure exclusive
# access.
lock

# Disable BSD-Compress compression
nobsdcomp 
```

---

### Post by Foeburner on 2009-06-09
would it be easier to just setup a windows box? seems like it at this point.

---

### Post by Foeburner on 2009-06-15
I got it working... somewhat. I enabled WINS and added name resolve order on samba on the file server and now I can connect to the vpn and browse the file server. 

BUT...

There is also another share on another computer (Vista Business) that I need access to but the path is unrecognizable and cannot ping it. 

I followed these howto's:
[http://ubuntuforums.org/showthread.php?t=65385&highlight=wins](http://ubuntuforums.org/showthread.php?t=65385&highlight=wins)
[http://pigtail.net/nicholas/pptp/](http://pigtail.net/nicholas/pptp/)
this did not work for me
[http://pigtail.net/nicholas/pptp/browsing.html](http://pigtail.net/nicholas/pptp/browsing.html)

How can I add this new share?

---

### Post by Foeburner on 2009-06-16
bump

---

### Post by Foeburner on 2009-11-05
For future reference, my mistake was in the pptpd.conf file. If you look at my pptpd.conf posted on June 4th, the ip range I gave was beyond my subnet. 

localip 172.30.11.1
remoteip 172.30.11.100-238

My network's subnet is 255.255.255.192 and to set it in pptp, I needed to set the highest range to 172.30.11.62. 

In my case, since only a handful of people were going to be connected to the vpn at one time, I set the range to 172.30.11.58-62.

This fixed my subnet issue and was able to browse all shares on the same subnet.

Hope this helps!  =D

---

