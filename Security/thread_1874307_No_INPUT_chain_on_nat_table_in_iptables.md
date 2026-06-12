---
title: "No INPUT chain on nat table in iptables"
date: 2011-11-02
forum: Security
---

### Post by narnie on 2011-11-02
Hello,

I'm having problem with an iptables rule. It seems that on one of two systems on the nat table, the INPUT chain doesn't exist for some strange reason.

I get the error below:

```

# iptables -t nat -A INPUT -j ACCEPT
iptables: No chain/target/match by that name.

```

Here is my kernal:

```

# uname -a
Linux dell-desktop 2.6.32-5-amd64 #1 SMP Mon Mar 7 21:35:22 UTC 2011 x86_64 GNU/Linux

```

I have two systems that I have installed exactly that same (at least so I thought). Only one will throw the above error. The good system shows:

```

# iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination

```

However, the offending system shows:

```

# iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

As far as loaded modules different that I looked for on the good system :

```

# lsmod| grep ip
ipt_REJECT             12465  0 
ipt_LOG                12605  0 
ipt_REDIRECT           12471  0 
iptable_mangle         12536  0 
iptable_nat            12928  0 
nf_nat                 18012  2 ipt_REDIRECT,iptable_nat
nf_conntrack_ipv4      18081  3 iptable_nat,nf_nat
nf_conntrack           55903  5 xt_conntrack,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12483  1 nf_conntrack_ipv4
iptable_filter         12536  0 
ip_tables              21818  3 iptable_mangle,iptable_nat,iptable_filter
x_tables               18839  11 xt_conntrack,ipt_REJECT,ipt_LOG,xt_state,ipt_REDIRECT,xt_tcpudp,xt_owner,iptable_mangle,iptable_nat,iptable_filter,ip_tables

```

Bad system:

```

# lsmod | grep ip
ipt_REJECT              1953  0 
ipt_LOG                 4518  0 
ipt_REDIRECT            1111  0 
iptable_mangle          2817  0 
iptable_nat             4299  0 
nf_nat                 13388  2 ipt_REDIRECT,iptable_nat
nf_conntrack_ipv4       9833  3 iptable_nat,nf_nat
nf_conntrack           46535  4 xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1139  1 nf_conntrack_ipv4
iptable_filter          2258  0 
ip_tables              13899  3 iptable_mangle,iptable_nat,iptable_filter
x_tables               12845  8 ipt_REJECT,ipt_LOG,xt_state,ipt_REDIRECT,xt_tcpudp,xt_owner,iptable_nat,ip_tables

```

Good system:

```

# lsmod| grep xt
xt_conntrack           12599  0 
xt_state               12503  0 
xt_tcpudp              12527  0 
xt_owner               12423  0 
nf_conntrack           55903  5 xt_conntrack,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
x_tables               18839  11 xt_conntrack,ipt_REJECT,ipt_LOG,xt_state,ipt_REDIRECT,xt_tcpudp,xt_owner,iptable_mangle,iptable_nat,iptable_filter,ip_tables
ext3                  112218  2 
jbd                    41698  1 ext3
mbcache                12930  1 ext3

```

Bad system:

```

# lsmod |grep xt
xt_state                1303  0 
xt_tcpudp               2319  0 
xt_owner                1063  0 
nf_conntrack           46535  4 xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
x_tables               12845  8 ipt_REJECT,ipt_LOG,xt_state,ipt_REDIRECT,xt_tcpudp,xt_owner,iptable_nat,ip_tables
ext3                  106518  2 
jbd                    37085  1 ext3
mbcache                 5050  1 ext3

```

The only thing different is on the offending system xt_conntrack is not loaded. Manually loading this module does not fix the issue.

Could someone please tell me how to get the INPUT chain on my nat table?

Thanks,
Narnie

---

### Post by emiller12345 on 2011-11-02
the NAT table only has the OUTPUT, PREROUTING, and POSTROUTING chains associated with it by default.  if you do a ...```
man iptables
``` you can see what chains are available for each table.
on the computer with iptables -t nat -L which has the INPUT chain, it's possible that this is an added chain. I think a ```
iptables -t nat -X
``` command should wipe out any user generated chains in the nat table

---

### Post by narnie on 2011-11-02
> **emiller12345 said:**
> the NAT table only has the OUTPUT, PREROUTING, and POSTROUTING chains associated with it by default.  if you do a ...```
man iptables
``` you can see what chains are available for each table.
on the computer with iptables -t nat -L which has the INPUT chain, it's possible that this is an added chain. I think a ```
iptables -t nat -X
``` command should wipe out any user generated chains in the nat table

This isn't the case. There is an INPUT on the nat tables. It runs fine on my one machine (doing exactly what I need it to do) when I do:

```

# iptables -t nat -F
# iptables -t nat -X
# iptables -t nat -A INPUT -s 192.168.1.1 -p tcp -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
# iptables -t nat -nvL
Chain PREROUTING (policy ACCEPT 3 packets, 786 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 3 packets, 786 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       192.168.1.1          0.0.0.0/0            ctstate RELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT 10 packets, 1532 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 10 packets, 1532 bytes)
 pkts bytes target     prot opt in     out     source               destination
```

I have no user-defined chains.

Do a google search for "iptables -t nat -A INPUT" and "iptables -A INPUT -t nat" and you'll find other sites using the iptables -t nat -A INPUT table/chain such as [http://lists.debian.org/debian-firewall/2003/06/msg00085.html]("http://lists.debian.org/debian-firewall/2003/06/msg00085.html")

My full iptables rules are:

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

FIREWALL_DIR="dansguardian_firewall"
FIREWALL_NAME="Dansguardian Firewall"
IPTABLES="/sbin/iptables"

case "$1" in
	start)
		echo -e "\nStarting $FIREWALL_NAME .....\n"
		# Clears chains in filter table
		$IPTABLES -F
		# Deletes any user-define chains
		$IPTABLES -X
		# Clears chains in nat table
		$IPTABLES -t nat -F
		# Deletes any user-defined chains in nat table
		$IPTABLES -t nat -X
		# Clears chains in the mangle table (which is rarely using in SOHO)
		$IPTABLES -t mangle -F
		# Deletes any user defined chains in mangle table
		$IPTABLES -t mangle -X
		# Sets policy for filter FORWARD chain to accept all incoming/outgoing traffic
		$IPTABLES -P FORWARD ACCEPT
		# Sets policy for filter OUTPUT table to accept all outgoing traffic
		$IPTABLES -P OUTPUT ACCEPT

		# Check for banned users and ban them from net access
		if [ -r /etc/$FIREWALL_DIR/banned_users ]; then
			. /opt/$FIREWALL_DIR/ban_users_from_net
		fi

		# Checks to see if you are on a home router and if so
		# bypasses Dansguardian/privoxy to home router (change number
		# if number not 192.168.1.1).
		GATEWAY=`route -n|grep "^0.0.0.0."|awk '{print $2}'`
		GATEWAY_8=`echo $GATEWAY|awk -F. '{print $1}'`
		if [ "$GATEWAY_8" -eq 192 ]; then
			$IPTABLES -t nat -A INPUT -s $GATEWAY -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
			$IPTABLES -t nat -A OUTPUT -d $GATEWAY -m conntrack --ctstate NEW -j ACCEPT
		fi

		# Prevents any tcp packets from any user except dansguardian from being accepted on 127.0.0.1:8118
		# thus bypassing dansguarding through to the proxy
		$IPTABLES -A OUTPUT -d 127.0.0.1 -p tcp --dport 8118 -m owner ! --uid-owner dansguardian -j DROP
		# Changes any tcp packets over the localhost adapter from another IP number destined for port 8080
		# (where dansguardian listens) changing the source IP to localhost (127.0.0.1)
		$IPTABLES -A POSTROUTING -t nat -o lo -p tcp --dport 8080 -j SNAT --to 127.0.0.1

		## This section is needed if printing to a network printing over Internet Printing Protocol (IPP) with CUPS
		## needing tcp port 631 and udp 5353 open
		$IPTABLES -A INPUT -p tcp --dport 631 -j ACCEPT
#		$IPTABLES -A OUTPUT -p tcp --sport 631 -j ACCEPT		#enable this if OUTPUT policy is DROP
		$IPTABLES -A INPUT -p udp --dport 5353 -j ACCEPT
#		$IPTABLES -A OUTPUT -p udp --sport 5353 -j ACCEPT		#enable this if OUTPUT policy is DROP
		## End IPP/CUPS section

		# This does the magic directing any tcp packet NOT from root to any IP number that is NOT localhost
		# destined to port 80 (web site ports) redirecting it to port 8080 where dansguardian is listening
		$IPTABLES -A OUTPUT -t nat ! -d 127.0.0.1 -p tcp --dport 80 -m owner ! --uid-owner root -j REDIRECT --to-ports 8080
		# Sets the policy for all INPUT packets to be dropped setting up good security for the computer
		# protecting it from the outside world.
		$IPTABLES -P INPUT DROP
		# This is allowing all packets in to the localhost adapter adapter to be accepted
		# (which is needed by the some programs on the computer to be able to communicate)
		$IPTABLES -A INPUT -i lo -j ACCEPT
		# This causes all packets INTO the computer that are related to or extablished with an OUTPUT
		# packet into the system (such as a response from a web host)
		$IPTABLES -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT

		## Open port for ssh server (22), web server (80), and mail server (25)
		$IPTABLES -A INPUT -p tcp --dport 50505 -m conntrack --ctstate NEW -j ACCEPT
		#$IPTABLES -A INPUT -p tcp --dport 80 -m conntrack --ctstate NEW -j ACCEPT
		#$IPTABLES -A INPUT -p tcp --dport 25 -m conntrack --ctstate NEW -j ACCEPT

		## Uncomment below to open NSF port, edit the port accoring actual setting
		## the mountd (32771) and lockmanager port (4045) must be set to be a
		## static port or NFS will not work through the firewall (it is normally dynamically assigned)
		## see this thread for more info on how to do this http://ubuntuforums.org/showthread.php?t=1263114
		$IPTABLES -A INPUT -p tcp --dport 111 -m conntrack --ctstate NEW -j ACCEPT
		$IPTABLES -A INPUT -p udp --dport 111 -m conntrack --ctstate NEW -j ACCEPT
		$IPTABLES -A INPUT -p tcp --dport 2049 -m conntrack --ctstate NEW -j ACCEPT
		$IPTABLES -A INPUT -p udp --dport 2049 -m conntrack --ctstate NEW -j ACCEPT
		$IPTABLES -A INPUT -p tcp --dport 4045 -m conntrack --ctstate NEW -j ACCEPT
		$IPTABLES -A INPUT -p udp --dport 4045 -m conntrack --ctstate NEW -j ACCEPT
		$IPTABLES -A INPUT -p tcp --dport 32771 -m conntrack --ctstate NEW -j ACCEPT
		$IPTABLES -A INPUT -p udp --dport 32771 -m conntrack --ctstate NEW -j ACCEPT
		## Open ports for NSF end

		#Accept Ping request
		$IPTABLES -A INPUT -p icmp -j ACCEPT

		## Drop other packets, Logging, and closing firewall.
		$IPTABLES -A INPUT -d 255.255.255.255/0.0.0.255 -j DROP	#drop broadcast packets
		$IPTABLES -A INPUT -d 224.0.0.1 -j DROP			#drop multicast packets
		$IPTABLES -A INPUT -j LOG --log-prefix "iptables INPUT drop: "	#log all other packets making it through to this point
		$IPTABLES -A INPUT -j REJECT				#reject all other packets sending it through sending a tcp RST packet back
	;;

	stop)
		echo -e "\nFlushing $FIREWALL_NAME and setting default policies to ACCEPT\n"
		$IPTABLES -F
		$IPTABLES -X
		$IPTABLES -t nat -F
		$IPTABLES -t nat -X
		$IPTABLES -t mangle -F
		$IPTABLES -t mangle -X
		$IPTABLES -P INPUT ACCEPT
		$IPTABLES -P FORWARD ACCEPT
		$IPTABLES -P OUTPUT ACCEPT
	;;

	status)
		echo "FILTER POLICY"
		$IPTABLES -L OUTPUT 
		$IPTABLES -L INPUT
		echo ; echo "NAT POLICY"
		$IPTABLES -t nat -L OUTPUT
		$IPTABLES -t nat -L POSTROUTING
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

Bear in mind this iptables script runs find on one computer, and dies at the -t nat -A INPUT on the other.

Regards,
Narnie

---

### Post by emiller12345 on 2011-11-02
Wow, that's strange. Which version of iptables are you runninng?
```
iptables --version
```

---

### Post by narnie on 2011-11-02
> **emiller12345 said:**
> Wow, that's strange. Which version of iptables are you runninng?
```
iptables --version
```

You are so very right! It is strange. I don't understand why programmers have so many undocumented features. If I go to the trouble to provide a feature, I want people to know about it.

iptables v1.4.12

My man page just shows 3 chains, too (excluding the INPUT).

Regards,
Narnie

---

### Post by narnie on 2011-11-02
> **emiller12345 said:**
> Wow, that's strange. Which version of iptables are you runninng?
```
iptables --version
```

This provides some more insight:

[http://serverfault.com/questions/245564/iptables-built-in-input-chain-in-nat-table]("http://serverfault.com/questions/245564/iptables-built-in-input-chain-in-nat-table") which references [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=c68cd6cc21eb329c47ff020ff7412bf58176984e]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=c68cd6cc21eb329c47ff020ff7412bf58176984e") which added the INPUT chain.

Cheerio,
Narnie

---

### Post by emiller12345 on 2011-11-03
It looks like there might be a new way of NAT'ing.  the old way of doing SNAT/DNATI think is something like this
```
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to $IP 
iptables -t nat -A PREROUTING -d $IP1 -j DNAT --to-destination $IP2  
```
I'll need to look into the nat INPUT chain a bit more. From what you found, it looks like its used when your dealing with two networks that have the same ip/netmask range, or ones that are overlapping.

---

### Post by narnie on 2011-11-03
> **emiller12345 said:**
> It looks like there might be a new way of NAT'ing.  the old way of doing SNAT/DNATI think is something like this
```
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to $IP 
iptables -t nat -A PREROUTING -d $IP1 -j DNAT --to-destination $IP2  
```
I'll need to look into the nat INPUT chain a bit more. From what you found, it looks like its used when your dealing with two networks that have the same ip/netmask range, or ones that are overlapping.

I'm using it in this situation to allow access to the hardware router at 192.168.1.1 on my home lan. Just using filter table input and output wouldn't get around sending everything through my dansguardian/privoxy setup. It is painfully slow getting the router's html code through this setup, so I was trying to bypass it. I have subsequently found that 

```
iptables -t nat -A PREROUTING -p tcp -m conntrack --ctstate ESTABLISHED,RELATED
```

Does what I need, too, and allows me to use this script on older kernels such as my kids' Ubuntu Netbook Remix 9.04 LTS systems.

I also realized that in fixing a broken package, it scaled me back from 

```
# uname -a
Linux gateway-laptop 2.6.38-2-amd64 #1 SMP Sun May 8 13:51:57 UTC 2011 x86_64 GNU/Linux
```

to the 2.6.32.x kernel noted above which doesn't have the INPUT chain. So, I'm going to mark this as solved.

Thanks for joining the ride with me   :)

Regards,
Narnie

---

