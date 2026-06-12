---
title: "HOWTO - Basic Network Troubleshooting / Understanding"
date: 2005-04-10
forum: Tutorials
---

### Post by dataw0lf on 2005-04-10
[SIZE=3][CENTER]**HOWTO - Basic Network Troubleshooting / Understanding**[/CENTER][/SIZE]

Networking is sometimes considered to be complex, and hard to debug and manage.  However, Linux (and thus Ubuntu) provides you with numerous tools to figure out exactly what's going wrong on your network, and how to fix it.  What is really the problem is most people don't understand networking in the way they should.  Hopefully, this HOWTO will get you started down the long, and sometimes hairy, road of figuring out exactly what's going wrong.  This guide isn't intended to be all inclusive. However, this is the first in three guides on networking I plan on posting, this being the most basic.

[SIZE=2]**The Basic Formula**[/SIZE]

This is a list of basic steps you should take in troubleshooting your network.  Explanations will follow.


[B]Is the interface configured correctly ? (lspci, lsmod, dmesg, ifconfig /etc/network/interfaces)

Is/Are DNS / hostnames configured correctly ? (Bind, /etc/hosts, /etc/resolv.conf)


Are the ARP tables correct ? ( arp -a )

Can you ping the localhost ? (ping localhost / 127.0.0.1 *try both*)

Can you ping other local hosts (hosts on the local network) by IP Address?  How about hostname? (ping)

Can you ping hosts on another network (ala internet) ? (ping)

Do applications like ssh, firefox, sftp, etc, work ? (chosen application)[/B]

This seems rather verbose.  However, all you're doing is going either up or down the network model layers.  Huh, you say? The basic network model layers are just differing levels of the network, it's better if you see a layout:

[I]Application Layer (ssh, telnet, firefox)
Transport Layer (flow control, etc)
Network Layer (addressing, routing)
Link Layer (hardware / device drivers)
Physical Layer (the actual cable or other physical media)[/I]

If you look at my troubleshooting steps above, we move up the layers.  This is always a good idea when troubleshooting networks.  Move up or down the layers; don't skip any steps.
[SIZE=2]
**Explanations**[/SIZE]

Ok, so you're reading this and your mind feels like it's frying.  What the hell is dataw0lf talking about??? I'M A NEWBIE, FOR GOD'S SAKE!  Well, I'm going to try to explain some simple commands that'll make your life (and hopefully mine) a bit easier.  Before that, however, we're going to go over routing tables and DNS very, very quickly. In the intermediate guide, I'll go over more complex protocols.

[SIZE=2]**Routing Tables **
[/SIZE]
Want to see your routing tables? Open a prompt and type either netstat -nr or route.  This will list your routing tables.  Well what does that mean? Let's take a look.

```
dataw0lf@darktower:~ $ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
```

Brief explanation of the -nr options: -n means return numeric output (ie, IP address instead of hostname) and -r means print the routing table.
To understand IP routing you just have to understand one thing : it's 'next hop' routing.  At any given point in the network, you just have to figure out where the NEXT host or router to get to to reach it's destination.  
This is where 'default' routes come in.  The 0.0.0.0 in my routing table is the 'default route'.  If I get a packet that says ' I need to go to yahoo.com ', my routing tables are searched.  If yahoo.com is NOT found in my routing table (which it obviously isn't), it's routed to my default route, which is also my gateway (the G flag in Flags).  So it's forwarded to that IP (which happens to be my router/firewall, which in turn routes it out to the wilderness of the internet).  Always check and see if the box you're having trouble with has a default route.  Adding a default route is easy as pie:

```
route add default gw <gateway-ip-address>
```

The gateway is usually going to be your DSL modem / router / firewall. 
If you can wrap your mind around that, you understand routing.
[SIZE=2]
**DNS **[/SIZE]

DNS can be very complex to setup (ala Bind).  However, I'm going to give you a very simple explanation: DNS is used to map names (dataw0lf.org) to IPs (198.60.114.127).  This is why, when you check hosts on your network, try to use the hostname AND IP.  

A brief anecdote on why this is important:

At work, I installed a fiber network card on an employee's workstation.  It was on Windows 2k Pro, and I thought I'd just stick it in real quick before I got onto some more pressing issues.  So I just made sure it was detected and operating (and removed the ethernet NIC).  What a mistake.

Three days later, the same employee can't attach our backup software gui to a ssh x session.  I go through complex ssh configs, try everything.  After three hours of futile troubleshooting, I remember the fiber card.  And that I didn't setup the IP to make sure it was the same (he was trying to attach using the hostname, which pointed at the old IP, and it was giving off ssh authentication errors).  Three hours when, if I'd tried attaching the display to the IP as well as the hostname, I would've known what the problem was.

Now, onto tools..

*ping *

ping is THE tool.  Just because it's simple doesn't mean it shouldn't be used.  ping returns all sorts of goodies.  Plus, it's a great baseline: if you can't ping something, you probably can't connect to it through a higher level application (ssh and the like).  Here's an example of ping at work:
```

dataw0lf@darktower:~ $ ping -c 3 yahoo.com
PING yahoo.com (66.94.234.13) 56(84) bytes of data.
64 bytes from w2.rc.vip.scd.yahoo.com (66.94.234.13): icmp_seq=1 ttl=55 time=65.5 ms
64 bytes from w2.rc.vip.scd.yahoo.com (66.94.234.13): icmp_seq=2 ttl=56 time=65.1 ms
64 bytes from w2.rc.vip.scd.yahoo.com (66.94.234.13): icmp_seq=3 ttl=56 time=65.4 ms

--- yahoo.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 65.150/65.378/65.568/0.342 ms

```

First off: the -c option is used to pass how many packets you're sending.  As you can see, I decided to send 3 (just to keep it brief).  Optionally, you can just Ctrl-C your way out of a ping, but that's no fun. 
As you can see I'm pinging yahoo.com.  It gives me the IP address (definitely useful, and meaning that DNS is working [ yahoo.com got resolved to the IP address ] ), and some other rather cryptic stuff.  We'll go over this briefly.
The ttl 
Now, look at the icmp_seq.  As you might guess, the icmp_seq is the ICMP Sequence number.  If these are off (ie, you get a 1, then a 4, then a 6).  A healthy network won't drop these too much.  TCP/IP isn't foolproof, but if you're seeing major gaps in your icmp_seq, you're losing packets somewhere, and you'll experience lag that you normally shouldn't.  I'm not going to explain how to 'clean' this up (through traceroute), that will be for my 'intermediate course'.  

*ifconfig *

Ah, ye ifconfig.  This can tell you everything you need to know about the interface.

Example:
 
```

dataw0lf@darktower:~ $ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0A:E6:C6:07:85
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e6ff:fec6:785/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4015093 (3.8 MiB)  TX bytes:1449812 (1.3 MiB)
          Interrupt:10 Base address:0xd400
```

This gives me my IP, my MAC address (HWaddr), RX/TX packets, the interrupt it's on, etc. RX means Received, TX means Transferred.  This is another easy tool to see if your interface is actually loading correctly.  I'll explain Broadcasting and Netmasking in the next guide, when I explain TCP/IP in detail.

This is the very basics of network debugging.  In the next issue, we'll discover TCP/IP, tcpdump, and traceroute.

---

### Post by dewey on 2005-04-10
Many times I've found for applications like webmin or SSH, simply add a port forwarding line for them inside of your router, and point them to preferably, a static ip. and it works like a charm.

For instance, I configured my computer to have a static ip of 192.168.1.111 (easy to remember) through Ubuntu's network gui config, then simply accessed my Network Everywhere router by using the URL [http://192.168.1.1/](http://192.168.1.1/) and added the lines for port forwarding of webmin and SSH default ports, 10000 and 22 respectfully, pointing to the computer running the services with the ip 192.168.1.111.

This is a very stripped down explanation, but it's helped alot of people. (Note: For this method, you must be within your own network)

---

### Post by LusiphurScyla on 2005-04-11
I wirted it, but doesnt work.

Same error...the interface is not reconized.
The pcmcia card works fine...im sure of it. i tried with the comand ifconfig /etc/network/interfaces....and says the same.

i tried to add another gateway but is useless...it does not leave me.

---

### Post by puelly on 2005-04-15
Nice article. looking forward to the next installment. kudos.  \\:D/

---

### Post by Zhukov on 2005-04-16
Hmmm, maybe you can help me... Ive just bought a router, and after some small troubles i made him work with ubuntu - Big DNS problems...
The DNS problems are still there...Every app takes a while finding the server...to long...

Is there any way to solve this?

---

### Post by dewey on 2005-04-16
Did you use static or dynamic addressing?  And what exactly is the problem, we need specifics to be of any help.

---

### Post by Marble2 on 2005-04-17
Great guide, but I have a small problem. Traceroute won't work for me, ping works fine, I can connect to the internet, all that works. But traceroute just won't work. It drops after the first hop. Here's a sample traceroute. ```

greg@Greg:~ $ traceroute google.com
traceroute: Warning: google.com has multiple addresses; using 216.239.57.99
traceroute to google.com (216.239.57.99), 30 hops max, 38 byte packets
 1  192.168.1.1 (192.168.1.1)  0.692 ms  0.652 ms  0.611 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * *

```

---

### Post by Zhukov on 2005-04-17
:D Just to say that finally ive managed to solve the problem...

The problem was with the dns. My router was receiveng dns from the isp, in windows, using 192.168.1.1 as dns worked, but not in ubuntu. Ive inserted the ip of the real dns server, but my isp wasnt giving the right ips, so...

...i've wandered for 3 days, just because i had a wrong dns server ip.

Thanks anyway.  ;-)

---

### Post by javifs on 2005-04-26
This script might prove useful:

```

#!/bin/sh
# Network testing script v 1.0
# (c) 2005 Javier Fernandez-Sanguino
#
# This script will test your system's network configuration using basic
# tests and providing both information (INFO messages), warnings (WARN)
# and possible errors (ERR messages) by checking:
# - Interface status
# - Availability of configured routers, including the default route
# - Proper host resolution, including DNS checks
# - Proper network connectivity (the remote host can be configured, see
#   below)
# 
# The script does not need special privileges to run as it does not 
# do any system change. It also will not fix the errors by itself.
#
#   This program is free software; you can redistribute it and/or modify
#   it under the terms of the GNU General Public License as published by
#   the Free Software Foundation; either version 2 of the License, or
#   (at your option) any later version.
#
#   This program is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.
#
#   You should have received a copy of the GNU General Public License
#   along with this program; if not, write to the Free Software
#   Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA
#  
# You can also find a copy of the GNU General Public License at
# [http://www.gnu.org/licenses/licenses.html#TOCLGPL](http://www.gnu.org/licenses/licenses.html#TOCLGPL)
#
# TODO
# - Works only on Linux, can this be generalised for other UNIX systems
#   (probably not unless rewritten in C)
# - Does not check for errors properly, use -e and test intensively
#   so that expected errors are trapped
#   (specially for tools that are not available, like netcat)
# - If the tools are localised to languages != english the script might 
#   break 
# - Ask 'host' maintainer to implement error codes as done with 
#   dlint
# - Should be able to check if DNS server is in the same network, if 
#   it doesn't answer to pings, check ARP in that case.
# - DHCP checks?
# - Other internal services tests? (LDAP if using pam...)
# - Generate summary of errors in the end (pretty report?)
# - Check if packets are being dropped by local firewall? (use dmesg
#   and look for our tests)
# - Support wireless interfaces? (use iwconfig)
# - Check other TODOs inline in the code


# BEGIN configuration
# Configure to your needs, these values will be used when
# checking DNS and Internet connectivity
# DNS name to resolve
CHECK_HOST=www.debian.org
CHECK_IP_ADRESS=194.109.137.218
# Web server to check for
CHECK_WEB_HOST=www.debian.org
CHECK_WEB_PORT=80
export CHECK_HOST CHECK_IP_ADRESS CHECK_WEB_HOST CHECK_WEB_PORT
# END configuration


# Extract the interface of our default route

defaultif=`netstat -nr |grep ^0.0.0.0 | awk '{print $8}' | head -1`
defaultroutes=`netstat -nr |grep ^0.0.0.0 | wc -l`
if [ -z "$defaultif" ] ; then
	defaultif=none
	echo "WARN: This system does not have a default route"
elif [ "$defaultroutes" -gt 1 ] ; then
	echo "WARN: This system has more than one default route"
else 
	echo "INFO: This system has exactly one default route"
fi



# Check loopback
check_local () {
# Is there a loopback interface? 
	if [ -n "`ip link show lo`" ] ; then
# OK, can we ping localhost
		if  ! check_host localhost 1; then
# Check 127.0.0.1  instead (not everybody uses this IP address however,
# although its the one commonly used)
			if  ! check_host 127.0.0.1 1; then
				echo "ERR: Cannot ping localhost (127.0.0.1), loopback is broken in this system"
			else
				echo "ERR: Localhost is not answering but 127.0.0.1, check /etc/hosts and verify localhost points to 127.0.0.1"
			fi
		else
		 echo "INFO: Loopback interface is working properly"
		fi
			
	else
		echo "ERR: There is no loopback interface in this system"
		status=1
	fi
	status=0
	return $status
}

# Check network interfaces
check_if () {
	ifname=$1
	status=0
	[ -z "$ifname" ] && return 1
# Find IP addresses for $ifname
	inetaddr=`ip addr show $ifname | grep inet | awk '{print $2}'`
	if [ -z "$inetaddr" ] ; then
		echo "WARN: The $ifname interface does not have an IP address assigned"
		status=1
	else
# TODO: WARN if more than 2 IP addresses?
		echo $inetaddr | while read ipaddr; do
			echo "INFO: The $ifname interface has IP address $ipaddr  assigned"
		done
	fi

# Lookup TX and RX statistics
# TODO: This is done using ifconfig but could use /proc/net/dev for
# more readibility or, better, 'netstat -i'
	txpkts=`ifconfig $ifname | awk '/RX packets/ { print $2 }' |sed 's/.*://'`
	rxpkts=`ifconfig $ifname | awk '/RX packets/ { print $2 }' |sed 's/.*://'`
	txerrors=`ifconfig $ifname | awk '/TX packets/ { print $3 }' |sed 's/.*://'`
	rxerrors=`ifconfig $ifname | awk '/RX packets/ { print $3 }' |sed 's/.*://'`
# TODO: Check also frames and collisions, to detect faulty cables
# or network devices (cheap hubs)
	if [ "$txpkts" -eq 0 ] && [ "$rxpkts" -eq 0 ] ; then
		echo "ERR: The $ifname interface has not tx or rx any packets. Link down?"
		status=1
	elif  [ "$txpkts" -eq 0 ]; then
		echo "WARN: The $ifname interface has not transmitted any packets."
	elif [ "$rxpkts" -eq 0 ] ; then
		echo "WARN: The $ifname interface has not received any packets."
	else
		echo "INFO: The $ifname interface has tx and rx  packets."
	fi
# TODO: It should be best if there was a comparison with tx/rx packets.
# a few errors are not uncommon if the card has been running for a long
# time. It would be better if a relative comparison was done (i.e.
# less than 1% ok, more than 20% warning, over 80% major issue, etc.)
	if [ "$txerrors" -ne 0 ]; then
		echo "WARN: The $ifname interface has tx errors."
	fi
	if [ "$rxerrors" -ne 0 ]; then
                echo "WARN: The $ifname interface has rx errors."
	fi
	return $status
}

check_netif () {
	status=0
	ip link show | egrep '^[[:digit:]]' |
	while read ifnumber ifname status extra; do
		ifname=`echo $ifname |sed -e 's/:$//'`
		if [ -z "`echo $status | grep UP\>`" ] ; then
			if  [ "$ifname" = "$defaultif" ] ; then
				echo "ERR: The $ifname interface that is associated with your defualt route is down!"
				status=1
			elif  [ "$ifname" = "lo"  ] ; then
				echo "ERR: Your lo inteface is down, this might cause issues with local applications (but not necessarily with network connectivity)"
			else
				echo "WARN: The $ifname interface is down"
			fi
		else
		# Check network routes associated with this interface
			echo "INFO: The $ifname interface is up"
			check_if $ifname
			check_netroute $ifname
		fi
	done
	return $status
}

check_netroute () {
	ifname=$1
	[ -z "$ifname" ] && return 1
	netstat -nr  | grep "${ifname}$" |
	while read network gw netmask flags mss window irtt iface; do
	# For each gw that is not the default one, ping it
		if [ "$gw" != "0.0.0.0" ] ; then
			if ! check_router $gw  ; then
				echo "ERR: The default route is not available since the default router is unreachable"
			fi
		fi
	done
}

check_router () {
# Checks if a router is up
	router=$1
	[ -z "$router" ] && return 1
	status=0
# First ping the router, if it does not answer then check arp tables and
# see if we have an arp. We use 5 packets since it is in our local network.
	ping -q -c 5 "$router" >/dev/null 2>&1 
	if [ "$?" -ne 0 ]; then
		echo "WARN: Router $router does not answer to ICMP pings"
# Router does not answer, check arp
		routerarp=`arp -n | grep "^$router" | grep -v incomplete`
		if [ -z "$routerarp" ] ; then
			echo "ERR: We cannot retrieve a MAC address for router $router"
			status=1
		fi
	fi
	if [ "$status" -eq 0 ] ; then
		echo "INFO: The router $router is reachable"
	fi
	return $status
}

check_host () {
# Check if a host is reachable
# TODO: 
# - if the host is in our local network (no route needs to be used) then
#   check ARP availability
# - if the host is not on our local network then check if we have a route
#   for it
	host=$1
	[ -z "$host" ] && return 1
# Use 10 packets as we expect this to be outside of our network
	COUNT=10
	[ -n "$2" ] && COUNT=$2
	status=0
	ping -q -c $COUNT "$host" >/dev/null 2>&1 
	if [ "$?" -ne 0 ]; then
		echo "WARN: Host $host does not answer to ICMP pings"
		status=1
	else
		echo "INFO: Host $host answers to ICMP pings"
	fi
	return $status
}

check_dns () {
# Check the nameservers defined in /etc/resolv.conf
	status=1
	nsfound=0
	nsok=0
	tempfile=`mktemp tmptestnet.XXXXXX` || { echo "ERR: Cannot create temporary file! Aborting! " >&2 ; exit 1; }
	trap " [ -f \"$tempfile\" ] && /bin/rm -f -- \"$tempfile\"" 0 1 2 3 13 15
	cat /etc/resolv.conf |grep nameserver | 
	awk '/nameserver/ { for (i=2;i<=NF;i++) {  print $i ; } }'  >$tempfile
	for nameserver in `cat $tempfile`;  do
		nsfound=$(( $nsfound + 1 ))
		echo "INFO: This system is configured to use nameserver $nameserver"
		check_host $nameserver 5
		if check_ns $nameserver ; then
			nsok=$(( $nsok +1 ))
		else
			status=$?
		fi
	done
	#Could also do:
	#nsfound=`wc -l $tempfile | awk '{print $1}'`
	/bin/rm -f -- "$tempfile"
	trap  0 1 2 3 13 15
	if [ "$nsfound" -eq 0 ] ; then
		echo "ERR: The system does not have any nameserver configured"	
	else
		if [ "$status" -ne 0 ] ; then
			if [ "$nsfound" -eq 1 ] ; then
				echo -e "ERR: There is one nameserver configured for this system but it does not work properly"
			else
				echo "ERR: There are $nsfound nameservers configured for this system and none of them works properly"
			fi
		else
			if [ "$nsfound" -eq 1 ] ; then
				echo "INFO: The nameserver configured for this system works properly"
			else
				echo "INFO: There are $nsfound nameservers is configured for this system and $nsok are working properly"
			fi
		fi
	fi
	return $status
}

check_ns () {
# Check the nameserver using host
# TODO: use nslookup?
#	nslookup $CHECK_HOST -$nameserver 
	nameserver=$1
	[ -z "$nameserver" ] && return 1
	status=1
	CHECK_RESULT="$CHECK_HOST .* $CHECK_IP_ADDRESS"
# Using dnscheck:
	dnscheck=`host -t A $CHECK_HOST $nameserver 2>&1 | tail -1`
	if [ -n "`echo $dnscheck |grep NXDOMAIN`" ] ; then
		echo "ERR: Dns server $nameserver does not resolv properly"
	elif [ -n "`echo $dnscheck | grep \"timed out\"`" ] ; then
		echo "ERR: Dns server $nameserver is not available"
	elif [ -z "`echo $dnscheck | egrep \"$CHECK_RESULT\"`" ] ; then
		echo "WARN: Dns server $nameserver did not return the expected result for $CHECK_HOST"
	else
		echo "INFO: Dns server $nameserver resolved correctly $CHECK_HOST"
		status=0
	fi

# Using dlint
#	dlint $CHECK_HOST @$nameserver >/dev/null 2>&1
#	if [ $? -eq 2 ] ; then
#		echo "ERR: Dns server $nameserver does not resolv properly"
#	elif [ $? -ne 0 ]; then
#		echo "ERR: Unexpected error when testing $nameserver"
#	else
#		echo "INFO: Dns server $nameserver resolved correctly $CHECK_HOST"
#		status=0
#	fi

	return $status
}

check_conn () {
# Checks network connectivity
	if ! check_host $CHECK_WEB_HOST >/dev/null ; then
		echo "WARN: System does not seem to reach Internet host $CHECK_WEB_HOST through ICMP"
	else
		echo "INFO: System can reach Internet host $CHECK_WEB_HOST"
	fi
# Check web access, using nc
	echo -e "HEAD / HTTP/1.0\n\n" |nc $CHECK_WEB_HOST $CHECK_WEB_PORT >/dev/null 2>&1
	if [ $? -ne 0 ] ; then
		echo "WARN: Cannot access web server at Internet host $CHECK_WEB_HOST"
	else
		echo "INFO: System can access web server at Internet host $CHECK_WEB_HOST"
	fi
}

# TODO: checks could be conditioned, i.e. if there is no proper
# interface setup don't bother with DNS and don't do some Inet checks
# if DNS is not setup properly
check_local
check_netif
check_dns
check_conn

exit 0
```

---

### Post by jkndrkn on 2005-05-30
Here is my IP routing table

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.5.96.65      0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.2.1     0.0.0.0         UG        0 0          0 wlan0
``` 

I am unable to reach the internet through my ppp0 connection. How can I set the flag for it to UG?

I tried using route add etc, but it returned an error: 

```

jkndrkn@SubtleBubbleWilliams:~$ sudo route add default gw 0.0.0.0
SIOCADDRT: Invalid argument
```

Any pointers?

---

### Post by Lunde on 2005-07-01
Great guide, thanks! looking forward to the other 2 parts..

---

### Post by dataw0lf on 2005-07-25
Sorry about the length between installments.  For those of you who don't know, I was involved in a rather serious car crash and was hospitalized, and currently have a demolished leg.  

However, I'm doing better now, and am working on the Intermediate Guide, after getting multiple requests from a surprising amount of forum members. For any suggestions or ideas for topics to cover, feel free to email me at digitalsuicide [at] gmail [dot] com.  

Should have it out for you guys by Wednesday.

---

### Post by skyboy on 2005-07-25
Hope you'll get better soon because your guides are really usefull for newbies. Especially that often the same "simple" question come back. 
Great Job and take care

---

### Post by dataw0lf on 2005-07-25
[QUOTE=skyboy]Hope you'll get better soon because your guides are really usefull for newbies. Especially that often the same "simple" question come back. 
Great Job and take care[/QUOTE]

Thanks.  And thanks to everyone who cares enough to request the 'sequel'.  I was very pleased to see that this howto was so helpful for so many people.  It kinda gives you that 'oompf' to do another one ;)

---

### Post by erygon on 2005-07-28
Hi,

I have small problem, when I want my network connection started after boot, I need to type 4 commands.

dhclient
(Get ip address etc)

pon sauna1
(Open vpn connection)

route add -host x.x.x.x gw x.x.x.x
route add -net x.x.x.x netmask x.x.x.x dev ppp0
(Setup routes) 

How do I make these run automatically at boot or is there any config files where I can set routes?

---

### Post by Mr-F on 2005-07-28
Ok sorry if this is obvious but I've spent a couple of hours searching the web with no luck.  I was wondering if any of you couple possible point me in the right direction.  I should explain the situation.  I've got two ubuntu systems at home.  The first I install at home and everything is fine.  I have a network connection, it gets the IP address assigned to the mac address of the network card.  The second machine is being an absolute pain, won't pick up an ip address from the dhcp server.

I know the networking on this second machine works, since I install it at another location and set up all the different pieces of software such as samba, and updated the base system.  However, know that I have brought it home it just doesn't work.  I'm guess its something to do with ubuntu picking up the DNS at the other location "/etc/resolv.conf".  The question is how do I reconfigure the network settings so that it will work at home?  I've tried taking the entries from "/etc/resolv.conf" out and changing then by hand to the settings from my other machine, with no joy.  I've even used ifconfig -a eth0 192.167.7.5 netmask 255.255.255.0 which works until I reset the machine.

I was sure there was a way to run a reconfigure script/program but I completely stumped when it comes to finding what the command is.  Any ideas?

Oh I've also tried working through the network tools within the GUI with no joys.

---

### Post by Mr-F on 2005-07-28
Just in case someone else comes across this thread from google, I found the answer to my problem was fault network equipment.  In particular the switch, and I would therefore advise you to check your network.  In my case the switch was working for every other computer on the network, except this second linux box.  When I connected it directly to the router it picked up the IP address straight away.  When I swapped the switch with another one I had around it also worked.  So I'm guessing there is something wrong with the switch since the network card in the machine and this particular switch was working just over two weeks ago.

---

### Post by Scio on 2005-08-01
[QUOTE=erygon]Hi,

I have small problem, when I want my network connection started after boot, I need to type 4 commands.

dhclient
(Get ip address etc)

pon sauna1
(Open vpn connection)

route add -host x.x.x.x gw x.x.x.x
route add -net x.x.x.x netmask x.x.x.x dev ppp0
(Setup routes) 

How do I make these run automatically at boot or is there any config files where I can set routes?[/QUOTE]

I have the same problem with routing tables. Can anyone help?

---

### Post by Copter on 2005-08-09
dataw0lf - great howto :razz:. hope you are feeling better now.

```

route add default gw 10.0.0.1
```and let there be light!

thanks a lot! cant wait for the sequel :D

copter :]

---

### Post by Yeormom on 2006-03-13
Where is the magical file that keeps a static routing table?

---

### Post by geek.de.nz on 2006-06-24
I thought I know quite a bit about networking and linux, but I cannot get the following to work like I want it to:

I want to have a static local ip address for my Ubuntu 5.10 (custom kernel 2.6.16-suspend2).

I have set up debian before on the same network with the same gateway/router.

Here the config I'm aiming for:

router   10.0.0.11
local static ip  10.0.0.4/8


I got dhcp enabled on the router and my box with Ubuntu 5.10 and it works fine. But I use port-forwarding for my web-server I got running and for other little things. The annoying thing is that my ip keeps changing when I reboot or similar. So, every time I boot, I have to reconfigure my router. The funny thing is, that with other Linux versions, such as Debian it works with the same configuration.

Is it maybe an issue that I have vmware installed?

Here an output of 
```

# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:05:1C:01:7C:85
          inet addr:10.0.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1682309 (1.6 MiB)  TX bytes:461215 (450.4 KiB)
          Interrupt:11 Base address:0xb800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:73755 (72.0 KiB)  TX bytes:73755 (72.0 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:172.16.231.128  Bcast:172.16.231.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.120.128  Bcast:172.16.120.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
and
```
# netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.16.231.0    0.0.0.0         255.255.255.0   U         0 0          0 vmnet1
172.16.120.0    0.0.0.0         255.255.255.0   U         0 0          0 vmnet8
10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 eth0
0.0.0.0         10.0.0.11       0.0.0.0         UG        0 0          0 eth0
0.0.0.0         172.16.120.2    0.0.0.0         UG        0 0          0 vmnet8

```
when it's working.
and
```

eth0      Link encap:Ethernet  HWaddr 00:05:1C:01:7C:85
          inet addr:10.0.0.4  Bcast:10.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1685308 (1.6 MiB)  TX bytes:462483 (451.6 KiB)
          Interrupt:11 Base address:0xb800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:497 errors:0 dropped:0 overruns:0 frame:0
          TX packets:497 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:80019 (78.1 KiB)  TX bytes:80019 (78.1 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:172.16.231.128  Bcast:172.16.231.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.120.128  Bcast:172.16.120.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

# netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.16.231.0    0.0.0.0         255.255.255.0   U         0 0          0 vmnet1
172.16.120.0    0.0.0.0         255.255.255.0   U         0 0          0 vmnet8
10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 eth0
0.0.0.0         10.0.0.11       0.0.0.0         UG        0 0          0 eth0
0.0.0.0         172.16.120.2    0.0.0.0         UG        0 0          0 vmnet8

```
when it's not working

I think I have to let the vmnet1 and vmnet8 settings alone, otherwise networking wont work in the bridged networking of my virtual machines.

My virtual machines have ip addresses 
10.0.0.100
10.0.0.101
...
and they all work fine ('ping -c 1 google.com' gives ip etc). Windows, Linux, all work.

I used [http://howtoforge.com/perfect_setup_debian_sarge_p3]("http://howtoforge.com/perfect_setup_debian_sarge_p3") as a skeleton for my setup on the Ubuntu machine, but am never successful in pinging google when I set a static ip.

Also, I did put my correct nameservers into /etc/resolv.conf .

What am I missing? I thought Ubuntu is Debian based.

---

### Post by mellison on 2006-09-01
i am not able to access other systems in the network as well not able to connect to internet.i have set the ipaddresse and default gateway address

---

### Post by nick_austen on 2006-09-28
You seemed to be trying to create a default route to address 0.0.0.0. You might like to try 'route add default gw 192.168.1.1' or what ever your gateway's IP address is.

Also note that 'default' is just shorthand for '0.0.0.0'.

Oops - just noticed how old this was ... sorry.


Nick.

---

### Post by sriganeshs on 2006-10-02
Hi,
Thanks dataw0lf for the wonderful guide.

Well,I am using DHCP to connect to the internet. Eventhough yahoo.com and other sites can be opened through the browser, I cant Ping them. I had problems with activating my universe and multiverse, for which I had set configure proxy. But, how do I do something similar for Ping?

---

### Post by kipeloff on 2006-10-03
heh, very nice guide :D 

**sriganeshs**,
what do you mean by 'similar to Ping' ?
Tracerouter or 'tracepath' is similar (it uses the same protocol ICMP), but it shows routers, which packet passes to reach the destination.

Proxy goal to cache Internet object requests (commonly HTTP, FTP data), not ICMP packets.

---

### Post by dataw0lf on 2006-11-16
I'm back from the nether, and I'll be writing the sequel to this post in the next week.  Any specific requests?

---

### Post by Ennead on 2006-11-19
Your HOWTO is very good.  Glad you're going to continue, and hope you're fully recovered from your accident.

My network has 1 Winxp, 2 Win98se and 1 Ubuntu.  All of them can get on the internet, ping all the other boxes, and print to my printer server (ref:  [http://pigtail.net/LRP/printsrv/](http://pigtail.net/LRP/printsrv/)).
 The Win boxes can see each other but my favorite box can't see the other 3 and vice versa.  Someone just gave me an old P3, so I will soon have a second  Ubuntu box. \\:D/ 

The question that I can't seem to find an answer to is, how do I get them to share files?  What am I missing?  :-({|=    Is it something very basic?  Is this possibly something you're going to cover in your next HOWTO?

---

### Post by bemo on 2007-03-22
Thanks for the how to post. 
Now for my problem,
I am unable to connect through firefox, ssh or any other application.
I suspect that its a DNS linker problem. 

~$ ping -c 3 yahoo.com
PING yahoo.com (66.94.234.13) 56(84) bytes of data.
64 bytes from yahoo.com (66.94.234.13): icmp_seq=1 ttl=52 time=182 ms
64 bytes from yahoo.com (66.94.234.13): icmp_seq=2 ttl=52 time=182 ms
64 bytes from yahoo.com (66.94.234.13): icmp_seq=3 ttl=52 time=179 ms

--- yahoo.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 179.117/181.250/182.451/1.590 ms

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

I greatly appreciate everyone’s time in helping me.

---

### Post by warmachine000 on 2007-04-02
Ok, so I was looking at the basic part of the networking guide, and it had that list of a couple commands (ie ifconfig /etc/network/interfaces), it returns an error saying "error fetching interface information: Device not found." I think it's a matter of the interface not being configured correctly considering that when I look at the network statistics, it shows that packets are being sent and received. I am trying to network this with a Windows XP laptop, but when I look at the windows network stats, it only shows that packets are being sent. Any have any suggestions?

---

### Post by jmmcd on 2007-06-22
Hi all,

thanks to Javier for the network test script. I ran it today for the first time in ages and noticed a problem:

```
$ networktest.sh 
-e is not available! (please install netstat net-tools)
```

This is a small bug probably caused by a conflict between the built-in echo and the /bin/echo command. I fixed it by changing the "echo -e" to "/bin/echo -e" in this stanza near the top of the script:

```
# Check if all commands we need are available
# NOTE:  if using nslookup add "nslookup dnsutils"
( echo -e "netstat net-tools\nifconfig net-tools\nping netkit-ping\n\
arp net-tools\nip iproute\nhost bind9-host\nmktemp debianutils\nnc netcat" |
while read cmd package; do
if ! `which $cmd 2>/dev/null >&2`; then
	echo "$cmd is not available! (please install $package)" >&2
	exit 1
fi
done ) || exit 1
```

(I think there are multiple versions of the script floating around, so my apologies if this has already been fixed.)

---

### Post by AngeloB on 2007-12-06
Hi, 

I have a loptop, Compaq Parario c5000

I can't get it to do wifi or even get on my local network

can you help?

thanks

Angelo

---

### Post by nazrysamaratin on 2008-11-03
1.i have problem with my connection information i cant click at icon if   want to see my ip address ,subnet gateway.

2. i cant browse my modem Billion Bipac 5112s 192.168.1.254

3. if i set my modem in window from bridge mode to pppoe my connection internet not work ubuntu.

So anybody can help me to solve it. Sorry my bad english not my mother tongue

---

### Post by Zhukov on 2008-11-14
> **nazrysamaratin said:**
> 1.i have problem with my connection information i cant click at icon if   want to see my ip address ,subnet gateway.

2. i cant browse my modem Billion Bipac 5112s 192.168.1.254

3. if i set my modem in window from bridge mode to pppoe my connection internet not work ubuntu.

So anybody can help me to solve it. Sorry my bad english not my mother tongue

Hi there!

Could you please be a little bit more specific?

Also, this is quite an old thread :D

Best regards!

---

### Post by gasto on 2008-12-01
OK I really don't know what to do, I have been using Windows for too long and my mind has become to stuborn about it. 

So I have IP adress 192.168.0.1 (default I guess) for my router.
That should be my default gateway.

eth0 is the only ethernet adapter I find at the **network connections**

In this whole tutorial, there is no way you can view or test if your hardware is actually working. Because in that same PC with Windows it wasn't detecting the RJ45 cables with the router at the other side.

I really need some help. Ubuntu without internet connection seems useless(video driver from NVidia downloadble from their site, etc.)

---

### Post by liz589 on 2008-12-19
hi, i'm a newbie for networking, i got problem for home networking. i got 4 computers at home, one is running ubuntu 8.04 lts, the rest are running xp, among them is laptop using wireless which is old stuff. i got one linksys broadband router which is connected with 2 xps and 1 ubuntu, 3 xps can see eachother and share their folders, vnc is running perfect. the problem is ubuntu machine can ping 3 xp machines, but xps cannot see ubuntu machine. i tried ubuntu networking tools and network under places menu, i cannot see 3 xps in windows network which is empty. anybody can help me? i'm worried about that. thanks.

---

### Post by crgalindo on 2009-03-15
dataw0lf,
did you ever post the intermediate course?

---

### Post by jcorcione on 2010-01-21
I have a di624 router that i am trying to make it work like a range extender.  I am running ubuntu linux.  I am trying to connect to the eth01 but not getting any where, question is two fold.  1 how can i connect to the di624 router enabling what ever properties on the linux box and 2 how do i make the di624 more of a range extender.  btw i am connecting directly from the ethernet port on the pc to the lan port 1 on the wireless router.

thanks for reading this

ps still trying to get the Raylinktech usb  to be recognized but to no avail.. trying something different.

---

### Post by scrapmetal on 2010-09-09
Thanks for the 1st post.:p
Did you get well?, your link = 404 page not found.
Crash is for me life changing.
Encouraged enough to do the intermediate?:popcorn:

---

### Post by jesuscamp on 2012-12-06
Great article.

Thanks!

---

### Post by assen on 2013-02-28
Yes, great thread! But wanted to point out, please check also the hardware side. Had issue with network, connecting just at 10MB/s. Issue was, somehow broken cable, too many errors on the cable, so that was the reason why the nic was going down to 10MB/s. Changed cable and all was good.
Please check cables, ports on router, switch, cross-change cable and ports to check functionality. You get the point.
That's what i wanted to say about TS, do not forget the HW side ;)

Best regards

---

