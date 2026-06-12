---
title: "IPTABLES - combine router Firewall/NAT with VPN"
date: 2012-09-15
forum: Security
---

### Post by SeaKing on 2012-09-15
Hey,

I'm having a little trouble with my IP tables Firewal/NAT/VPN Script

first of all I'm running my router behind a DSL Modem, which provides a static IP.

If I try to connect via VPN from outside I get a connection timeout reset.
The script:

```

# External (Internet-facing) interface
EXTIF="eth0"

# External IP address (automatically detected)
EXTIP=$(/sbin/ip addr show dev "$EXTIF" | perl -lne 'if(/inet (\S+)/){print$1;last}');
 
# Internal interface
INTIF="br0"

# Internal IP address (in CIDR notation)
INTIP="192.168.1.1/32"

# Internal network address (in CIDR notation)
INTNET="192.168.1.0/24"

# The address of anything/everything (in CIDR notation)
UNIVERSE="0.0.0.0/0"


echo "External: [Interface=$EXTIF] [IP=$EXTIP]"
echo "Internal: [Interface=$INTIF] [IP=$INTIP] [Network:$INTNET]"

echo
echo -n "Loading rules..."

# Enabling IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward


/sbin/iptables-restore <<-EOF;

*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]

###################################################
# INPUT: Incoming traffic from various interfaces #
###################################################
#vpn
-A INPUT -i tun+ -j ACCEPT

# Loopback interface is valid
-A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT


# Local interface, local machines, going anywhere is valid
-A INPUT -i $INTIF -s $INTNET -d $UNIVERSE -j ACCEPT


# Remote interface, claiming to be local machines, IP spoofing, get lost
-A INPUT -i $EXTIF -s $INTNET -d $UNIVERSE -j REJECT


# External interface, from any source, for ICMP traffic is valid
-A INPUT -i $EXTIF -p ICMP -s $UNIVERSE -d $EXTIP -j ACCEPT


# Allow any related traffic coming back to the MASQ server in.
-A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m conntrack --ctstate ESTABLISHED,RELATED $


# Internal interface, DHCP traffic accepted
-A INPUT -i $INTIF -p tcp --sport 68 --dport 67 -j ACCEPT
-A INPUT -i $INTIF -p udp --sport 68 --dport 67 -j ACCEPT

# Internal interface, DNS traffic accepted
-A INPUT -i $INTIF -p tcp --dport 53 -j ACCEPT
-A INPUT -i $INTIF -p udp --dport 53 -j ACCEPT

# External interface, SSH traffic allowed
-A INPUT -i $EXTIF -m conntrack --ctstate NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE$

# Catch-all rule, reject anything else
-A INPUT -s $UNIVERSE -d $UNIVERSE -j REJECT

# Accept port 1234 to be forwarded (this rule needs to correspond with PREROUTING rul$
-A FORWARD -i $EXTIF -o $INTIF -p tcp --dport 5555 -m conntrack --ctstate NEW,ESTABLI$


####################################################
# OUTPUT: Outgoing traffic from various interfaces #
####################################################

# Workaround bug in netfilter
-A OUTPUT -m conntrack -p icmp --ctstate INVALID -j DROP

# Loopback interface is valid.
-A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT


# Local interfaces, any source going to local net is valid
-A OUTPUT -o $INTIF -s $EXTIP -d $INTNET -j ACCEPT


# local interface, MASQ server source going to the local net is valid
-A OUTPUT -o $INTIF -s $INTIP -d $INTNET -j ACCEPT


# outgoing to local net on remote interface, stuffed routing, deny
-A OUTPUT -o $EXTIF -s $UNIVERSE -d $INTNET -j REJECT


# anything else outgoing on remote interface is valid
-A OUTPUT -o $EXTIF -s $EXTIP -d $UNIVERSE -j ACCEPT


# Internal interface, DHCP traffic accepted
-A OUTPUT -o $INTIF -p tcp -s $INTIP --sport 67 -d 255.255.255.255 --dport 68 -j ACCE$
-A OUTPUT -o $INTIF -p udp -s $INTIP --sport 67 -d 255.255.255.255 --dport 68 -j ACCE$

# Internal interface, DNS traffic accepted
-A OUTPUT -o $INTIF -p tcp -s $INTIP --dport 53 -d 255.255.255.255 -j ACCEPT
-A OUTPUT -o $INTIF -p udp -s $INTIP --dport 53 -d 255.255.255.255 -j ACCEPT


# Catch all rule, all other outgoing is denied and logged. 
-A OUTPUT -s $UNIVERSE -d $UNIVERSE -j REJECT

# Accept solicited tcp packets
-A FORWARD -i $EXTIF -o $INTIF -m conntrack --ctstate ESTABLISHED,RELATED  -j ACCEPT

# Allow packets across the internal interface
-A FORWARD -i $INTIF -o $INTIF -j ACCEPT

# Forward packets from the internal network to the Internet
-A FORWARD -i $INTIF -o $EXTIF -j ACCEPT

#vpn
-A FORWARD -i tun+ -j ACCEPT
-A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
# Catch-all REJECT rule
-A FORWARD -j REJECT

COMMIT


###########################
# Address translations (only; there is no actual forwarding done here)
###########################
*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]

# ----- Begin OPTIONAL FORWARD Section -----

#Optionally forward incoming tcp connections on port 1234 to 192.168.0.100
#-A PREROUTING -p tcp -d $EXTIP --dport 1234 -m conntrack --ctstate NEW,ESTABLISHED,REL$
-A PREROUTING -p tcp -d $EXTIP --dport 22 -m conntrack --ctstate NEW,ESTABLISHED,RELATE$
-A PREROUTING -p udp -d $EXTIP --dport 22 -m conntrack --ctstate NEW,ESTABLISHED,RELATE$
-A PREROUTING -p tcp -d $EXTIP --dport 5555 -m conntrack --ctstate NEW,ESTABLISHED,RELA$


# ----- End OPTIONAL FORWARD Section -----

#vpn
-F POSTROUTING
-A POSTROUTING -s 10.8.0.0/24 -o $INTIF -j MASQUERADE

# IP-Masquerade
-A POSTROUTING -o $EXTIF -j MASQUERADE
###########################
*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]

# ----- Begin OPTIONAL FORWARD Section -----

#Optionally forward incoming tcp connections on port 1234 to 192.168.0.100
#-A PREROUTING -p tcp -d $EXTIP --dport 1234 -m conntrack --ctstate NEW,ESTABLISHED,REL$
-A PREROUTING -p tcp -d $EXTIP --dport 22 -m conntrack --ctstate NEW,ESTABLISHED,RELATE$
-A PREROUTING -p udp -d $EXTIP --dport 22 -m conntrack --ctstate NEW,ESTABLISHED,RELATE$
-A PREROUTING -p tcp -d $EXTIP --dport 5555 -m conntrack --ctstate NEW,ESTABLISHED,RELA$


# ----- End OPTIONAL FORWARD Section -----

#vpn
-F POSTROUTING
-A POSTROUTING -s 10.8.0.0/24 -o $INTIF -j MASQUERADE

# IP-Masquerade
-A POSTROUTING -o $EXTIF -j MASQUERADE

COMMIT
EOF

echo " done."


```

Forwading is enabled in the DSL Model.

---

### Post by sandyd on 2012-09-16
a) what VPN server software are you using?
b) post configuration file of VPN server software (i.e. /etc/openvpn/openvpn.conf for openvpn)

---

