---
title: "How to"
date: 2011-10-16
forum: Tutorials
---

### Post by narnie on 2011-10-16
Hello,

I wanted to use this thread to document the solution to a problems others might come across using network printers with iptables. I was surprised to find that a google search caused me to come up bupkis for information. I'm hopeful this will help someone.

My system(s) are setup with an raw iptables firewall (no UFW, Firestarter, GUFW, etc), Dansguardian, and privoxy to act as a contact filter with the added benefit of an inbound firewall to help protect the computer from the big, bad web.

I have heavily adapted (from ubuntu_ce_firewall) and commented on the below init script that I have in /etc/init.d/. Much thanks to Dangertux on ubuntuforums.org who helped me understand several of the iptable rules.

I could not get my network printer (An HP multifunctional Officejet 6500 series) to talk with my computer(s) with the firewall up.

In looking at the iptables logs, it turns out that I kept having udp activity between the network printer and the computer on port 5353. Unblocking tcp on port 631 and udp port 5353 in the filter INPUT chain allowed normal printing.

Here is my /etc/init.d/dansguardian_firewall script:

```

#!/bin/bash
### BEGIN INIT INFO
# Provides: dansgardian_firewall
# Required-Start: $remote_fs $syslog
# Required-Stop: $remote_fs $syslog
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: firewall
# Description: Start, stop or reload firewall.
### END INIT INFO
#heavily adapted from the ubuntu_ce_firewall script from an older version of Ubuntu Christian Edition

set -e

case "$1" in
	start)
		echo -e "\nStarting Dansguardian firewall .....\n"
		# Clears chains in filter table
		/sbin/iptables -F
		# Deletes any user-define chains
		/sbin/iptables -X
		# Clears chains in nat table
		/sbin/iptables -t nat -F
		# Deletes any user-defined chains in nat table
		/sbin/iptables -t nat -X
		# Clears chains in the mangle table (which is rarely using in SOHO)
		/sbin/iptables -t mangle -F
		# Deletes any user defined chains in mangle table
		/sbin/iptables -t mangle -X
		# Sets policy for filter FORWARD chain to accept all incoming/outgoing traffic
		/sbin/iptables -P FORWARD ACCEPT
		# Sets policy for filter OUTPUT table to accept all outgoing traffic
		/sbin/iptables -P OUTPUT ACCEPT
		# Prevents any tcp packets from any user except dansguardian from being accepted on 127.0.0.1:8118
		# thus bypassing dansguarding through to the proxy
		/sbin/iptables -A OUTPUT -d 127.0.0.1 -p tcp --dport 8118 -m owner ! --uid-owner dansguardian -j DROP
		# Changes any tcp packets over the localhost adapter from another IP number destined for port 8080
		# (where dansguardian listens) changing the source IP to localhost (127.0.0.1)
		/sbin/iptables -A POSTROUTING -t nat -o lo -p tcp --dport 8080 -j SNAT --to 127.0.0.1

		## This section is needed if printing to a network printing over Internet Printing Protocol (IPP) with CUPS
		## needing tcp port 631 and udp 5353 open
		/sbin/iptables -A INPUT -p tcp --dport 631 -j ACCEPT
#		/sbin/iptables -A OUTPUT -p tcp --sport 631 -j ACCEPT		#enable this if OUTPUT policy is DROP
		/sbin/iptables -A INPUT -p udp --dport 5353 -j ACCEPT
#		/sbin/iptables -A OUTPUT -p udp --sport 5353 -j ACCEPT		#enable this if OUTPUT policy is DROP
		## End IPP/CUPS section

		# This does the magic directing any tcp packet NOT from root to any IP number that is NOT localhost
		# destined to port 80 (web site ports) redirecting it to port 8080 where dansguardian is listening
		/sbin/iptables -A OUTPUT -t nat ! -d 127.0.0.1 -p tcp --dport 80 -m owner ! --uid-owner root -j REDIRECT --to-ports 8080
		# Sets the policy for all INPUT packets to be dropped setting up good security for the computer
		# protecting it from the outside world.
		/sbin/iptables -P INPUT DROP
		# This is allowing all packets in to the localhost adapter adapter to be accepted
		# (which is needed by the some programs on the computer to be able to communicate)
		/sbin/iptables -A INPUT -i lo -j ACCEPT
		# This causes all packets INTO the computer that are related to or extablished with an OUTPUT
		# packet into the system (such as a response from a web host)
		/sbin/iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

		## Open port for ssh server (22), web server (80), and mail server (25)
		/sbin/iptables -A INPUT -p tcp --dport 22 -m state --state NEW -j ACCEPT
		#/sbin/iptables -A INPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT
		#/sbin/iptables -A INPUT -p tcp --dport 25 -m state --state NEW -j ACCEPT

		## Uncomment below to open NSF port, edit the port accoring actual setting
		## the mountd (32771) and lockmanager port (4045) must be set to be a
		## static port or NFS will not work through the firewall (it is normally dynamically assigned)
		## see this thread for more info on how to do this http://ubuntuforums.org/showthread.php?t=1263114
		/sbin/iptables -A INPUT -p tcp --dport 111 -m state --state NEW -j ACCEPT
		/sbin/iptables -A INPUT -p udp --dport 111 -m state --state NEW -j ACCEPT
		/sbin/iptables -A INPUT -p tcp --dport 2049 -m state --state NEW -j ACCEPT
		/sbin/iptables -A INPUT -p udp --dport 2049 -m state --state NEW -j ACCEPT
		/sbin/iptables -A INPUT -p tcp --dport 4045 -m state --state NEW -j ACCEPT
		/sbin/iptables -A INPUT -p udp --dport 4045 -m state --state NEW -j ACCEPT
		/sbin/iptables -A INPUT -p tcp --dport 32771 -m state --state NEW -j ACCEPT
		/sbin/iptables -A INPUT -p udp --dport 32771 -m state --state NEW -j ACCEPT
		## Open ports for NSF end

		#Accept Ping request
		/sbin/iptables -A INPUT -p icmp -j ACCEPT

		## Drop other packets, Logging, and closing firewall.
		/sbin/iptables -A INPUT -d 255.255.255.255/0.0.0.255 -j DROP	#drop broadcast packets
		/sbin/iptables -A INPUT -d 224.0.0.1 -j DROP			#drop multicast packets
		/sbin/iptables -A INPUT -j LOG					#log all other packets making it through
		/sbin/iptables -A INPUT -j REJECT				#reject all other packets sending it through sending a tcp RST packet back
	;;

	stop)
		echo -e "\nFlushing firewall and setting default policies to ACCEPT\n"
		/sbin/iptables -F
		/sbin/iptables -X
		/sbin/iptables -t nat -F
		/sbin/iptables -t nat -X
		/sbin/iptables -t mangle -F
		/sbin/iptables -t mangle -X
		/sbin/iptables -P INPUT ACCEPT
		/sbin/iptables -P FORWARD ACCEPT
		/sbin/iptables -P OUTPUT ACCEPT
	;;

	status)
		echo "FILTER POLICY"
		/sbin/iptables -L OUTPUT 
		/sbin/iptables -L INPUT
		echo ; echo "NAT POLICY"
		/sbin/iptables -t nat -L OUTPUT
		/sbin/iptables -t nat -L POSTROUTING
	;;

	restart|force-reload)
		$0 stop
		$0 start
	;;

	*)
		echo "Usage: $0 {start|stop|restart|force-reload|status}"
		exit 1
	;;
esac

```

Hopefully this might clear up some problems others might have or will have in the future.

Kind Regards,
Narnie

---

### Post by Dangertux on 2011-10-20
Great job Narnie :-)

While I am thankful for the credit, the community should be thankful for the hard work you put together in creating this, I am sure many can benefit from this.

Thanks for the opportunity to help, I learned a lot as well :-)

---

