---
title: "My simple, fast and... er effective Ubuntu firewall."
date: 2008-02-27
forum: Security Discussions
---

### Post by Kernel_Krunch on 2008-02-27
Hello everyone!

Ok so I tried very hard to find a simple desktop firewall that was fast, resource friendly and simple... tried and failed, so I wrote my own.

Edit: Hardy has `ufw` which is better then this... I'll leave it up anyways ;)

At the very last code post is the install script which builds a configure script that runs on machine start up.  The configure script looks like this:
```
#! /bin/bash
# This is the startup script for a iptable ruleset

if [ "$1" = "restart" ]
then
iptables -F
iptables -X
fi
if [ "$1" = "start" ]
then
/sbin/depmod -a
/sbin/modprobe ip_tables
/sbin/modprobe iptable_filter
/sbin/modprobe ipt_state
/sbin/modprobe ip_conntrack
echo 1 > /proc/sys/net/ipv4/ip_dynaddr
echo 1 > /proc/sys/net/ipv4/conf/all/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/all/proxy_arp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
echo 1 > /proc/sys/net/ipv4/tcp_syncookies
echo 0 > /proc/sys/net/ipv4/conf/all/accept_source_route
echo 0 > /proc/sys/net/ipv4/conf/all/accept_redirects
echo 0 > /proc/sys/net/ipv4/conf/all/send_redirects
echo 1 > /proc/sys/net/ipv4/conf/all/secure_redirects
fi
if [ "$1" = "stop" ]
then
exit
fi
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP
iptables -N tcp_chain
iptables -A tcp_chain -p tcp --tcp-flags SYN,ACK SYN,ACK -m state --state NEW -m limit --limit 5/second -j REJECT --reject-with tcp-reset
iptables -N udp_chain
iptables -A udp_chain -p udp -s 0/0 --sport 67 --dport 68 -j ACCEPT
iptables -N icmp_chain
iptables -A INPUT -p ALL -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p ALL -m state --state INVALID -j DROP
iptables -A INPUT -p TCP -j tcp_chain
iptables -A INPUT -p UDP -j udp_chain
iptables -A INPUT -p ICMP -j icmp_chain
iptables -A tcp_chain -j DROP
iptables -A udp_chain -j DROP
iptables -A icmp_chain -j DROP

```

If you enable local access the following rules will be included 
```
iptables -I INPUT 3 -i lo -s 127.0.0.1 -j ACCEPT
iptables -I FORWARD -i lo -s 127.0.0.1 -j ACCEPT
```


Cut and paste into text editor, save as InstallFire.sh... make it executable with chmod a+x and run it as 'root'.

```
#! /bin/bash

#  Firewaller Sub-script: an Iptables rule set builder and installer script for most linux/gnu platforms that have the iptables module.


## Important network values

# Interface details.
NetCard=""  		# The system name of your network card.  Left empty so that all rules apply to all external interfaces.

LocalAccess=""	# Default is no for performance.

# Internet details.
# *ToDo*  allow DHCP script to alter this values after success...

DHCP_server="0/0"  	#The IP address of your DHCP server, often the default gateway.

TCP_OpenPorts=""  	# Desktops don't have open ports... if not, enter them here (e.g. TCP_OpenPorts="1,45,7").
		  	# Max 15 ports.
UDP_OpenPorts=""  	# Same as above.

## -End- Important values



### Command arrays: Used to hold and build table/chain rules. The rules are built in specific order for maximum effeciency.

## System configuration
Sys_set=( '/sbin/depmod -a' '/sbin/modprobe ip_tables' '/sbin/modprobe iptable_filter' '/sbin/modprobe ipt_state' '/sbin/modprobe ip_conntrack' 'echo 1 > /proc/sys/net/ipv4/ip_dynaddr' 'echo 1 > /proc/sys/net/ipv4/conf/all/rp_filter' 'echo 0 > /proc/sys/net/ipv4/conf/all/proxy_arp' 'echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts' 'echo 1 > /proc/sys/net/ipv4/tcp_syncookies' 'echo 0 > /proc/sys/net/ipv4/conf/all/accept_source_route' 'echo 0 > /proc/sys/net/ipv4/conf/all/accept_redirects' 'echo 0 > /proc/sys/net/ipv4/conf/all/send_redirects' 'echo 1 > /proc/sys/net/ipv4/conf/all/secure_redirects' )
 
##   Network Rules  

#  TCP rule chain
TCP_chain=('iptables -N tcp_chain' 'iptables -A tcp_chain -p tcp --tcp-flags SYN,ACK SYN,ACK -m state --state NEW -m limit --limit 5/second -j REJECT --reject-with tcp-reset')

# UDP rule chain
UDP_chain=('iptables -N udp_chain' 'iptables -A udp_chain -p udp -s '$DHCP_server' --sport 67  --dport 68 -j ACCEPT')

# ICMP rule chain    (empty, all will be dropped)
ICMP_chain=('iptables -N icmp_chain')

# EXIT rule chains   (No match for this protocol so its garbage)
EXIT_chain=('iptables -A tcp_chain -j DROP' 'iptables -A udp_chain -j DROP' 'iptables -A icmp_chain -j DROP')
## -End- User Rules



##  Primary tables and their default policy.

Policy=( 'iptables -P INPUT DROP' 'iptables -P OUTPUT ACCEPT' 'iptables -P FORWARD DROP' )

# INPUT table
Input_table=( 'iptables -A INPUT -p ALL -m state --state ESTABLISHED,RELATED -j ACCEPT' 'iptables -A INPUT -p ALL -m state --state INVALID -j DROP' 'iptables -A INPUT -p TCP -j tcp_chain' 'iptables -A INPUT -p UDP -j udp_chain' 'iptables -A INPUT -p ICMP -j icmp_chain' )





#### Installer  
if [ `id -u` != 0 ]; then  zenity --error --text="You must have root privileges to use this script."
exit 1
fi

file=/etc/init.d/firewaller.sh
if [ -e $file ]; then
	rm $file
fi
# The version changes left old files and syslinks, delete them.
if [ -e /etc/init.d/A1Net.sh ]; then
	rm /etc/init.d/A1Net.sh
fi
if [ -e /etc/init.d/A1network.sh ]; then
	rm /etc/init.d/A1network.sh
fi
if [ -e /etc/init.d/a1Network.sh ]; then
	rm /etc/init.d/a1Network.sh
fi
if [ -e /etc/init.d/a1network.sh ]; then
	rm /etc/init.d/a1network.sh
fi
if [ -e /etc/rcS.d/S40A1network ]; then
	rm /etc/rcS.d/S40A1network
fi

echo
echo 'Welcome to Firewaller.sh v0.2b testing!'
echo
echo 'Answer the next questions carefully...'
echo
sleep 2
echo 'Please enter the address of your DHCP server(ask your ISP).'
echo '"e.g. 192.168.0.1"  If you do not know then just press Enter(not recommended)'
read -p'DHCP_S--> ' DHCP_S

if [ ! $DHCP_S ]; then DHCP_server=DHCP_S; fi

	
# Need ip validator :s


echo
echo 'Would you like local access?(yes/no) Default is no.'
read -p'Local access--> ' LocalAccess

if [ -n "$LocalAccess" ]; then
	LocalAccess='no'
elif [ $LocalAccess != 'yes' ]; then LocalAccess=no
fi

echo 'Would you like to open some UDP or TCP ports? (yes/no) Default is no.'
read -p'--> ' ans
if [ $ans == 'yes' ]; then
	echo
	echo 'Please enter the TCP port(s) value(s). (e.g. 10,56,2300) press enter for none.'
	read -p'--> ' TCP_OpenPorts
	echo
	echo 'Please enter the UDP port(s) value(s). (e.g. 10,56,2300) press enter for none.'
	read -p'--> ' UDP_OpenPorts
	echo
fi

echo "#! /bin/bash" 1>$file
chmod +x $file
echo "# This is the startup script for a iptable ruleset" 1>>$file
echo "#" 1>>$file
echo " " 1>>$file
echo "#" 1>>$file

### Service clauses
##   If restart then flush and clean.
echo "if [ "\"\$1\" = "\"restart\" ]" 1>>$file
echo "then" 1>>$file
echo "iptables -F" 1>>$file
echo "iptables -X" 1>>$file
echo "fi" 1>>$file

##   If 'start' then setup the system for packet filtering
echo "if [ "\"\$1\" = "\"start\" ]" 1>>$file
echo "then" 1>>$file
Elements=${#Sys_set[@]}
for (( i=0; i<$Elements;i++)); do 
	echo ${Sys_set[${i}]} 1>>$file
done
echo "fi" 1>>$file

##   If stop then just exit.
echo "if [ "\"\$1\" = "\"stop\" ]" 1>>$file
echo "then" 1>>$file
echo "exit" 1>>$file
echo "fi" 1>>$file


####   Set table policies
Elements=${#Policy[@]}
for (( i=0; i<$Elements;i++)); do 
	echo ${Policy[${i}]} 1>>$file
done

##  Build TCP chain
Elements=${#TCP_chain[@]}
for (( i=0; i<$Elements;i++)); do 
	echo ${TCP_chain[${i}]} 1>>$file
done

Elements=${#UDP_chain[@]}
for (( i=0; i<$Elements;i++)); do 
	echo ${UDP_chain[${i}]} 1>>$file
done

Elements=${#ICMP_chain[@]}
for (( i=0; i<$Elements;i++)); do 
	echo ${ICMP_chain[${i}]} 1>>$file
done


##  Build INPUT table
Elements=${#Input_table[@]}
for (( i=0; i<$Elements;i++)); do 
	echo ${Input_table[${i}]} 1>>$file
done

## If user wants open ports.
if [ $TCP_OpenPorts ]; then
	echo 'iptables -A tcp_chain -p tcp -m tcp -m multiport --dports '$TCP_OpenPorts' -j ACCEPT' 1>>$file
fi

if [ $UDP_OpenPorts ]; then
	echo 'iptables -A udp_chain -p udp -m udp -m multiport --dports '$UDP_OpenPorts' -j ACCEPT' 1>>$file
fi

# If local access is required then allow via netcard.
if [ $LocalAccess == "yes" ]
then 
	echo 'iptables -I INPUT 3 -i lo -s 127.0.0.1 -j ACCEPT' 1>>$file
	echo 'iptables -I FORWARD -i lo -s 127.0.0.1 -j ACCEPT'	1>>$file
fi

## Set default policy
# The last rule of each protcol chain is drop.
Elements=${#EXIT_chain[@]}
for (( i=0; i<$Elements;i++)); do 
	echo ${EXIT_chain[${i}]} 1>>$file
done

ln -sfv $file /etc/rcS.d/S40a1network
echo
echo 'Loading module and configuration...'
#/etc/init.d/firewaller.sh start

echo 'Complete, enjoy.'
sleep 2

# 
#
# Copyright (C) 2008  Jayotis Diggory;
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; version 3 of the License.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program or from the site that you downloaded it
# from; if not, write to the Free Software Foundation, Inc., 59 Temple
# Place, Suite 330, Boston, MA  02111-1307   USA
#
exit

```

---

### Post by Kernel_Krunch on 2008-02-27
Plz help test.

---

### Post by The Cog on 2008-02-28
The rules look very comprehensive to me. 

But I would suggest that you also do iptables -F and -X if the arg is "start" as well as if "restart".  You may consider either fully opening or fully closing the firewall (with DROP polocies) if you get a "stop" argument.

I lost interest in the script though.

---

### Post by k_grdn on 2008-02-28
Hi,

I would set the default policy of OUPUT to drop, you are also responsible for traffic going from your host, you don't want to become a relay.

Also I would drop traffic defined as reserved by IANA, also from broadcast, multicast, private addresses (spoofed packets) on the INPUT chain.

Also check for common forms of stealth scans via TCP State flags.

Regards,

k_grdn

---

### Post by brabo on 2008-02-29
k_grdn: what is the reasoning behind dropping traffic from IANA?

thx!

brabo.

---

### Post by k_grdn on 2008-02-29
Hi,

0.0.0.0/8 - class A network 0 addresses
169.254.0.0/16 - Link local network (DHCP addresses)
192.0.2.0/24 - TEST-NET

Above are some address blocks reserved by IANA, there are other blocks but they are not in use as of yet.  As the internet grows I suspect these addresses will be used and you may unintentionally block a legitimate host.

Simply this just reduces the number of possible spoofed addresses your host is subject too.

Regards,

k_grdn

---

### Post by damatta on 2008-02-29
Does that config automatically ignore every incoming TCP and UDP traffic to an ALLOWED port whilst it's daemon is not running? If not, how could this be done in UBUNTU? I know FreeBSD kernel support these Sysctl settings:
net.inet.tcp.blackhole and net.inet.udp.blackhole

---

### Post by Kernel_Krunch on 2008-03-03
> **The Cog said:**
> The rules look very comprehensive to me. 

But I would suggest that you also do iptables -F and -X if the arg is "start" as well as if "restart".  You may consider either fully opening or fully closing the firewall (with DROP policies) if you get a "stop" argument.

I lost interest in the script though.

Thank you for the suggestions :)
on start should be when system starts up so all tables empty and no user chains to delete.  I have now properly noted a way to make changes to the setup.

I'm not to sure about shutdown of the system and rcS.d, if it calls the scripts in the same order as start up (i.e. S0-->S40a) then the firewall should stay up until ifdown is called... in S40network.

---

### Post by Kernel_Krunch on 2008-03-03
> **k_grdn said:**
> Hi,

I would set the default policy of OUPUT to drop, you are also responsible for traffic going from your host, you don't want to become a relay.

Also I would drop traffic defined as reserved by IANA, also from broadcast, multicast, private addresses (spoofed packets) on the INPUT chain.

Also check for common forms of stealth scans via TCP State flags.

Regards,

k_grdn

Thank you very musk for your suggestions :)

The OUTPUT table controls all packets leaving my CPU, the only way I could become a relay is if someone compromised my local security and installed an agent.  In that case it will be a stealth thread and we would never see it. 

All traffic is dropped by default, I then only allow necessary traffic.
Any scan should show nothing at your address accept when a SYN/ACK is sent... and maybe your DHCP client port.(If you use the DHCP_server value, ask your ISP, then this will not be an issue).

I see what your saying about the scanning, I read all those docs too :)
All those rules for scans and logging, waste your CPU cycles.  A DROP rule is the same as 'exit', (i.e. "go back to processing my apps kernel... this is only garbage")

---

### Post by nloding on 2008-03-03
This isn't totally related to this thread, but I'm intrigued by the scripts that were posted.  I'm new to iptables -- is there a "comprehensive" tutorial on the net somewhere, or a recommended book?  I guess somewhere for me to start ...

---

### Post by Kernel_Krunch on 2008-03-03
> **damatta said:**
> Does that config automatically ignore every incoming TCP and UDP traffic to an ALLOWED port whilst it's daemon is not running? If not, how could this be done in UBUNTU? I know FreeBSD kernel support these Sysctl settings:
net.inet.tcp.blackhole and net.inet.udp.blackhole

First, this is not a daemon. the software for filtering packets is a kernel module, this script loads and configures the module, then exits.  You must re-run the script to alter the iptables(kernel module) setup.  If you open a port the rule to allow packets to the port is inserted into iptables, which always runs untill you either reboot or unload the module.

Thank you for your interest in my firewall :-D

---

### Post by Kernel_Krunch on 2008-03-03
Don't start with iptables, start with basic networking.

---

### Post by nloding on 2008-03-03
> **Kernel_Krunch said:**
> Don't start with iptables, start with basic networking.

I know basic networking, I'm looking to learn Linux software now.  Thanks though.

---

### Post by k_grdn on 2008-03-03
Hi,

My logic for comprehensive spoof scans is placing these rules high up the chain, on large scale firewalls this prevents the packet from traversing to the end of the chain before being dropped by the default policy, thus saving all the intergrate header checks, memory & wasted cpu cycles.

Regards,

k_grdn

---

### Post by Kernel_Krunch on 2008-03-05
> **k_grdn said:**
> 
My logic for comprehensive spoof scans is placing these rules high up the chain, on large scale firewalls... 

I wrote a desktop firewall :)  desktops don't need comprehensive scanning detection.  Maybe a honey pot... but not a regular PC.  I stick by my guns, flag checks are a waste of CPU.

---

