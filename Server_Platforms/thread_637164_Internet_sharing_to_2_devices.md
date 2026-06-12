---
title: "Internet sharing to 2 devices"
date: 2007-12-10
forum: Server Platforms
---

### Post by Centaur5 on 2007-12-10
I would like to share internet from eth0 (ppp0) to eth1 and eth2.  I currently have it working fine with eth1 but I can't get eth2 going.  The reason for this is to have eth1 going to a hardwire switch and eth2 to a wireless router using Chillispot.  I was originally using Firestarter but since it doesn't support sharing to 2 devices I read about ipkungfu on a forum which allows you to do space separated ethernet devices in the configuration but it still doesn't work.  I'm also running DHCP on both network cards but only eth1 is truly important for that.  I don't know if there is an application, script, or some other easy howto that I haven't run across to do this but I would appreciate if somebody could point me the right way.  This is on Gutsy in case that's of any importance.

---

### Post by HermanAB on 2007-12-10
You can bridge the two inside ports eth1 and eth2 together so that they act as one device called br0 then do NAT between eth0 and br0.  Read up on 'bridging' with 'ebtables'.

Cheers,

H.

---

### Post by Centaur5 on 2007-12-10
Thanks HermanAB, I was considering doing a bridge but thought that would maybe cause a conflict with the DHCP server giving the same IP addresses over both NICs.  Correct me if I'm wrong but doesn't a bridge basically ignore the devices as separate eth1 and eth2 and creates a symbolic br0 which then is referred to as just that one connection?  I'll do that if it won't cause a problem with what I'm attempting to setup.  Thanks again for the fast response.

---

### Post by HermanAB on 2007-12-11
It will work for a small home or lab LAN.  Bridging basically creates an (expensive) Ethernet Hub out of multiple adaptors.

The DHCP address assignment messages flow point to point, so if a device receives a packet, it knows whether it is relevant and if not, drops it.  It is only the initial cry for help that is a broadcast message.

Cheers,

H.

---

### Post by sciurus on 2007-12-13
Something like 

```

#!/bin/sh
EXTIF=ppp0
WIRED=eth1
WIRELESS=eth2
IPTABLES=/sbin/iptables
# Enable IP Forwarding
echo "1" > /proc/sys/net/ipv4/ip_forward
# Clearing any existing rules and setting default policy
$IPTABLES -P INPUT ACCEPT
$IPTABLES -F INPUT 
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT 
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD 
$IPTABLES -t nat -F
# Allow all connections OUT and only existing and related ones IN
$IPTABLES -A FORWARD -i $EXTIF -o $WIRED -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $EXTIF -o $WIRELESS -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $WIRED -o $EXTIF -j ACCEPT
$IPTABLES -A FORWARD -i $WIRELESS -o $EXTIF -j ACCEPT
$IPTABLES -A FORWARD -j LOG
# Enabling SNAT (MASQUERADE) functionality on $EXTIF
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

```

if you have the interfaces and DNS configured properly.

---

### Post by mckryptyk on 2007-12-13
Try this: 

I wrote it with the xbox in mind, but it will share from any machine to any other machine and it may be of use to you if you want a simple way to share internet connections.

[http://ubuntuforums.org/showthread.php?t=103881](http://ubuntuforums.org/showthread.php?t=103881)

Hope its of some use to you,

Bye! :)

---

### Post by Centaur5 on 2007-12-16
Thanks everybody for the help.  I finally got the time to come post what my friend helped me to to get this to work.  First off I used the following script that my friend found:

#!/bin/bash
IPTABLES='/sbin/iptables'

# Set interface values
EXTIF='ppp0'
INTIF1='eth1'
INTIF2='eth2'

# enable ip forwarding in the kernel
/bin/echo 1 > /proc/sys/net/ipv4/ip_forward

# flush rules and delete chains
$IPTABLES -F
$IPTABLES -X

# enable masquerading to allow LAN internet access
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

# allow loopback
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A OUTPUT -o lo -j ACCEPT

# forward LAN traffic from $INTIF1 to Internet interface $EXTIF
$IPTABLES -A FORWARD -i $INTIF1 -o $EXTIF -m state --state NEW,ESTABLISHED -j ACCEPT

# forward LAN traffic from $INTIF2 to Internet interface $EXTIF
$IPTABLES -A FORWARD -i $INTIF2 -o $EXTIF -m state --state NEW,ESTABLISHED -j ACCEPT

# block out all other Internet access on $EXTIF
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW,INVALID -j DROP
$IPTABLES -A FORWARD -i $EXTIF -m state --state NEW,INVALID -j DROP


However, after running the script everything was working perfect except client computers couldn't go to any microsoft site (ie: windowsupdate.microsoft.com, msn.com, microsoft.com, or hotmail.com) and also couldn't access apple.com.  Therefore I had to add the following line to the script above which I figured I would post in case this ever happens to somebody else.

$IPTABLES -I FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu

---

### Post by HermanAB on 2007-12-16
Hmm, that hack is only necessary if there is an intervening idiot router that is dropping PMTU ICMP packets.  Hopefully that is not one of your own pieces of kit, but it may very well be: [http://support.microsoft.com/kb/925280](http://support.microsoft.com/kb/925280)

Cheers,

Herman

---

### Post by Centaur5 on 2007-12-17
The cat5 cable coming from the PoE box that our ISP left with us goes directly into eth0 on the Ubuntu server I just configured.  There is no other equipment on my end that should be dropping those packets.

---

### Post by HermanAB on 2007-12-17
So, you have an idiot ISP...

---

### Post by Centaur5 on 2007-12-18
They're the best ISP in town though.  I'll be taking a class from one of their system administrators next semester so maybe I'll ask him what is wrong.  :)

---

