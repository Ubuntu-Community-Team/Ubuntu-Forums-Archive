---
title: "iptables rules blocking outlook outgoing mail?"
date: 2010-05-12
forum: Security
---

### Post by tumandro on 2010-05-12
Hello all,

I have a linux box set up as a firewall/router at my parents house. My father is having problems sending outgoing mail to his work from home but can do it fine from a public wifi source. I have a similar firewall set up at home and am experiencing the same problem as him. I was just wondering if anyone knew the best course of action to get this working? my firewall rules are as follows (ip's taken out but otherwise the same).

 ```
#!/bin/sh
  #
  # rc.firewall-iptables-stronger
  #
  FWVER=0.88s

echo -e "\nLoading rc.firewall-iptables-STRONGER - version $FWVER..\n"
  IPTABLES=/sbin/iptables
  #IPTABLES=/usr/local/sbin/iptables
  LSMOD=/sbin/lsmod
  DEPMOD=/sbin/depmod
  MODPROBE=/sbin/modprobe
  GREP=/bin/grep
  AWK=/usr/bin/awk
  IFCONFIG=/sbin/ifconfig
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
  #  NOTE:  If this doesnt EXACTLY fit your configuration, you must
  #         change the EXTIF or INTIF variables above. For example:
  #
  #            If you are a PPPoE or analog modem user:
  #
  #               EXTIF="ppp0"
  #
  EXTIF="eth1"
  INTIF="eth2"
  echo "  External Interface:  $EXTIF"
  echo "  Internal Interface:  $INTIF"
  echo "  ---"

EXTIP="`$IFCONFIG $EXTIF | $AWK \
   /$EXTIF/'{next}//{split($0,a,":");split(a[2],a," ");print a[1];exit}'`"
  # For users who wish to use STATIC IP addresses:
  #
  #  # out the EXTIP line above and un-# out the EXTIP line below
  #
  #EXTIP="your.static.PPP.address"
  echo "  External IP: $EXTIP"
  echo "  ---"


  # Assign the internal TCP/IP network and IP address
  INTNET=""
  INTIP=""
  echo "  Internal Network: $INTNET"
  echo "  Internal IP:      $INTIP"
  echo "  ---"



  # Setting a few other local variables
  #
  UNIVERSE="0.0.0.0/0"

echo "  - Verifying that all kernel modules are ok"
  $DEPMOD -a

  echo -en "    Loading kernel modules: "
  #Load the main body of the IPTABLES module - "ip_tables"
  #  - Loaded automatically when the "iptables" command is invoked
  #
  #  - Loaded manually to clean up kernel auto-loading timing issues
  #
  echo -en "ip_tables, "
  #
  #Verify the module isn't loaded.  If it is, skip it
  #
  if [ -z "` $LSMOD | $GREP ip_tables | $AWK {'print $1'} `" ]; then
     $MODPROBE ip_tables
  fi


  #Load the IPTABLES filtering module - "iptable_filter"
  #
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

if [ -z "` $LSMOD | $GREP ip_conntrack | $AWK {'print $1'} `" ]; then
     $MODPROBE ip_conntrack
  fi


  #Load the FTP tracking mechanism for full FTP tracking
  #
  # Enabled by default -- insert a "#" on the next line to deactivate
  #
  echo -e "ip_conntrack_ftp, "
  #
  #Verify the module isn't loaded.  If it is, skip it
  #
  if [ -z "` $LSMOD | $GREP ip_conntrack_ftp | $AWK {'print $1'} `" ]; then
     $MODPROBE ip_conntrack_ftp
 fi


  #Load the IPTABLES filtering module - "iptable_filter"
  #
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

 if [ -z "` $LSMOD | $GREP ip_conntrack | $AWK {'print $1'} `" ]; then
     $MODPROBE ip_conntrack
  fi


  #Load the FTP tracking mechanism for full FTP tracking
  #
  # Enabled by default -- insert a "#" on the next line to deactivate
  #
  echo -e "ip_conntrack_ftp, "
  #
  #Verify the module isn't loaded.  If it is, skip it
  #
  if [ -z "` $LSMOD | $GREP ip_conntrack_ftp | $AWK {'print $1'} `" ]; then
     $MODPROBE ip_conntrack_ftp
  fi

if [ -z "` $LSMOD | $GREP iptable_nat | $AWK {'print $1'} `" ]; then
     $MODPROBE iptable_nat
  fi
  if [ -z "` $LSMOD | $GREP ip_nat_ftp | $AWK {'print $1'} `" ]; then
     $MODPROBE ip_nat_ftp
  fi
  echo "  ---"

 echo "  Enabling forwarding.."
  echo "1" > /proc/sys/net/ipv4/ip_forward


  # Dynamic IP users:
  #
  #   If you get your IP address dynamically from SLIP, PPP, or DHCP,
  #   enable the following option.  This enables dynamic-address hacking
  #   which makes the life with Diald and similar programs much easier.
  #
  echo "  Enabling DynamicAddr.."
 echo "1" > /proc/sys/net/ipv4/ip_dynaddr

  echo "  ---"

echo "  Clearing any existing rules and setting default policy to DROP.."
  $IPTABLES -P INPUT DROP
  $IPTABLES -F INPUT
  $IPTABLES -P OUTPUT DROP
  $IPTABLES -F OUTPUT
  $IPTABLES -P FORWARD DROP
  $IPTABLES -F FORWARD
  $IPTABLES -F -t nat

  #Not needed and it will only load the unneeded kernel module
  #
  #$IPTABLES -F -t mangle


  # Delete all User-specified chains
  $IPTABLES -X


  # Reset all IPTABLES counters
  $IPTABLES -Z

echo "  Creating a DROP chain.."
  $IPTABLES -N reject-and-log-it
  $IPTABLES -A reject-and-log-it -j LOG --log-level info
  $IPTABLES -A reject-and-log-it -j DROP

  echo -e "\n   - Loading INPUT rulesets"


  #######################################################################
  # INPUT: Incoming traffic from various interfaces.  All rulesets are
  #        already flushed and set to a default policy of DROP.
  #

  # loopback interfaces are valid.
  #
  $IPTABLES -A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT


  # local interface, local machines, going anywhere is valid
  #
  $IPTABLES -A INPUT -i $INTIF -s $INTNET -d $UNIVERSE -j ACCEPT


  # remote interface, claiming to be local machines, IP spoofing, get lost
  #
  $IPTABLES -A INPUT -i $EXTIF -s $INTNET -d $UNIVERSE -j reject-and-log-it


  # external interface, from any source, for ICMP traffic is valid
  #
  #  If you would like your machine to "ping" from the Internet,
  #  enable this next line

 #
  $IPTABLES -A INPUT -i $EXTIF -p ICMP -s $UNIVERSE -d $EXTIP -j ACCEPT

   #tunnels for openvpn
  $IPTABLES -A INPUT -i tun+ -j ACCEPT
  $IPTABLES -A OUTPUT -o tun+ -j ACCEPT
  $IPTABLES -A FORWARD -i tun+ -j ACCEPT

 echo -e "statefully tracked"
  # Allow any related traffic coming back to the MASQ server in.
  #
  #  STATEFULLY TRACKED
  #
  $IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state ESTABLISH
ED,RELATED -j ACCEPT

  echo -e "dchpd ****"
  # ----- Begin OPTIONAL INPUT Section -----
  #

  # DHCPd - Enable the following lines if you run an INTERNAL DHCPd server
  #
  $IPTABLES -A INPUT -i $INTIF -p tcp --sport 68 --dport 67 -j ACCEPT
  $IPTABLES -A INPUT -i $INTIF -p udp --sport 68 --dport 67 -j ACCEPT
  $IPTABLES -A INPUT -i $INTIF -p udp --sport 69 --dport 69 -j ACCEPT

  # HTTPd - Enable the following lines if you run an EXTERNAL WWW server
  #
  #    NOTE:  This is NOT needed for simply enabling PORTFW.  This is ONLY
  #           for users that plan on running Apache on the MASQ server itself
  #
  #echo -e "      - Allowing EXTERNAL access to the SSH server"
  #$IPTABLES -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED \
  # -p tcp -s $UNIVERSE -d $EXTIP --dport 80 -j ACCEPT
  echo -e "SSH INCOMING TO HOST"
  $IPTABLES -A INPUT -i $EXTIF -p tcp -s $UNIVERSE -d $EXTIP --dport 22 -j ACCEP
T

  #
  # ----- End OPTIONAL INPUT Section -----

# Catch all rule, all other incoming is denied and logged.
  #
  $IPTABLES -A INPUT -s $UNIVERSE -d $UNIVERSE -j reject-and-log-it


  # ---------------------------------------------------------------------

  echo -e "   - Loading OUTPUT rulesets"

  #######################################################################
  # OUTPUT: Outgoing traffic from various interfaces.  All rulesets are
  #         already flushed and set to a default policy of DROP.
  #

  # Workaround bug in netfilter
  # See [http://www.netfilter.org/security/2002-04-02-icmp-dnat.html](http://www.netfilter.org/security/2002-04-02-icmp-dnat.html)
 #
  $IPTABLES -A OUTPUT -m state -p icmp --state INVALID -j DROP

  # loopback interface is valid.
  #
  $IPTABLES -A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT


  # local interfaces, any source going to local net is valid
  #
  $IPTABLES -A OUTPUT -o $INTIF -s $EXTIP -d $INTNET -j ACCEPT


  # local interface, MASQ server source going to the local net is valid
  #
  $IPTABLES -A OUTPUT -o $INTIF -s $INTIP -d $INTNET -j ACCEPT


  # outgoing to local net on remote interface, stuffed routing, deny
  #
  $IPTABLES -A OUTPUT -o $EXTIF -s $UNIVERSE -d $INTNET -j reject-and-log-it

 # anything else outgoing on remote interface is valid
  #
  $IPTABLES -A OUTPUT -o $EXTIF -s $EXTIP -d $UNIVERSE -j ACCEPT


  # ----- Begin OPTIONAL OUTPUT Section -----
  #

  # DHCPd - Enable the following lines if you run an INTERNAL DHCPd server
  #         - Remove BOTH #s all the #s if you need this functionality.
  #
  $IPTABLES -A OUTPUT -o $INTIF -p tcp -s $INTIP --sport 67 \
   -d 255.255.255.255 --dport 68 -j ACCEPT
  $IPTABLES -A OUTPUT -o $INTIF -p udp -s $INTIP --sport 67 \
   -d 255.255.255.255 --dport 68 -j ACCEPT
  $IPTABLES -A INPUT -p udp --dport 1194 -j ACCEPT

  #
  # ----- End OPTIONAL OUTPUT Section -----


  # Catch all rule, all other outgoing is denied and logged.
  #
  $IPTABLES -A OUTPUT -s $UNIVERSE -d $UNIVERSE -j reject-and-log-it


  echo -e "   - Loading FORWARD rulesets"

  #######################################################################
  # FORWARD: Enable Forwarding and thus IPMASQ
  #

  # ----- Begin OPTIONAL FORWARD Section -----
  #
  #  Put PORTFW commands here
 #
  # ----- End OPTIONAL FORWARD Section -----


  echo "     - FWD: Allow all connections OUT and only existing/related IN"
  $IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED
\
   -j ACCEPT
  $IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT

 # Catch all rule, all other forwarding is denied and logged.
  #
  $IPTABLES -A FORWARD -j reject-and-log-it


  echo "     - NAT: Enabling SNAT (MASQUERADE) functionality on $EXTIF"
  #
  #More liberal form
  #$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE
  #
  #Stricter form
  $IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP


  #######################################################################
  echo -e "\nrc.firewall-iptables-stronger $FWVER done.\n"
```

---

### Post by schwascore on 2010-05-12
We'd need to know the protocol and port numbers that outlook needs to connect to for your father's work email. Share that and then perhaps someone could help.

---

### Post by tumandro on 2010-05-12
I'm pretty sure it's just using smtp and the standard port (25) for it. I can receive e-mail from the server but not send, it's using pop3.

---

### Post by spynappels on 2010-05-13
Would it be possible to just post the iptables rules rather than the whole script?

You will need to allow TCP traffic on port 25 outbound, and I'm not sure if I missed it, but do you allow connected and related connections?

---

### Post by tumandro on 2010-05-13
$IPTABLES -P INPUT DROP
  $IPTABLES -F INPUT
  $IPTABLES -P OUTPUT DROP
  $IPTABLES -F OUTPUT
  $IPTABLES -P FORWARD DROP
  $IPTABLES -F FORWARD
  $IPTABLES -F -t nat
  $IPTABLES -X
  $IPTABLES -Z
  $IPTABLES -N reject-and-log-it
  $IPTABLES -A reject-and-log-it -j LOG --log-level info
  $IPTABLES -A reject-and-log-it -j DROP
  $IPTABLES -A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT
  $IPTABLES -A INPUT -i $INTIF -s $INTNET -d $UNIVERSE -j ACCEPT
  $IPTABLES -A INPUT -i $EXTIF -s $INTNET -d $UNIVERSE -j reject-and-log-it
  $IPTABLES -A INPUT -i $EXTIF -p ICMP -s $UNIVERSE -d $EXTIP -j ACCEPT
  $IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state ESTABLISHED,RELATED -j ACCEPT
  $IPTABLES -A INPUT -i $INTIF -p tcp --sport 68 --dport 67 -j ACCEPT
  $IPTABLES -A INPUT -i $INTIF -p udp --sport 68 --dport 67 -j ACCEPT
  $IPTABLES -A INPUT -i $EXTIF -p tcp -s $UNIVERSE -d $EXTIP --dport 22 -j ACCEPT
  $IPTABLES -A INPUT -s $UNIVERSE -d $UNIVERSE -j reject-and-log-it
  $IPTABLES -A OUTPUT -m state -p icmp --state INVALID -j DROP
  $IPTABLES -A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT
  $IPTABLES -A OUTPUT -o $INTIF -s $EXTIP -d $INTNET -j ACCEPT
  $IPTABLES -A OUTPUT -o $INTIF -s $INTIP -d $INTNET -j ACCEPT
  $IPTABLES -A OUTPUT -o $EXTIF -s $UNIVERSE -d $INTNET -j reject-and-log-it
  $IPTABLES -A OUTPUT -o $EXTIF -s $EXTIP -d $UNIVERSE -j ACCEPT
  $IPTABLES -A OUTPUT -o $INTIF -p tcp -s $INTIP --sport 67 -d 255.255.255.255 --dport 68 -j ACCEPT
  $IPTABLES -A OUTPUT -o $INTIF -p udp -s $INTIP --sport 67 -d 255.255.255.255 --dport 68 -j ACCEPT
  $IPTABLES -A INPUT -p udp --dport 1194 -j ACCEPT
  $IPTABLES -A OUTPUT -s $UNIVERSE -d $UNIVERSE -j reject-and-log-it
  $IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED \
  $IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
  $IPTABLES -A FORWARD -j reject-and-log-it
  $IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP


I believe the that it is set currently it should allow all outbound traffic and existing and related connections in... Think I might have to run wireshark when I get home and see if I can see the packets leaving...

---

### Post by tumandro on 2010-05-14
Went home and checked to see if wireshark could detect outgoing smtp packets and guess what? They're going out but nothing is coming back in... Very frustrating. Anyone have any ideas? I was thinking maybe both of our ips were on a blacklist but it is just really weird that it's happening at home but not elsewhere...

---

### Post by The Cog on 2010-05-14
> **tumandro said:**
> Went home and checked to see if wireshark could detect outgoing smtp packets and guess what? They're going out but nothing is coming back in... Very frustrating. Anyone have any ideas? I was thinking maybe both of our ips were on a blacklist but it is just really weird that it's happening at home but not elsewhere...

Some ISPs filter port 25 by default, as a measure to prevent spamming zombies. Maybe ask your ISP if they are blocking it?

Seeng the real iptables rules would be more informative than seeing an extract from the script:
**sudo iptables-save -c**
would do nicely.

---

### Post by spynappels on 2010-05-14
Thanks Cog, that was the command I was trying to remember.

---

