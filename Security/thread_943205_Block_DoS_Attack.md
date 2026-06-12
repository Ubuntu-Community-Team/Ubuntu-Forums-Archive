---
title: "Block DoS Attack"
date: 2008-10-10
forum: Security
---

### Post by Diego507PTY on 2008-10-10
Hello!, I have ubuntu server and running Half-Life Dedicated Server in UPD port 27015,  my server is attacked with UDP Flood on port 27015 and collapses the internet conection how to filter the upd packets in port 27015 to stop flood and ban ip of the attacker, Thanks.

---

### Post by mregister on 2008-10-10
Are you behind a firewall? You can block IP's that way or use iptables

---

### Post by hyper_ch on 2008-10-10
are you behind a router? If so, just close that port there... 

or if you are not behind a router run

```

sudo ufw deny 27015/udp

```

or if it all comes from one IP

```

sudo ufw deny from IPADDRESS

```

---

### Post by Nepherte on 2008-10-10
I suppose you can't block the udp port if you want people to join your half life server.

---

### Post by Diego507PTY on 2008-10-10
Hello!, Thanks for reply

@mregister 
I Don't have firewall or router,iptable is my option.

@hyper_ch
The port 27015 is for HLDS, I can't block this port.

@Nepherte 
Correct.

I find metod for filter the packet in the port 27015 for stop the flood.

[UDP Flood Description]("http://en.wikipedia.org/wiki/UDP_flood_attack")

---

### Post by hyper_ch on 2008-10-10
does hlds use udp or tcp?

---

### Post by Diego507PTY on 2008-10-10
Udp

---

### Post by Diego507PTY on 2008-10-10
i found this code in a blog, could someone help me?
> Sep 15, 2008
Prevent DoS attack in Linux using IPTABLES 
A major problem facing by mail server admin is DOS (Deniel Of Service) attack. Hackers will try to mess up with the most popular ports of a UNIX/LINUX machines. We can prevent this my writing an IPTABLE rule in the server. The working is ,if some one is trying make connection continuously through a specified port the rule will block the IPADDRESS permanently. Here I am stating the securing of PORT 25 (SMTP) here you can use your own 

iptables -I INPUT -p tcp --dport 25 -i eth0 -m state --state NEW -m recent --set

iptables -I INPUT -p tcp --dport 25 -i eth0 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 -j DROP

This will Block all the IP ADDRESS which will make connection to port 25 continuously within ie 4 SMTP connection within 60 seconds. You can change PORT,INTERVALs here. 

---

### Post by djhedges on 2008-10-12
I could write a rule for iptables to limit a TCP Syn flood but I'm not sure how to do that for UDP without blocking legitimate users since UDP is connectionless.

You could tweak around with something like
```
iptables -A INPUT -p udp --dport 27015 --limit 10/s --limit-burst 20 -j Drop
```
--limit 10/s will limit the clients to only 10 packets per second while 
--limit will allow an inital 20 packet burst

You could use wireshark to capture some packets as you game and filter for that port.  Then just count the # of packets it capture over a given time to better tweak those values.

---

### Post by Diego507PTY on 2008-10-28
hello, I found a script that can work, but I'm not sure
please guys help me to find the line code to stop the flooding

```
#!/bin/sh

#
#	debugging
#
set -x


#
# binaries
#
TC=/sbin/tc
IPTABLES=/sbin/iptables


#
#	variables
#
WIFIFACE=ath0
INETFACE=eth2
LANIFACE=eth3
CHANNEL=9
ESSID="doom"
KEY="000A-BABE-0A7E-DEAD-BEEF-3141-59"
WIPADDR="10.1.1.1"
WNETMASK="255.255.255.0"
WBROADCAST="10.1.1.255"
WNETWORK="10.1.1.0"
DNLD=150Kbit   # DOWNLOAD Limit
DWEIGHT=15Kbit # DOWNLOAD Weight Factor ~ 1/10 of DOWNLOAD Limit
UPLD=12Kbit    # UPLOAD Limit
UWEIGHT=1Kbit  # UPLOAD Weight Factor


#
#	cleanup if needed
#
function cleanup() {
	/etc/init.d/dhcp3-server stop
}


#
#	Set up the wireless card
#
function wifi_up() {
	wlanconfig ${WIFIFACE} destroy # needed for madwifi thingy
	sleep 1
	wlanconfig ${WIFIFACE} create wlandev wifi0 wlanmode ap
	sleep 1
	iwconfig ${WIFIFACE} mode master
	sleep 1
	ifconfig ${WIFIFACE} ${WIPADDR} broadcast ${WBROADCAST} netmask ${WNETMASK}
	sleep 1
	iwconfig ${WIFIFACE} essid ${ESSID}
	sleep 1
	iwconfig ${WIFIFACE} channel ${CHANNEL}
	sleep 1
	iwconfig ${WIFIFACE} key ${KEY}
}


#
#	dhcpd
#
function dhcp()	{
	#dhcpd3 -pf /var/run/dhcpd.run
	/etc/init.d/dhcp3-server start
}


#
#  traffic control
#
function tc_start() {
	$TC qdisc add dev $WIFIFACE root handle 11: cbq bandwidth 100Mbit avpkt 1000 mpu 64
	$TC class add dev $WIFIFACE parent 11:0 classid 11:1 cbq rate $DNLD weight $DWEIGHT allot 1514 prio 1 avpkt 1000 bounded
	$TC filter add dev $WIFIFACE parent 11:0 protocol ip handle 4 fw flowid 11:1

	$TC qdisc add dev $INETFACE root handle 10: cbq bandwidth 10Mbit avpkt 1000 mpu 64
	$TC class add dev $INETFACE parent 10:0 classid 10:1 cbq rate $UPLD weight $UWEIGHT allot 1514 prio 1 avpkt 1000 bounded
	$TC filter add dev $INETFACE parent 10:0 protocol ip handle 3 fw flowid 10:1
}
function tc_stop() {
	$TC qdisc del dev $WIFIFACE root
	$TC qdisc del dev $INETFACE root
}
function tc_show() {
	echo ""
	echo "$WIFIFACE:"
	$TC qdisc show dev $WIFIFACE
	$TC class show dev $WIFIFACE
	$TC filter show dev $WIFIFACE
	echo ""

	echo "$INETFACE:"
	$TC qdisc show dev $INETFACE
	$TC class show dev $INETFACE
	$TC filter show dev $INETFACE
	echo ""
}  


#
#	firewall
#
function firewall() {
	echo 1 > /proc/sys/net/ipv4/ip_forward
	# Disable response to broadcasts.
	echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
	# Don't accept source routed packets.
	echo 0 > /proc/sys/net/ipv4/conf/all/accept_source_route
	# Disable ICMP redirect acceptance.
	echo 0 > /proc/sys/net/ipv4/conf/all/accept_redirects
	# Enable bad error message protection
	echo 1 > /proc/sys/net/ipv4/icmp_ignore_bogus_error_responses
	# Log spoofed packets, source routed packets, redirect packets
	echo 1 > /proc/sys/net/ipv4/conf/all/log_martians

	$IPTABLES -F
	$IPTABLES -X
	$IPTABLES -Z

	$IPTABLES -P INPUT ACCEPT
	$IPTABLES -P OUTPUT ACCEPT
	$IPTABLES -P FORWARD DROP

	# Loopback - Allow unlimited traffic
	$IPTABLES -A INPUT -i lo -j ACCEPT
	$IPTABLES -A OUTPUT -o lo -j ACCEPT

	# [COLOR="Red"]Drop all invalid packets[/COLOR]
	$IPTABLES -A INPUT -m state --state INVALID -j DROP
	$IPTABLES -A OUTPUT -m state --state INVALID -j DROP
	$IPTABLES -A FORWARD -m state --state INVALID -j DROP

	# Masquerade
	$IPTABLES -t nat -A POSTROUTING -o $INETFACE -j MASQUERADE

	# SYN-Flooding Protection
	$IPTABLES -N syn-flood
	$IPTABLES -A syn-flood -m limit --limit 1/second --limit-burst 4 -j RETURN
	$IPTABLES -A syn-flood -j DROP

	# [COLOR="Red"]UDP-Flooding protection[/COLOR]
	$IPTABLES -N udp-flood
	$IPTABLES -A udp-flood -m limit --limit 4/second --limit-burst 4 -j RETURN
	$IPTABLES -A udp-flood -j DROP

	# INPUT filters
	$IPTABLES -A INPUT -i $WIFIFACE -p tcp --tcp-flags  SYN,RST,ACK,FIN SYN,ACK -j syn-flood # SYN flood
	# Make sure that new TCP connections are SYN packets
	$IPTABLES -A INPUT -i $WIFIFACE -p tcp ! --syn -m state --state NEW -j DROP
	$IPTABLES -A INPUT -i $WIFIFACE -p udp -j udp-flood
	$IPTABLES -A INPUT -i $WIFIFACE -f -j DROP # drop fragments

	# Forwarding rules
	$IPTABLES -A FORWARD -i $WIFIFACE -s 10.1.1.200 -j ACCEPT # allow kali
	$IPTABLES -A FORWARD -i $WIFIFACE -s 10.1.1.3 -j ACCEPT # allow kali
	$IPTABLES -A FORWARD -i $WIFIFACE -s 10.1.1.2 -j ACCEPT # allow vorian
	$IPTABLES -A FORWARD -i $WIFIFACE -s ! 10.1.1.0/24 -j DROP # must be from network
	$IPTABLES -A FORWARD -i $WIFIFACE -d 192.168.2.1 -j ACCEPT # access router
	$IPTABLES -A FORWARD -i $WIFIFACE -d 192.168.2.0/24 -j DROP # drop for local network
	$IPTABLES -A FORWARD -i $WIFIFACE -p tcp ! --syn -m state --state NEW -j DROP
	$IPTABLES -A FORWARD -i $WIFIFACE -p tcp --syn -j syn-flood # SYN flood
	$IPTABLES -A FORWARD -i $WIFIFACE -p udp -j udp-flood #[COLOR="Red"] UDP flood[/COLOR]
	$IPTABLES -A FORWARD -i $WIFIFACE -f -j DROP
	$IPTABLES -A FORWARD -i $WIFIFACE -j ACCEPT
	$IPTABLES -A FORWARD -o $WIFIFACE -j ACCEPT
	
	$IPTABLES -nvL
}


#
#	core script
#
case "$1" in
	start)
		cleanup
		sleep 1
		wifi_up
		sleep 1
		dhcp
		sleep 1
		firewall
	;;
	stop)
		cleanup
	;;
	restart)
		cleanup
		sleep 1
		wifi_up
		sleep 1
		dhcp
		sleep 1
		# restart tc
		tc_stop
		sleep 1
		tc_start
		# firewall
		firewall
	;;
	reload)
		cleanup
		sleep 1
		dhcp
		sleep 1
		# restart tc
		tc_stop
		sleep 1
		tc_start
		# firewall
		firewall
	;;
	*)
		echo "Usage is: $0 {start|stop|restart|reload}"
	;;
esac
exit 0



```
[source](source)

---

### Post by Diego507PTY on 2008-11-04
server@linux:~$ iptables -A INPUT -p udp --dport 27015 --limit 10/s --limit-burst 20 -j Drop
iptables v1.4.0: Unknown arg `--limit'
Try `iptables -h' or 'iptables --help' for more information.

impossible block udp flood?

---

### Post by Kinstonian on 2008-11-04
> **Diego507PTY said:**
> server@linux:~$ iptables -A INPUT -p udp --dport 27015 --limit 10/s --limit-burst 20 -j Drop
iptables v1.4.0: Unknown arg `--limit'
Try `iptables -h' or 'iptables --help' for more information.

impossible block udp flood?

Try this:

iptables -A INPUT -p udp --dport 27015 **-m limit** --limit 10/s --limit-burst 20 -j Drop

Edit:  I just saw what you're trying to do.  The above command will ruin your HL server until you remove that rule.  Perhaps you should modify the rule to only limit **new** UDP connections.

However, the problem is with the way UDP works.  From what I can tell, this UDP DoS attack (if that's what it is) is trying to consume bandwidth and overwhelm your network card.  It's not trying to overwhelm your OS like a SYN flood.  So by blocking this UDP traffic on the server itself, you're really blocking it after the damage has been done.  You want to block it or do rate limiting upstream at your ISP.

---

### Post by wineman on 2009-03-23
> **Diego507PTY said:**
> hello, I found a script that can work, but I'm not sure
please guys help me to find the line code to stop the flooding


dude this firewall is perfect, but still doesn't have sufficient DoS protection. THe 2 lines above in Kinstonian's post are better.

---

