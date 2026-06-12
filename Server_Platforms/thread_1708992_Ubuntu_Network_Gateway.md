---
title: "Ubuntu Network Gateway"
date: 2011-03-17
forum: Server Platforms
---

### Post by inckiekage on 2011-03-17
I have a gateway with 3 Nic

eth0 - WAN
eth1 - LAN
eth2 - DMZ

I have NAT up and running, and hosts on both subnets can access the internet.

Interface
```
FW:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# LAN
auto eth1
iface eth1 inet static
           address 192.168.1.1
           netmask 255.255.255.0
# DMZ
auto eth2
iface eth2 inet static
        address 192.168.10.1
        netmask 255.255.255.0
```

my problems is that there is no route between the hosts on the subnets.


IP Route - WAN IP: 192.168.106.135
```
FW:~$ ip route show
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.1 
192.168.10.0/24 dev eth2  proto kernel  scope link  src 192.168.10.1 
192.168.106.0/24 dev eth0  proto kernel  scope link  src 192.168.106.135 
default via 192.168.106.2 dev eth0  metric 100
```


Here is my iptables script
```
#!/bin/sh
#
#firewall-iptables
FWVER= 0.76

#
#               Initial SIMPLE IP Masquerade test for 2.6 / 2.4 kernels
#               using IPTABLES.
#
#               Once IP Masquerading has been tested, with this simple
#               ruleset, it is highly recommended to use a stronger
#               IPTABLES ruleset either given later in this HOWTO or
#               from another reputable resource.

echo -e "\n\nLoading simple rc.firewall-iptables version $FWVER..\n"


# The location of the iptables and kernel module programs
#
#   If your Linux distribution came with a copy of iptables,
#   most likely all the programs will be located in /sbin.  If
#   you manually compiled iptables, the default location will
#   be in /usr/local/sbin
#
# ** Please use the "whereis iptables" command to figure out
# ** where your copy is and change the path below to reflect
# ** your setup
#
IPTABLES=/sbin/iptables
#IPTABLES=/usr/local/sbin/iptables
DEPMOD=/sbin/depmod
MODPROBE=/sbin/modprobe


#Setting the EXTERNAL and INTERNAL interfaces for the network
#
#  Each IP Masquerade network needs to have at least one
#  external and one internal network.  The external network
#  is where the natting will occur and the internal network
#  should preferably be addressed with a RFC1918 private address
#  scheme.
#
#  For this example, "eth0" is external and "eth1" is internal"
#
#
#  NOTE:  If this doesnt EXACTLY fit your configuration, you must
#         change the EXTIF or INTIF variables above. For example:
#
#            If you are a PPPoE or analog modem user:
#
#               EXTIF="ppp0"
#
#
EXTIF="eth0"
INTIF="eth1"
INTIF2="eth2"
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"
echo "   Internal Interface:  $INTIF2"

EXTIP="192.168.106.135"
echo "   External IP:  $EXTIP"

#======================================================================
#== No editing beyond this line is required for initial MASQ testing ==


echo -en "   loading modules: "

# Need to verify that all modules have all required dependencies
#
echo "  - Verifying that all kernel modules are ok"
$DEPMOD -a

# With the new IPTABLES code, the core MASQ functionality is now either
# modular or compiled into the kernel.  This HOWTO shows ALL IPTABLES
# options as MODULES.  If your kernel is compiled correctly, there is
# NO need to load the kernel modules manually.
#
#  NOTE: The following items are listed ONLY for informational reasons.
#        There is no reason to manual load these modules unless your
#        kernel is either mis-configured or you intentionally disabled
#        the kernel module autoloader.
#

# Upon the commands of starting up IP Masq on the server, the
# following kernel modules will be automatically loaded:
#
# NOTE:  Only load the IP MASQ modules you need.  All current IP MASQ
#        modules are shown below but are commented out from loading.
# ===============================================================

echo "----------------------------------------------------------------------"

#Load the main body of the IPTABLES module - "iptable"
#  - Loaded automatically when the "iptables" command is invoked
#
#  - Loaded manually to clean up kernel auto-loading timing issues
#
echo -en "ip_tables, "
$MODPROBE ip_tables


#Load the IPTABLES filtering module - "iptable_filter"
#  - Loaded automatically when filter policies are activated


#Load the stateful connection tracking framework - "ip_conntrack"
#
# The conntrack  module in itself does nothing without other specific
# conntrack modules being loaded afterwards such as the "ip_conntrack_ftp"
# module
#
#  - This module is loaded automatically when MASQ functionality is
#    enabled
#
#  - Loaded manually to clean up kernel auto-loading timing issues
#
echo -en "ip_conntrack, "
$MODPROBE ip_conntrack


#Load the FTP tracking mechanism for full FTP tracking
#
# Enabled by default -- insert a "#" on the next line to deactivate
#
echo -en "ip_conntrack_ftp, "
$MODPROBE ip_conntrack_ftp


#Load the IRC tracking mechanism for full IRC tracking
#
# Enabled by default -- insert a "#" on the next line to deactivate
#
echo -en "ip_conntrack_irc, "
$MODPROBE ip_conntrack_irc


#Load the general IPTABLES NAT code - "iptable_nat"
#  - Loaded automatically when MASQ functionality is turned on
#
#  - Loaded manually to clean up kernel auto-loading timing issues
#
echo -en "iptable_nat, "
$MODPROBE iptable_nat


#Loads the FTP NAT functionality into the core IPTABLES code
# Required to support non-PASV FTP.
#
# Enabled by default -- insert a "#" on the next line to deactivate
#
echo -en "ip_nat_ftp, "
$MODPROBE ip_nat_ftp


#Loads the IRC NAT functionality into the core IPTABLES code
# Required to support NAT of IRC DCC requests
#
# Disabled by default -- remove the "#" on the next line to activate
#
#echo -e "ip_nat_irc"
#$MODPROBE ip_nat_irc

echo "----------------------------------------------------------------------"

# Just to be complete, here is a partial list of some of the other
# IPTABLES kernel modules and their function.  Please note that most
# of these modules (the ipt ones) are automatically loaded by the
# master kernel module for proper operation and don't need to be
# manually loaded.
# --------------------------------------------------------------------
#
#    ip_nat_snmp_basic - this module allows for proper NATing of some
#                        SNMP traffic
#
#    iptable_mangle    - this target allows for packets to be
#                        manipulated for things like the TCPMSS
#                        option, etc.
#
# --
#
#    ipt_mark       - this target marks a given packet for future action.
#                     This automatically loads the ipt_MARK module
#
#    ipt_tcpmss     - this target allows to manipulate the TCP MSS
#                     option for braindead remote firewalls.
#                     This automatically loads the ipt_TCPMSS module
#
#    ipt_limit      - this target allows for packets to be limited to
#                     to many hits per sec/min/hr
#
#    ipt_multiport  - this match allows for targets within a range
#                     of port numbers vs. listing each port individually
#
#    ipt_state      - this match allows to catch packets with various
#                     IP and TCP flags set/unset
#
#    ipt_unclean    - this match allows to catch packets that have invalid
#                     IP/TCP flags set
#
#    iptable_filter - this module allows for packets to be DROPped,
#                     REJECTed, or LOGged.  This module automatically
#                     loads the following modules:
#
#                     ipt_LOG - this target allows for packets to be
#                               logged
#
#                     ipt_REJECT - this target DROPs the packet and returns
#                                  a configurable ICMP packet back to the
#                                  sender.
#

echo -e "   Done loading modules.\n"



#CRITICAL:  Enable IP forwarding since it is disabled by default since
#
#           Redhat Users:  you may try changing the options in
#                          /etc/sysconfig/network from:
#
#                       FORWARD_IPV4=false
#                             to
#                       FORWARD_IPV4=true
#
echo "   Enabling forwarding.."
echo "1" > /proc/sys/net/ipv4/ip_forward


# Dynamic IP users:
#
#   If you get your IP address dynamically from SLIP, PPP, or DHCP,
#   enable this following option.  This enables dynamic-address hacking
#   which makes the life with Diald and similar programs much easier.
#
echo "   Enabling DynamicAddr.."
echo "1" > /proc/sys/net/ipv4/ip_dynaddr


# Enable simple IP forwarding and Masquerading
#
#  NOTE:  In IPTABLES speak, IP Masquerading is a form of SourceNAT or SNAT.
#
#  NOTE #2:  The following is an example for an internal LAN address in the
#            192.168.0.x network with a 255.255.255.0 or a "24" bit subnet mask
#            connecting to the Internet on external interface "eth0".  This
#            example will MASQ internal traffic out to the Internet but not
#            allow non-initiated traffic into your internal network.
#
#
#         ** Please change the above network numbers, subnet mask, and your
#         *** Internet connection interface name to match your setup
#


#Clearing any previous configuration
#
#  Unless specified, the defaults for INPUT and OUTPUT is ACCEPT
#    The default for FORWARD is DROP (REJECT is not a valid policy)
#
#   Isn't ACCEPT insecure?  To some degree, YES, but this is our testing
#   phase.  Once we know that IPMASQ is working well, I recommend you run
#   the rc.firewall-*-stronger rulesets which set the defaults to DROP but
#   also include the critical additional rulesets to still let you connect to
#   the IPMASQ server, etc.
#
echo "   Clearing any existing rules and setting default policy.."
$IPTABLES -P INPUT ACCEPT
$IPTABLES -F INPUT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD
$IPTABLES -t nat -F

echo "   FWD: Allow all connections OUT and only existing and related ones IN"
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED \-j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
$IPTABLES -A FORWARD -j LOG
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF2 -m state --state ESTABLISHED,RELATED \-j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $INTIF2 -m state --state ESTABLISHED,RELATED \-j ACCEPT
$IPTABLES -A FORWARD -i $INTIF2 -o $INTIF -m state --state ESTABLISHED,RELATED \-j ACCEPT
$IPTABLES -A FORWARD -i $INTIF2 -o $EXTIF -j ACCEPT
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP


echo "   Enabling SNAT (MASQUERADE) functionality on $EXTIF"
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

echo -e "\nrc.firewall-iptables v$FWVER done.\n"

```

---

### Post by SeijiSensei on 2011-03-18
Your routing table looks fine.  I suspect it's a different problem.

Run "cat /proc/sys/net/ipv4/ip_forward" and see what it returns.  If it's zero, IP forwarding is disabled in the kernel (that's the default).  Edit the file /etc/sysctl.conf and change the net.ipv4.ip_forward flag to one as described there.  

A quick check to see if this fixes the problem without the need to reboot is to run the command:

```
sudo echo '1' > /proc/sys/net/ipv4/ip_forward
```

and see if everything works.  If so, make the change in /etc/sysctl.conf.

---

