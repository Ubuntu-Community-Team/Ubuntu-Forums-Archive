---
title: "Firewall Ubuntu 5.10 IpTables Script"
date: 2006-06-19
forum: Server Platforms
---

### Post by EasyUwe on 2006-06-19
Hello @ All!

I've some problems with my ubuntu iptables firewall! now i tried a couple of times to get it fixed but I'am very new to linux and also I' am not used to program a firewall like it needs to be done in iptables...

here is my script:

```
#!/bin/bash

# Firewall Script fuer dual-homed Router
# Using Iptables
# written by Arne B.

# |  Modified  by  Uwe  Allgäuer      |

# Interface deklaration:
LAN_INTERFACE="eth0"
WAN_INTERFACE="ppp0"
# IP vom Router:
LAN_IP="10.95.101.1"
# LAN Addresses:
LAN_RANGE="10.95.101.0/24"
LAN_BCAST="10.95.101.255"
IPTABLES="/sbin/iptables"
echo "Network address Variables set to" $LAN_RANGE

#Script Start
start() {

echo "Firewall hochfahren...........[OK]"

#Regeln loeschen
$IPTABLES -F
$IPTABLES -t mangle -F
$IPTABLES -t nat    -F
$IPTABLES -X
$IPTABLES -t mangle -X
$IPTABLES -t nat    -X
echo "IpTabels rules deleted........[OK]"

# switch on ip forwarding
echo "Activate IP-Forwarding..."
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "Routing set Active............[OK]"

#Default Policys
$IPTABLES -P INPUT DROP
$IPTABLES -P FORWARD DROP
$IPTABLES -P OUTPUT DROP

#Set Loopback acitve
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A OUTPUT -o lo -j ACCEPT

#SSH aus dem LAN freigeben
$IPTABLES -A INPUT -p tcp -i $LAN_INTERFACE --dport 22 -s $LAN_RANGE -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A OUTPUT -p tcp -o $LAN_INTERFACE --sport 22 -d $LAN_RANGE -m state --state ESTABLISHED,RELATED -j ACCEPT

#Samba/Windows / tcp-137:139 / udp-137:138
$IPTABLES -A FORWARD -p tcp --dport 137:139 -j LOG --log-level 6 --log-prefix "FIREWALL:Forward:DROP"
$IPTABLES -A FORWARD -p tcp --dport 137:139 -j DROP
$IPTABLES -A FORWARD -p udp --dport 137:138 -j LOG --log-level 6 --log-prefix "FIREWALL:Forward:DROP"
$IPTABLES -A FORWARD -p udp --dport 137:138 -j DROP
#SQLSlammer / SQL-Wurm / udp-1434
$IPTABLES -A FORWARD -p udp --dport 1434 -j LOG --log-level 6 --log-prefix "FIREWALL:Forward:DROP"
$IPTABLES -A FORWARD -p udp --dport 1434 -j DROP
#wir routen keine Esel / tcp-4661:4662
$IPTABLES -A FORWARD -p tcp --dport 4661:4662 -j LOG --log-level 6 --log-prefix "FIREWALL:Forward:ESEL "
$IPTABLES -A FORWARD -p tcp --dport 4661:4662 -j DROP
# udp 3943
$IPTABLES -A FORWARD -p udp --dport 3943 -j LOG --log-level 6 --log-prefix "FIREWALL:Forward:3943 "
$IPTABLES -A FORWARD -p udp --dport 3943 -j DROP
#Forward pakets from LAN
$IPTABLES -A FORWARD -s $LAN_RANGE -i $LAN_INTERFACE -j ACCEPT
$IPTABLES -A FORWARD -d $LAN_RANGE -m state --state RELATED,ESTABLISHED -o eth0 -j ACCEPT
$IPTABLES -A POSTROUTING -t nat -s $LAN_RANGE -j MASQUERADE

#Samba/Windows Broadcasts do not Log
$IPTABLES -A INPUT -p udp --dport 137:138 -j DROP

#e-donkey pakets drop bevor Log
$IPTABLES -A INPUT -p tcp --dport 4661:4662 -i $WAN_INTERFACE -j DROP

# udp 3943
$IPTABLES -A INPUT -p udp --dport 3943 -i $WAN_INTERFACE -j DROP

#Log everything wich reaches this point before it
#is dropped by the default policy
$IPTABLES -A INPUT -j LOG --log-level 6 --log-prefix "FIREWALL:Input:DROP "
$IPTABLES -A FORWARD -j LOG --log-level 6 --log-prefix "FIREWALL:Forward:DROP "
$IPTABLES -A OUTPUT -j LOG --log-level 6 --log-prefix "FIREWALL:Output:DROP "

echo

echo
exit 0
}

stop() {

echo "Firewall shutdown.................[OK]"
#										[OK]

#Regeln loeschen
$IPTABLES -F
$IPTABLES -X
echo "Firewall rules deleted........[OK]"

#Default Policys auf Accept
$IPTABLES -P INPUT ACCEPT
$IPTABLES -P FORWARD ACCEPT
$IPTABLES -P OUTPUT ACCEPT
echo "Firewall rules Set to default![OK]"

# switch off ip forwarding
echo "DeActivate IP-Forwarding..."
echo 0 > /proc/sys/net/ipv4/ip_forward
echo "Routing disabled..............[OK]"

exit 0
}

restart() {
$0 stop
$0 start
}

help() {
#this print a short description of the script
cat <<HELP

This Script starts/stops an IPTable-Based Firewall

Usage:   firewall {start|stop|restart|help}
Example: ./firewall restart

Check the Firewall-Rules with
    iptables --list

HELP
exit 0
}

case "$1" in
    start)
            start
            ;;
    stop)
            stop
            ;;
    restart)
            restart
            ;;
    help)
            help
            ;;
    *)
            echo $"Usage: $0 {start|stop|restart|help}"
            exit 1
esac
exit 0

#end of file

```

Please can you hep me and explain to me why the DNS request issnt possible with this computer where the pp0 and the firewall script is running? otherwise internet surfing is possible when the script is running and the dns request needs not too be done...

THX
Uwe

---

### Post by LordHunter317 on 2006-06-19
Your script has a host of problems, which I'll deal with line-by-line.

> ```
echo "Firewall hochfahren...........[OK]"
```All the status messages of this ilk are not only be generated incorrectly (there are functions you can include to report status) they are unnecessary.  You should give a single success/fail notifcation, and that's it.  Remove these.

> ```
# switch on ip forwarding
echo "Activate IP-Forwarding..."
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "Routing set Active............[OK]"
```I would not do this here, as there are other mechanisms for doing this.  Overriding the normal way of doing things makes life harder for administrators.

> ```
$IPTABLES -P OUTPUT DROP
```/quote]Unless you have a good reason for doing egress filtering, do not.  On a home system it is senseless.  On a border router, it only make sense when you have strongly defined egress policies.  It's also why your DNS requests aren't working correctly.  That alone is probably enough reason for you to just leave the policy at ACCEPT.  Obviously, if you do this, the output rules become unnecessary.

Also, I despise defining /sbin/iptables as a variable and subtituting.  Just say /sbin/iptables.

[quote]$IPTABLES -A INPUT -p tcp -i $LAN_INTERFACE --dport 22 -s $LAN_RANGE -m state --state NEW,ESTABLISHED,RELATED -j ACCEPTDon't do states like this.  This is bad, because it doesn't let you write strict enough rules.  Make your **first** INPUT and FORWARD rule the following:```
iptables -A INPUT -m state --state ESTABLISHED, RELATED -j ACCEPT
```(changing INPUT to FORWARD as needed, obviously). This allows you to tighten the service rule to the following:```
iptables -A INPUT -m state --state NEW -i $LAN_INTERFACE -s $LAN_RANGE -p tcp --syn --dport ssh -j ACCEPT
```which will stop malicious traffic from reaching the service.

> ```
#Samba/Windows / tcp-137:139 / udp-137:138
$IPTABLES -A FORWARD -p tcp --dport 137:139 -j LOG --log-level 6 --log-prefix "FIREWALL:Forward:DROP"
$IPTABLES -A FORWARD -p tcp --dport 137:139 -j DROP
$IPTABLES -A FORWARD -p udp --dport 137:138 -j LOG --log-level 6 --log-prefix "FIREWALL:Forward:DROP"
$IPTABLES -A FORWARD -p udp --dport 137:138 -j DROP
#SQLSlammer / SQL-Wurm / udp-1434
$IPTABLES -A FORWARD -p udp --dport 1434 -j LOG --log-level 6 --log-prefix "FIREWALL:Forward:DROP"
$IPTABLES -A FORWARD -p udp --dport 1434 -j DROP
#wir routen keine Esel / tcp-4661:4662
$IPTABLES -A FORWARD -p tcp --dport 4661:4662 -j LOG --log-level 6 --log-prefix "FIREWALL:Forward:ESEL "
$IPTABLES -A FORWARD -p tcp --dport 4661:4662 -j DROP
# udp 3943
$IPTABLES -A FORWARD -p udp --dport 3943 -j LOG --log-level 6 --log-prefix "FIREWALL:Forward:3943 "
$IPTABLES -A FORWARD -p udp --dport 3943 -j DROP

```Don't log traffic unless you have a specific interest in monitoring it.  I doubt you have a specific interest in this traffic (it will be mostly noise) so you don't need to log it.

> ```
$IPTABLES -A FORWARD -s $LAN_RANGE -i $LAN_INTERFACE -j ACCEPT
```This should specify -m state --state NEW.

> ```
$IPTABLES -A FORWARD -d $LAN_RANGE -m state --state RELATED,ESTABLISHED -o eth0 -j ACCEPT
```If you do I say above, this rule becomes unnecessary.

> ```
$IPTABLES -A INPUT -j LOG --log-level 6 --log-prefix "FIREWALL:Input:DROP "
$IPTABLES -A FORWARD -j LOG --log-level 6 --log-prefix "FIREWALL:Forward:DROP "
$IPTABLES -A OUTPUT -j LOG --log-level 6 --log-prefix "FIREWALL:Output:DROP "
```I would not be logging traffic unless you have a good reason, again.  Certainly not default dropped traffic.  **In no case should this be logged at level 6.**

> ```
#Regeln loeschen
$IPTABLES -F
$IPTABLES -X
echo "Firewall rules deleted........[OK]"

#Default Policys auf Accept
$IPTABLES -P INPUT ACCEPT
$IPTABLES -P FORWARD ACCEPT
$IPTABLES -P OUTPUT ACCEPT
echo "Firewall rules Set to default![OK]"
```Again, kill the spurious messages, use the correct status functions, and you do this backwards.  Set policy first, then flush the ruleset.

> ```
# switch off ip forwarding
echo "DeActivate IP-Forwarding..."
echo 0 > /proc/sys/net/ipv4/ip_forward
echo "Routing disabled..............[OK]"
```**This is a massive no-no.**

---

