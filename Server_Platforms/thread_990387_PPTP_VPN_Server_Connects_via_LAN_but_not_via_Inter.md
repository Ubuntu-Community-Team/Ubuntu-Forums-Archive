---
title: "PPTP VPN Server Connects via LAN but not via Internet"
date: 2008-11-22
forum: Server Platforms
---

### Post by coniefl on 2008-11-22
I am trying to setup PPTP VPN Server, at first I could not connect at all
but now I can only connect via LAN and cannot connect through the internet.
I have spent a few days searching for a solution, but cannot find one.

Can someone please help.

When I connect to the LAN with KVpnc it shows:

debug: No default interface given, tried default interface, got success, using "wlan0".
debug: Username: user
debug: Trying to connect to server "192.168.1.49" with user "user"... 
debug: [pppd] Using interface ppp0
debug: [pppd] Connect: ppp0 /dev/pts/0
debug: [pppd] CHAP authentication succeeded
debug: [pppd] MPPE 128-bit stateless compression enabled
debug: [pppd] found interface wlan0 for proxy arp
debug: [pppd] local IP address 192.168.1.31
debug: [pppd] remote IP address 192.168.1.49
success: Successful connected to server "192.168.1.49" user: "user" at Sat Nov 22 15:48:55 2008 [PPTP]
success: Connection established.



But when I connect via the Internet I get this:

debug: No default interface given, tried default interface, got success, using "wlan0".
debug: Username: user
debug: Trying to connect to server "xx.xx.xx.xx" with user "user"... 
debug: [pppd] anon warn[open_inetsock:pptp_callmgr.c:326]: connect: Connection refused
debug: [pppd] anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to xx.xx.xx.xx 
debug: [pppd] Using interface ppp0
debug: [pppd] Connect: ppp0 /dev/pts/0
debug: [pppd] anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
error: Call manager exited with error.

Windows just gives me an error 800.


I am trying to include everything I can think of that would possibly help with a solution.

The system configuration is as follows:


System is 

System hostname 	TMC
Operating system 	Ubuntu Linux 8.04.1
Webmin version 	1.440
Time on system 	Sat Nov 22 15:34:01 2008
Kernel and CPU 	Linux 2.6.24-21-generic on i686

There is a netgear router WGR614 V.7 attached with port forwarding for PPTP on port 1723.

The modem is a Ambit UBR cable modem with a static IP address.


Here is the pptpd.conf file:

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
ppp /usr/sbin/pppd

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
localip	192.168.1.49
remoteip	192.168.1.31-35

# or
#localip 192.168.0.234-238,192.168.0.245
#remoteip 192.168.1.234-238,192.168.1.245
#listen 192.168.1.1




and here is the /etc/ppp/pptpd-options file:

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
ms-dns 192.168.1.49


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
proxyarp



and here is  /etc/ppp/chap-secrets:

# Secrets for authentication using CHAP
# client	server	secret			IP addresses
user            *       password               *


and the port forwarding on the router looks like this


  	# 	Service Name 	Start Port 	End Port 	Server IP Address
  	1	HTTP	80	80	192.168.1.49
  	2	port	10000	10000	192.168.1.49
  	3	ftp	60000	60100	192.168.1.49
  	4	tmcftp	1980	1981	192.168.1.49
  	5	PPTP	1723	1723	192.168.1.49
 

There is no Firewall running on the server.

I hope that's enough info, if not please let me know what else would be needed.

---

### Post by Lars Noodén on 2008-11-23
You may want to steer away from PPTP and use SSL or IPSEC, if security is an aspect to be considered:
[http://www.vpnc.org/vpn-standards.html](http://www.vpnc.org/vpn-standards.html)

What is the goal you are after?  Having a VPN might be the long way around.    

Was there a particular reason you chose that package over openvpn or tinc?

---

### Post by coniefl on 2008-11-24
I chose this package for no particular reason, other than it did VPN. I could change to a different package if needed.

My goal is to allow certain users to VPN into the Ubuntu server from a windows box and map a folder from the server as a drive on there windows box. I don't know exactly how to do this, but figured I would need to VPN first, and then possibly have to set up a SAMBA share over the vpn.

I have a web site on the server that depending upon what the user is displaying, the web site will open up a local program (Bentley View) via java on the users computer. Bentley view will to point to the Mapped drive to access the files needed to be displayed in the Bentely view program.

If there is an easier way, please advise.

---

