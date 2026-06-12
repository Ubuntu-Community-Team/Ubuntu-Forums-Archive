---
title: "How to set up Firewall on Ubuntu?"
date: 2014-11-17
forum: Security
---

### Post by flaymond on 2014-11-17
I see that iptables is pre-installed firewall on Ubuntu. But, i also seen that the settings are default (all accepted).

So, how can i protect my pc using this firewall.

and how can I set it up?

Thanks

---

### Post by kevdog on 2014-11-17
This is a very difficult topic to actually reply to since their are many many methods to do this. 

It's possible to interact with the iptables executable directly or through a front-end such as ufw or the gui for the ufw.  The frontends are much easier to use, however I find them difficult if you need to set up some specifics and fine tine things such as on a server.  

I personally interact with iptables directly through a script file.  I'd be happy to share the script if you want.  You can also interact directly with iptables on the command line, however the advantage of a script file is that when you mess up on your rule set -- which you will invariably do when setting up the firewall, you use the script to clear all the rules and then just reissue the ruleset all over again within the script.

---

### Post by ajgreeny on 2014-11-17
If you have a standalone desktop you may not even need a firewall; it depends how you use your computer.  I do not have a separate firewall on mine apart from the router hardware.

See:-
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
[https://help.ubuntu.com/community/Firewall](https://help.ubuntu.com/community/Firewall)

---

### Post by flaymond on 2014-11-17
I installed the gufw, and run it fine and dandy. Very simple and easy. But I don't know what the firewall allow and deny....so...can you share the script? I don't like people inject virus or something malicious to my computer....thanks

---

### Post by sammiev on 2014-11-17
I have all my ports set for Deny but allow a few out.

---

### Post by flaymond on 2014-11-18
thanks for replies guys. Also, thanks for the script..I appreciate that ):P

---

### Post by sammiev on 2014-11-18
1194 is for my vpn service. You have no need for that at this time.

---

### Post by kevdog on 2014-11-19
I'm posting my firewall script.  Please read:

The main reason I like interacting through a firewall script is that its very intuitive in the script what ports are open or closed.  If commented properly the firewall script is very easy to read and make adjustments.

Within the script, many of the port numbers may need to be changed.
Please note that my internal LAN address is 10.0.1.x -- which is different than traditional.

The default policy of this firewall is drop.
All input ports are blocked to the outside world accept ntp - port 123.
Open services with open incoming ports as specified in the script are all accessible to computers on the LAN address

Output chain default policy is drop.  
Only specified ports within the output chain are open.  

I utilize a fwknop daemon to open the server SSH port to the outside world dynamically.  The fwknop daemon is started or stopped by a upstart service definition file (this sounds really hard but its not).  If you need instructions how to start this daemon at boot, please respond in the thread accordingly

If choosing to use this file -- save the script as root.  I place it within the /usr/local/sbin directory, however I suppose it could go elsewhere.  I save it as root:root with 755 permissions at /usr/local/sbin/iptable

There are a few ways to actually initiate the script at boot.  (For clarificationthe script is a bash script file named in this example iptable.  Its located within /usr/local/sbin with 755 permissions.
Option #1 - (Make use of the iptables-persistent package) (if not installed, install the iptables-persistent package through synaptic or using apt-get (sudo apt-get install iptables-persistent))
   a. Use the script to flush the existing filewall -- sudo iptable stop
   b. Use the script to load your existing rules -- sudo iptable start
   c. Save the iptable ruleset to a format the iptables-persistent package can reload on boot  (please note my script above only contains IPv4 rules and not IPv6 rules -- this could be changed if necessary)):
          sudo iptables-save > /etc/iptables/rules.v4
          sudo iptables-save > /etc/iptables/rules.v6
   d. Once the rules are saved within /etc/iptables/rules.v[4,6] they will be reloaded at boot by the iptables-persistent service (which automatically starts on boot)
   e. Everytime you modify the script, you will have to reload the firewall rules:
          sudo iptable restart
      And when satisfied with the script and loaded firewall ruleset resave the ruleset as inidicated in Step c above.  An automated way to perform Step C at shutdown is described in Option #3


Option #2 - (Create your own custom Upstart script which would call the iptable script at boot and load the firewall rulesut -- I employ this method since I have in conjuction with my iptables and the fwknop daemon)
  
   Here is an example of the script -- The script is saved within /etc/init/ directory.  Its owned by root,root with 644 permissions.  For example it could be called /etc/init/iptables-start.conf.  Please note that when adding any upstart script to this directory, you always want to run a double check for any syntax errors -- you do this by running at command line: init-checkconf /etc/init/iptables-start.conf
```

#iptables startup script -- Location /etc/init/iptables-start.conf

description "automatic start of iptables at boot"
  
start on (starting network-interface
             or starting network-manager
             or starting networking)

stop on shutdown

console output

respawn
respawn limit 10 5

pre-start script
    test -x /usr/local/sbin/iptable || { stop; exit 0; }
end script

post-stop script
    test -x /usr/local/sbin/iptable || { stop; exit 0; }
    /usr/local/sbin/iptable stop
end script

exec /usr/local/sbin/iptable start

```

Option #3 - Combine the two methods mentioned above.  A combination of the methods would automate the saving of any altered iptable ruleset at shutdown to the /etc/iptables/rules.v[4,6].  It would combine use of an upstart script that would save the current ruleset at shutdown to the respective rules version 4,6 files.   (Please note that I haven't tried this method but would appreciate feedback if you try this method).  I believe the upstart script would be similar to the following:

```

#iptables save configuration script -- found at /etc/init/iptables-save.conf

description "automatic saving of iptable ruleset at shutdown"
  
start on startup

stop on shutdown

console output

respawn
respawn limit 10 5


pre-stop script
          iptables-save > /etc/iptables/rules.v4
          iptables-save > /etc/iptables/rules.v6
end script


```

Ok here is the actual firewall script:

```

#!/bin/bash

### Gloval Variables
IPTABLES=/sbin/iptables
IP6TABLES=/sbin/ip6tables
MODULES=yes
MODPROBE=/sbin/modprobe
## SERVER_INTERFACE=wlan0
SERVER_INTERFACE=`ip addr show | awk '$1 == "inet" && $3 == "brd" { print $7 }'`
SERVER_IP=`ifconfig $SERVER_INTERFACE | grep inet | awk '{ print $2 }'| cut -d : -f2`
LOGLIMIT="2/s"
LOGLIMITBURST=10

#### Network Device Settings 
##Please alter settings for your own network
INT_NET=10.0.1.0/24
SSH_PORT=2223

#### /proc sysctl settings

IP_FORWARD=yes		#to enable ipforward, VERY important

ICMPALLIGNORE=no	#yes to block ALL the pings from everywhere
ICMPBROADCAST=yes	#yes to don't respond to broadcast pings (smurf)
ICMPERRORMESG=yes	#yes to protect against bogus error messages

LOGMARTIANS=yes		#yes to log packets with impossible addresses
IP_SPOOFING=yes		#yes to disable spoofing attacks on ALL interfaces

REDUCEDOS=yes		#reduces the timeouts and the posibility of a DOS

SYNCOOKIES=yes		#yes to enable tcp syn cookies protection
TIMESTAMPS=yes		#yes to enable tcp timestamps protection

SOURCEROUTED=yes	#yes to ignore source routed packets
SENDREDIRECTS=yes	#yes to ignore redirected packets


### load connection-tracking modules

if [ $MODULES == "yes" ]; then
	$MODPROBE ip_conntrack
	$MODPROBE iptable_nat
	$MODPROBE ip_conntrack_ftp
	$MODPROBE ip_nat_ftp
fi

#Following function only needed if employing a port knocker - Please delete or comment out this function if not required.
function restart_fwknopd_if_stopped() {

echo "[+] Checking on FWKNOPD status..."
ps cax | grep fwknopd > /dev/null
if [ $? -eq 0 ]; then
   echo "         .....FWKNOPD is Already Started..."
else
   echo "         .....Restarting FWKNOPD Service..."
   service fwknopd restart
fi


}


function clean() {

echo "[+] Flushing existing iptables rules..."
$IPTABLES -F
$IPTABLES -F -t mangle
$IPTABLES -F -t nat
$IPTABLES -X
$IPTABLES -X -t mangle
$IPTABLES -X -t nat

$IPTABLES -P INPUT ACCEPT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -P FORWARD ACCEPT
$IP6TABLES -P INPUT ACCEPT
$IP6TABLES -P OUTPUT ACCEPT
$IP6TABLES -P FORWARD ACCEPT

}


### flush existing rules and set chain policy setting to DROP

function Default_Policies() {

#Default Policies
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT DROP
$IPTABLES -P FORWARD DROP

### this policy does not handle IPv6 traffic except to drop it.
$IP6TABLES -P INPUT DROP
$IP6TABLES -P OUTPUT DROP
$IP6TABLES -P FORWARD DROP

}

function proc() {

if [ $IP_FORWARD == "yes" ] ; then
	if [ -f /proc/sys/net/ipv4/ip_forward ] ; then
		echo 1 > /proc/sys/net/ipv4/ip_forward
		echo "         ip_foward activated"
	fi
fi


if [ $ICMPALLIGNORE == "yes" ] ; then
	if [ -f /proc/sys/net/ipv4/icmp_echo_ignore_all ] ; then
		echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_all
		echo "         .....Blocking all pings from everywhere"
	fi
fi


if [ $ICMPBROADCAST == "yes" ] ; then
	if [ -f /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts ]; then
		echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
		echo "         .....Blocking all broadcast pings"
	fi
fi


if [ $ICMPERRORMESG == "yes" ] ; then
	if [ -f /proc/sys/net/ipv4/icmp_ignore_bogus_error_responses ]; then
		echo "1" > /proc/sys/net/ipv4/icmp_ignore_bogus_error_responses
		echo "         .....Enable error message protection"
	fi
fi


if [ $LOGMARTIANS == "yes" ] ; then
	if [ -f /proc/sys/net/ipv4/conf/all/log_martinas ] ; then
		echo "1" > /proc/sys/net/ipv4/conf/all/log_martians
		echo "         .....Logging packets with impossible addresses"
	fi
fi


if [ $IP_SPOOFING == "yes" ] ; then
	if [ -f /proc/sys/net/ipv4/conf/all/rp_filter ] ; then
		echo "2" > /proc/sys/net/ipv4/conf/all/rp_filter
		echo "         .....Blocking IP spoofing attacks"
	fi
fi


if [ $REDUCEDOS == "yes" ] ; then
	echo "30" > /proc/sys/net/ipv4/tcp_fin_timeout
	echo "2400" > /proc/sys/net/ipv4/tcp_keepalive_time
	echo "0" > /proc/sys/net/ipv4/tcp_window_scaling
	echo "0" > /proc/sys/net/ipv4/tcp_sack
	echo "         .....Denial of Service Reduction Measures"
fi


if [ $SYNCOOKIES == "yes" ] ; then
	if [ -e /proc/sys/net/ipv4/tcp_syncookies ] ; then
		echo "1" > /proc/sys/net/ipv4/tcp_syncookies
		echo "         .....TCP syn cookies protection enabled"
	fi
fi


if [ $TIMESTAMPS == "yes" ] ; then
	if [ -e /proc/sys/net/ipv4/tcp_timestamps ] ; then
		echo "0" > /proc/sys/net/ipv4/tcp_timestamps
		echo "         .....TCP timestamps protection enabled"
	fi
fi


if [ $SOURCEROUTED == "yes" ] ; then
	if [ -e /proc/sys/net/ipv4/conf/all/accept_source_route ] ; then
		echo "0" > /proc/sys/net/ipv4/conf/all/accept_source_route
		echo "         .....Ignore source routed packets"
	fi
fi


if [ $SENDREDIRECTS == "yes" ] ; then
	if [ -e /proc/sys/net/ipv4/conf/all/send_redirects ]; then
	        echo "0" > /proc/sys/net/ipv4/conf/all/send_redirects
		echo "         .....Ignore redirected packets"
	fi
fi

}

function firewall() {

###### INPUT chain ######
#
echo "[+] Setting up INPUT chain..."

### state tracking rules
echo "         .....State Tracking Rules"
$IPTABLES -A INPUT -m state --state INVALID -j LOG --log-prefix "DROP IN INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

## Flood Protection
#$IPTABLES -A INPUT -p tcp --syn -m limit --limit 1/s -j ACCEPT
#$IPTABLES -A INPUT -p tcp --tcp-flags SYN,ACK,FIN,RST RST -m limit --limit 1/s -j ACCEPT

### anti-spoofing rules
#$IPTABLES -A INPUT ! -s $INT_NET -j LOG --log-prefix "SPOOFED PKT "
#$IPTABLES -A INPUT ! -s $INT_NET -j DROP

### ACCEPT rules
echo "         .....Common Ports"
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j DROP

### SSH
echo "         .....SSH"
#$IPTABLES -A INPUT -p tcp ! -s $INT_NET --dport $SSH_PORT -m state --state NEW -m recent --set
#$IPTABLES -A INPUT -p tcp ! -s $INT_NET --dport $SSH_PORT -m state --state NEW -m recent --update --seconds 60 --hitcount 4 -j ACCEPT
$IPTABLES -A INPUT -p tcp -s $INT_NET --dport $SSH_PORT --syn -m state --state NEW -j ACCEPT

# Xwin
#$IPTABLES -A INPUT -p tcp --syn --dport 6000:6063 -j ACCEPT
#$IPTABLES -A INPUT -p udp --dport 177 -m state --state NEW -j ACCEPT

# NTP
echo "         .....NTP"
$IPTABLES -A INPUT -p udp --dport 123 -j ACCEPT

# CIFS/SMB ACCEPT Rules
echo "         .....CIFS/SMB"
$IPTABLES -A INPUT -p tcp -s $INT_NET --sport 137:139 --dport 137:139 -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -p udp -s $INT_NET --sport 137:139 --dport 137:139 -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -p tcp -s $INT_NET --sport 137:139 --dport 1024:65535 -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -p udp -s $INT_NET --sport 137:139 --dport 1024:65535 -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -p tcp -s $INT_NET --dport 137:139 -m state --state NEW -j ACCEPT

# MULTICAST
echo "         .....Multicast"
$IPTABLES -A INPUT -p udp -s $INT_NET --dport 5353 -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -p tcp -s $INT_NET --dport 5353 -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -s 0/0 -d 224.0.0.0/24 -m state --state NEW -j ACCEPT

### default INPUT LOG rule
echo "         .....Default INPUT LOG Rule"
$IPTABLES -A INPUT ! -i lo -j LOG -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST --log-prefix "DROP IN- " --log-ip-options --log-tcp-options

### make sure that loopback traffic is accepted
$IPTABLES -A INPUT -i lo -j ACCEPT

###### OUTPUT chain ######
#
echo "[+] Setting up OUTPUT chain..."

### state tracking rules
echo "         .....State Tracking Rules"
$IPTABLES -A OUTPUT -m state --state INVALID -j LOG --log-prefix "DROP OUT INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A OUTPUT -m state --state INVALID -j DROP
$IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### ACCEPT rules for allowing connections out
echo "         .....Common Ports"

#FTP - Port 21
$IPTABLES -A OUTPUT -p tcp --dport 21 --syn -m state --state NEW -j ACCEPT

#Global Outside SSH - Port 22
$IPTABLES -A OUTPUT -p tcp --dport 22 --syn -m state --state NEW -j ACCEPT

#Local SSH Server on LAN - Port 2222
$IPTABLES -A OUTPUT -p tcp -d $INT_NET --dport 2222 --syn -m state --state NEW -j ACCEPT

#SMTP - Port 25
$IPTABLES -A OUTPUT -p tcp --dport 25 --syn -m state --state NEW -j ACCEPT

#WHOIS - Port 43
$IPTABLES -A OUTPUT -p tcp --dport 43 --syn -m state --state NEW -j ACCEPT

#HTTP - Port 80
$IPTABLES -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT

#HTTPS - Port 443
$IPTABLES -A OUTPUT -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT

#RWhois Protocol - Port 4321
$IPTABLES -A OUTPUT -p tcp --dport 4321 --syn -m state --state NEW -j ACCEPT

#DNS Lookup - Port 53
$IPTABLES -A OUTPUT -p tcp --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT

#Ping Requests
$IPTABLES -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT

#SMTP - Port 587
$IPTABLES -A OUTPUT -p tcp --dport 587 -m state --state NEW -j ACCEPT

#NTP (Network Time) - Port 123
$IPTABLES -A OUTPUT -p udp --sport 123 -j ACCEPT

## NoIP
echo "         .....NoIP"
$IPTABLES -A OUTPUT -p tcp --dport 8245 -m state --state NEW -j ACCEPT

# Multicast DNS
echo "         .....Multicast"
$IPTABLES -A OUTPUT -p tcp --dport 5353 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp --dport 5353 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -s $SERVER_IP -d 224.0.0.0/24 -m state --state NEW -j ACCEPT

# CIFS
echo "         .....CIFS"
$IPTABLES -A OUTPUT -p tcp --sport 137:139 -d $INT_NET --dport 137:139 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp --sport 137:139 -d $INT_NET --dport 137:139 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --sport 1024:65535 -d $INT_NET --dport 137:139 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp --sport 1024:65535 -d $INT_NET --dport 137:139 -m state --state NEW -j ACCEPT

# SMB
echo "         .....SMB"
$IPTABLES -A OUTPUT -p tcp -s $INT_NET -d $INT_NET --dport 445 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp -s $INT_NET -d $INT_NET --dport 445 -m state --state NEW -j ACCEPT 

## GMail SMTP
echo "         .....Gmail SMTP"
$IPTABLES -A OUTPUT -p tcp --dport 993 -m state --state NEW -j ACCEPT

## Git
echo "         .....Git"
$IPTABLES -A OUTPUT -p tcp --dport 9418 -m state --state NEW -j ACCEPT

### default OUTPUT LOG rule
echo "         .....Default OUTPUT LOG Rule"
$IPTABLES -A OUTPUT ! -o lo -j LOG -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST --log-prefix "DROP OUT- " --log-ip-options --log-tcp-options

### make sure that loopback traffic is accepted
$IPTABLES -A OUTPUT -o lo -j ACCEPT

###### FORWARD chain ######
#
echo "[+] Setting up FORWARD chain..."

### state tracking rules
echo "         .....State Tracking Rules"
$IPTABLES -A FORWARD -m state --state INVALID -j LOG --log-prefix "DROP INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A FORWARD -m state --state INVALID -j DROP
$IPTABLES -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

### anti-spoofing rules
#$IPTABLES -A FORWARD ! -s $INT_NET -j LOG --log-prefix "SPOOFED PKT "
#$IPTABLES -A FORWARD ! -s $INT_NET -j DROP

### ACCEPT rules
echo "         .....Common Ports"
#$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 21 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 22 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 25 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 43 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 4321 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp --dport 53 -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p udp --dport 53 -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p icmp --icmp-type echo-request -j ACCEPT

# CIFS
echo "         .....CIFS"
$IPTABLES -A FORWARD -p udp -s $INT_NET --sport 137:139 -d $INT_NET --dport 137:139 -m state --state NEW -j ACCEPT

# MULTICAST
echo "         .....Multicast"
$IPTABLES -A FORWARD -p udp -s $INT_NET --sport 5353 -d 224.0.0.0/24 --dport 5353 -m state --state NEW -j ACCEPT

# Dynamic Device Discovery
echo "         .....Dynamic Device Discovery"
$IPTABLES -A FORWARD -p udp -s $INT_NET --sport 9131 --dport 9131 -m state --state NEW -j ACCEPT

### default LOG rule
echo "         .....Default FORWARD LOG Rule"
$IPTABLES -A FORWARD ! -i lo -j LOG -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST --log-prefix "DROP F- " --log-ip-options --log-tcp-options

###### NAT rules ######
#
echo "[+] Setting up NAT rules..."
#$IPTABLES -t nat -A PREROUTING -p tcp --dport 80 -i eth0 -j DNAT --to 192.168.10.3:80
#$IPTABLES -t nat -A PREROUTING -p tcp --dport 443 -i eth0 -j DNAT --to 192.168.10.3:443
#$IPTABLES -t nat -A PREROUTING -p udp --dport 53 -i eth0 -j DNAT --to 192.168.10.4:53
#$IPTABLES -t nat -A POSTROUTING -s $INT_NET -o eth0 -j MASQUERADE

###### forwarding ######
#

}

case "$1" in
   stop)
      echo "Shutting down firewall..."
      clean
      echo "...done"
      ;;
   status)
      echo $"Table: filter"
      iptables --list
      echo $"Table: nat"
      iptables -t nat --list
      echo $"Table: mangle"
      iptables -t mangle --list
      ;;
   restart|reload)
      $0 stop
      $0 start
      ;;
   start)
    echo "Starting Firewall..."
      clean 
      Default_Policies
      proc
      firewall

      #Following Function needed if Employing a FWKNOP Port Knocker Daemon -- Please delete or comment out following line if not employing a port knocker
      restart_fwknopd_if_stopped
      ;;
    *)
      echo "Usage iptable { start | stop | restart | status }"
      exit 1
      ;;
esac


exit
### EOF ### 

```

---

### Post by BBQdave on 2014-11-20
> **InterProg said:**
> I see that iptables is pre-installed firewall on Ubuntu. But, i also seen that the settings are default (all accepted).

So, how can i protect my pc using this firewall.

Ubuntu's default setting is to not accept incoming traffic to all ports. A port opens when you send.

You can install GUFW, a nice gui for the default firewall. Adjustments to your firewall would be opening ports, such as for a service (server) you might be running on your machine.

A default install of Ubuntu already has all ports closed to incoming traffic :)

---

