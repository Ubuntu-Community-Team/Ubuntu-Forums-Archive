---
title: "Please check my iptables rules."
date: 2010-07-07
forum: Server Platforms
---

### Post by jayboogee on 2010-07-07
Hello All. I have a set of iptables I have downloaded and modified for my use. I had it working for 1 lan and wan access. I now would like to have: wan access, 1 lan, and 1 wlan. I need to administer the entire network from my wireless laptop on the wlan network so I need to be able to access the lan from the wlan network, and have the wlan access the lan network. Here are my rules. thank you for any assistance. 



#!/bin/sh

#  IPTABLES  FIREWALL  script for the Linux 2.6 kernel.
#  This script is a derivitive of the script presented in
#  the IP Masquerade HOWTO page at:
#  [www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html]("http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html")
#  It was simplified to coincide with the configuration of
#  the sample system presented in the Guides section of
#  [www.aboutdebian.com]("http://www.aboutdebian.com")
#
#  This script is presented as an example for testing ONLY
#  and should not be used on a production firewall.
#
#    PLEASE SET THE USER VARIABLES
#    IN SECTIONS A AND B OR C

echo -e "\n\nSETTING UP IPTABLES FIREWALL..."


# === SECTION A
# -----------   FOR EVERYONE

# SET THE INTERFACE DESIGNATION FOR THE NIC CONNECTED TO YOUR INTERNAL NETWORK
#   The default value below is for "eth1".  This value
#   could also be "eth1" if you have Three NICs in your system.
#   You can use the ifconfig command to list the interfaces
#   on your system.  The internal interface will likely have
#   have an address that is in one of the private IP address
#   ranges.
#       Note that this is an interface DESIGNATION - not
#       the IP address of the interface.
#   Enter the internal interface's designation for the
#   INTIF variable:

INTIF="eth1"

# Enter the NETWORK address the Internal Interface is on
INTNET="10.10.10.0/24"

# Enter the IP address of the Internal Interface
INTIP="10.10.10.1/24"


# SET THE INTERFACE DESIGNATION FOR THE NIC CONNECTED TO YOUR WIRELESS NETWORK
#   The default value below is for "eth2".  This value
#   could also be "eth1" if you have Three NICs in your system.
#   You can use the ifconfig command to list the interfaces
#   on your system.  The wireless interface will likely have
#   have an address that is in one of the private IP address
#   ranges.
#       Note that this is an interface DESIGNATION - not
#       the IP address of the interface.
#   Enter the internal interface's designation for the
#   WLANIF variable:

WLANIF="eth2"

# Enter the NETWORK address the Internal Interface is on
WLANNET="10.0.0.0/24"

# Enter the IP address of the Internal Interface
WLANIP="10.0.0.1/24"


# SET THE INTERFACE DESIGNATION FOR YOUR "EXTERNAL" (INTERNET) CONNECTION
#   The default value below is "ppp0" which is appropriate
#   for a MODEM connection.
#   If you have two NICs in your system change this value
#   to "eth0" or "eth1" (whichever is opposite of the value
#   set for INTIF above).  This would be the NIC connected
#   to your cable or DSL modem (WITHOUT a cable/DSL router).
#       Note that this is an interface DESIGNATION - not
#       the IP address of the interface.
#   Enter the external interface's designation for the
#   EXTIF variable:

EXTIF="eth0"


# ! ! ! ! !  Use ONLY Section B  *OR*  Section C depending on
#  ! ! ! !   the type of Internet connection you have.


# === SECTION B
# -----------   FOR THOSE WITH STATIC PUBLIC IP ADDRESSES

   # SET YOUR EXTERNAL IP ADDRESS
   #   If you specified a NIC (i.e. "eth0" or "eth1" for
   #   the external interface (EXTIF) variable above,
   #   AND if that external NIC is configured with a
   #   static, public IP address (assigned by your ISP),
   #   UNCOMMENT the following EXTIP line and enter the
   #   IP address for the EXTIP variable:

#EXTIP="your.static.IP.address"



# === SECTION C
# ----------   RESIDENTIAL CABLE-MODEM/DSL (Dynamic IP) USERS


# SET YOUR EXTERNAL INTERFACE FOR DYNAMIC IP ADDRESSING
#   If you get your IP address dynamically from SLIP, PPP,
#   BOOTP, or DHCP, UNCOMMENT the command below.
#   (No values have to be entered.)
#         Note that if you are uncommenting these lines then
#         the EXTIP line in Section B must be commented out.

EXTIP="`/sbin/ifconfig eth0 | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`"


# --------  No more variable setting beyond this point  --------


echo "Loading required stateful/NAT kernel modules..."

/sbin/depmod -a
/sbin/modprobe ip_tables
/sbin/modprobe ip_conntrack
/sbin/modprobe ip_conntrack_ftp
/sbin/modprobe ip_conntrack_irc
/sbin/modprobe iptable_nat
/sbin/modprobe ip_nat_ftp
/sbin/modprobe ip_nat_irc

echo "    Enabling IP forwarding..."
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "1" > /proc/sys/net/ipv4/ip_dynaddr

echo "    External interface: $EXTIF"
echo "       External interface IP address is: $EXTIP"

echo "    Loading proxy server rules..."

UNIVERSE="0.0.0.0/0"

# Clearing any existing rules and setting default policy to DROP
iptables -P INPUT DROP
iptables -F INPUT
iptables -P OUTPUT DROP
iptables -F OUTPUT
iptables -P FORWARD DROP
iptables -F FORWARD
iptables -F -t nat


# Flush the user chain.. if it exists
if [ "`iptables -L | grep drop-and-log-it`" ]; then
   iptables -F drop-and-log-it
fi

# Delete all User-specified chains
iptables -X

# Reset all IPTABLES counters
iptables -Z

# Creating a DROP chain
iptables -N drop-and-log-it
iptables -A drop-and-log-it -j LOG --log-level info
iptables -A drop-and-log-it -j DROP

echo -e "     - Loading INPUT rulesets"

#######################################################################
# INPUT: Incoming traffic from various interfaces.  All rulesets are
#        already flushed and set to a default policy of DROP.
#

# loopback interfaces are valid.
iptables -A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT

# local interface, local machines, going anywhere is valid
iptables -A INPUT -i $INTIF -s $INTNET -d $UNIVERSE -j ACCEPT

# wireless interface, wireless machines, going anywhere is valid
iptables -A INPUT -i $WLANIF -s $WLANNET -d $UNIVERSE -j ACCEPT

# remote interface, claiming to be local machines, IP spoofing, get lost
iptables -A INPUT -i $EXTIF -s $INTNET -d $UNIVERSE -j drop-and-log-it

# remote interface, claiming to be wireless machines, IP spoofing, get lost
iptables -A INPUT -i $EXTIF -s $WLANNET -d $UNIVERSE -j drop-and-log-it

# stop DHCP server requests from filling up the log files
iptables -I INPUT -p UDP -i $EXTIF --dport 68 --sport 67 --source 0.0.0.0 -j ACCEPT

# remote interface, any source, going to permanent PPP address is valid
#iptables -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -j ACCEPT

# Allow any related traffic coming back to the MASQ server in
iptables -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state ESTABLISHED,RELATED -j ACCEPT

# Catch all rule, all other incoming is denied and logged.
iptables -A INPUT -s $UNIVERSE -d $UNIVERSE -j drop-and-log-it


echo -e "     - Loading OUTPUT rulesets"

#######################################################################
# OUTPUT: Outgoing traffic from various interfaces.  All rulesets are
#         already flushed and set to a default policy of DROP.
#

# loopback interface is valid.
iptables -A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT

# local interfaces, any source going to local net is valid
iptables -A OUTPUT -o $INTIF -s $EXTIP -d $INTNET -j ACCEPT

# wireless interfaces, any source going to wireless net is valid
iptables -A OUTPUT -o $WLANIF -s $EXTIP -d $WLANNET -j ACCEPT

# local interface, any source going to local net is valid
iptables -A OUTPUT -o $INTIF -s $INTIP -d $INTNET -j ACCEPT

# wireless interface, any source going to wireless net is valid
iptables -A OUTPUT -o $WLANIF -s $WLANIP -d $WLANNET -j ACCEPT

# outgoing to local net on remote interface, stuffed routing, deny
iptables -A OUTPUT -o $EXTIF -s $UNIVERSE -d $INTNET -j drop-and-log-it

# outgoing to wireless net on remote interface, stuffed routing, deny
iptables -A OUTPUT -o $EXTIF -s $UNIVERSE -d $WLANNET -j drop-and-log-it

# anything else outgoing on remote interface is valid
iptables -A OUTPUT -o $EXTIF -s $EXTIP -d $UNIVERSE -j ACCEPT

# Catch all rule, all other outgoing is denied and logged.
iptables -A OUTPUT -s $UNIVERSE -d $UNIVERSE -j drop-and-log-it


echo -e "     - Loading FORWARD rulesets"

#######################################################################
# FORWARD: Enable Forwarding and thus IPMASQ
#          Allow all connections OUT and only existing/related IN

iptables -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT

iptables -A FORWARD -i $EXTIF -o $WLANIF -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i $WLANIF -o $EXTIF -j ACCEPT

# Catch all rule, all other forwarding is denied and logged.
iptables -A FORWARD -j drop-and-log-it

# Enable SNAT (MASQUERADE) functionality on $EXTIF
iptables -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP

echo -e "    Firewall server rule loading complete\n\n"

---

### Post by frankvw on 2010-07-08
Rather than to sort though all your iptable rules (which can be quite a puzzle) you might want to try **fwbuilder**, which is an OSS GUI-based tool for creating a set of firewall rules for just about any occasion. This will make your configuration and maintenance jobs easier, too.

[www.fwbuilder.org]("http://www.fwbuilder.org")

// FvW

---

### Post by benderisgreat on 2010-07-08
> I need to be able to access the lan from the wlan network, and have the wlan access the lan network
add
```
iptables -A FORWARD -i $INTIF -o $WLANIF -j ACCEPT
iptables -A FORWARD -i $WLANIF -o $INTIF -j ACCEPT
```

if you don't understand iptables nor care to learn you could indeed take a look at fwbuilder as frankvw suggests.

---

### Post by jayboogee on 2010-07-09
Thanks for your help.

---

