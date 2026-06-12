---
title: "IPTABLES Firewall rules help needed"
date: 2009-10-28
forum: Server Platforms
---

### Post by twistedtwig on 2009-10-28
Hi all,

I have recently changed the architecture of my network and am now having a couple of problems.  Previously I had a server in the garage where the network came into directly.  It had two Ethernet cards, external and internal.  There was also a windows 2003 server inside my network.  I used proxy pass reverse to include this website in my main site.

I now have an ESXi4.0 box with 3 VM's on it, the Linux box and the windows server.

The linux website is working just fine apart from the proxy pass reverse part.  The windows site can not be found.  I have a feeling this might be due to a port issue.  Previously the old firewall trusted all internal traffic (was given the firewall by a friend who knows more than I do about IPTABLES).  Now I only have one network port for the linux box I can not use this firewall.

I also put torrentflux on the server and can not get it to download anything.  It creates the .torrentflux folder for the torrent file, it created a "jon" folder (this is the username used to login), but it instantly fails downloading the torrent.  I am guessing this is also due to ports not being open.

Below is my firewall.  I guess there are two options, open the ports needed (not sure what it would be to get Apache and proxypassreverse working) or just say it should open all ports and trust all traffic.

This VM is not exposed to the internet directly.  I forward port 80 to it from the router but nothing else, so I assume it should not be attackable if I open it right up.

Could anyone help, advise or offer some suggestions on which route to take and give some help with the iptables.

Thanks


```
#!/bin/sh
# /etc/init.d/firewall
# from http://wiki.linuxquestions.org/wiki/A_basic_firewall_configuration_suitable_for_a_workstation

set -e

iptables="/sbin/iptables"
modprobe="/sbin/modprobe"

load () {

 echo "Loading kernel modules..."
 $modprobe ip_tables
 $modprobe ip_conntrack
 $modprobe iptable_filter
 $modprobe ipt_state
 $modprobe iptable_nat
 echo "Kernel modules loaded."

 echo "Loading rules..."
 $iptables -P FORWARD DROP
 $iptables -P INPUT DROP

##### PORTS #####
# comment out the ones you don't need

### ftp
$iptables -A INPUT -p tcp -m tcp --destination-port 21 -j ACCEPT

### ssh
$iptables -A INPUT -p tcp -m tcp --destination-port 22 -j ACCEPT

### http
$iptables -A INPUT -p tcp -m tcp --destination-port 80 -j ACCEPT

### NetBIOS (Windows Networking, Samba)
$iptables -A INPUT -i eth0 --protocol tcp --dport 137 -j ACCEPT
$iptables -A INPUT -i eth0 --protocol tcp --dport 139 -j ACCEPT

### for Duelle: World of Warcraft
#$iptables -A INPUT -p tcp -m tcp --destination-port 6112:6119 -j ACCEPT

### for Duelle:  Bittorrent
#$iptables -A INPUT -p tcp -m tcp --destination-port 49200 -j ACCEPT


##### BLOCK OUT INTRUSION #####
$iptables -A INPUT -i eth0 -m state --state NEW,INVALID -j DROP
$iptables -A FORWARD -i eth0 -m state --state NEW,INVALID -j DROP


###### DEFAULTS #####
 $iptables -A INPUT -p ALL -m state --state ESTABLISHED,RELATED -j ACCEPT
 $iptables -A INPUT -s 127.0.0.1 -j ACCEPT
 echo "Rules loaded."
}

flush () {

 echo "Flushing rules..." $iptables -P FORWARD ACCEPT
 $iptables -F INPUT
 $iptables -P INPUT ACCEPT
 echo "Rules flushed."

}

case "$1" in

 start|restart)
   flush
   load
   ;;
 stop)
   flush
   ;;
 *)
   echo "usage: start|stop|restart."
   ;;

esac
exit 0
```

---

### Post by twistedtwig on 2009-10-29
bump... really struggling to figure this one out.  Hope someone might be able to help.

Thx

---

