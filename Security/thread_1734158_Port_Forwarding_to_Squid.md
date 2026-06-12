---
title: "Port Forwarding to Squid"
date: 2011-04-19
forum: Security
---

### Post by shivaram on 2011-04-19
Hi,
 
I have my firewall script as this.
 
FWVER= 0.76
echo -e "\n\nLoading simple rc.refewall-iptables version $FWVER.. \n"
IPTABLES=/sbin/iptables
DEPMOD=/sbin/depmod
MODPROBE=/sbin/modprobe
EXTIF="eth0"
INTIF="eth1"
echo " External Interface: $EXTIF"
echo " Internal Interface: $INTIF"
EXTIP="XXX.XXX.XXX.XXX"
echo "   External IP:  $EXTIP"
echo -en " loading modules :  "
echo "   - Verifying that all kernel modules are ok"
$DEPMOD -a
echo "------------------------------------------------------------------------"
echo -en "ip_tables,    "
$MODPROBE ip_tables
echo -en "ip_conntrack, "
$MODPROBE ip_conntrack
echo -en "ip_conntrack_ftp,"
$MODPROBE ip_conntrack_ftp
echo -en "ip_conntrack_irc,"
$MODPROBE ip_conntrack_irc
echo -en "iptable_nat,"
$MODPROBE iptable_nat
echo -en "ip_nat_ftp,"
$MODPROBE ip_nat_ftp
echo "-----------------------------------------------------------------------"
echo -e " Done loading modules. \n"
echo " Enabling forwarding ...."
echo "1"  > /proc/sys/net/ipv4/ip_forward
echo " Enabling DynamicAddr ...."
echo "1" > /proc/sys/net/ipv4/ip_dynaddr
echo  " CLEARNING ANY EXISTING RULES AND SETTING DEFAULT POLICY..."
$IPTABLES -P INPUT ACCEPT
$IPTABLES -F INPUT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD
$IPTABLES -t nat -F
echo "  FWD: Allow all connections OUT and only existing and related ones IN"
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
$IPTABLES -A FORWARD -j LOG
#$IPTABLES -t nat -A POSTROUTING -o $EXITIF -j SNAT --to $EXTIP
echo " Enabling SNAT (MASQUERADE) functionality on $EXITIF"
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE
echo -e "\nrc.firewall-iptables v$FWVER done.\n" 

 
Now everything is working fine. But I would like to do web filtering .
Please tell me how to forward web requests from clients to Squid?
Thanks in Advance.

---

### Post by Lars Noodén on 2011-04-22
It's called a transparent proxy and, technically, it "breaks" your network.  There are a lot of guides on how to set up Squid as a [transparent proxy](http://www.ivankristianto.com/os/ubuntu/howto-install-and-configure-squid-as-transparent-proxy/648/).

---

