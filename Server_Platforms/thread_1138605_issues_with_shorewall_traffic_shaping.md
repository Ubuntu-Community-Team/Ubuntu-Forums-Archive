---
title: "issues with shorewall traffic shaping"
date: 2009-04-26
forum: Server Platforms
---

### Post by headnoodle on 2009-04-26
Hi, I run a ubuntu server at home for my router amongst other things and am trying to set it up so that my lad only has a certain amount of the bandwidth available to him to download as he is hitting it quite hard most days and it is affecting everyone elses performance.

I am running shorewall with squid doing the transparent proxying for the clients.

I have setup traffic shaping and it is successfully shaping the traffic for that particular IP except for web traffic.  My guess is that the issue revolves around me redirecting www traffic in my rules file to squid which is bypassing the traffic shaping config.  Any help would be appreciated.

I have included my config files below

Cheers,

Dean.

**interfaces file**

#ZONE	INTERFACE	BROADCAST	OPTIONS
net     eth0            detect          dhcp,tcpflags,routefilter,nosmurfs,logmartians,upnp
loc     eth1            detect          tcpflags,nosmurfs,maclist
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE

[B]
policy file[/B]

# Policies for traffic originating from the local LAN (loc)
#
# If you want to force clients to access the Internet via a proxy server
# on your firewall, change the loc to net policy to REJECT info.
loc		net		ACCEPT
loc		$FW		REJECT		info
loc		all		REJECT		info

#
# Policies for traffic originating from the firewall ($FW)
#
# If you want open access to the Internet from your firewall, change the
# $FW to net policy to ACCEPT and remove the 'info' LOG LEVEL.
# This may be useful if you run a proxy server on the firewall.
$FW		net		ACCEPT		info
$FW		loc		REJECT		info
$FW		all		REJECT		info

#
# Policies for traffic originating from the Internet zone (net)
#
net		$FW		DROP		info
net		loc		DROP		info
net		all		DROP		info

# THE FOLLOWING POLICY MUST BE LAST
all		all		REJECT		info

#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE

**rules file**

#############################################################################################################
#ACTION		SOURCE		DEST		PROTO	DEST	SOURCE		ORIGINAL	RATE		USER/	MARK
DNS/ACCEPT	$FW		net
DNS/ACCEPT	loc		$FW
MySSH/ACCEPT	loc		$FW
MySSH/ACCEPT	net		$FW
Ping/ACCEPT	loc		$FW
HTTP/ACCEPT	loc		$FW
Ping/DROP	net		$FW
MySSH/ACCEPT	net		$FW
ACCEPT		$FW		loc		icmp
ACCEPT		$FW		net		icmp
REDIRECT	loc		3128		tcp	www	-		!10.9.8.1
ACCEPT		$FW		net		tcp	www
ACCEPT		$FW		loc		all	-	-		-		-		root
forwardUPnP	net		loc
allowinUPnP	loc		$FW
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE


**tcdevices file**

#INTERFACE	IN-BANDWITH	OUT-BANDWIDTH
eth1		1024mbit		1024mbit
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE

**tcclasses file**

#INTERFACE	MARK	RATE		CEIL	PRIORITY	OPTIONS
eth1		1	10mbit		full	1		default
eth1		2	256kbit		2mbit	2		
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE

**tcrules file**
#MARK		SOURCE		DEST		PROTO	DEST	SOURCE	USER	TEST	LENGTH	TOS
#							PORT(S)	PORT(S)
RESTORE:F	0.0.0.0/0	0.0.0.0/0
CONTINUE:F	0.0.0.0/0	0.0.0.0/0	all	-	-	-	!0
2:F		10.9.8.169	0.0.0.0/0	all
SAVE:F		0.0.0.0/0	0.0.0.0/0
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE

---

### Post by headnoodle on 2009-04-27
wondering if anyone had any idea on this?

---

### Post by headnoodle on 2009-05-06
have I posted this in the wrong forum?

---

