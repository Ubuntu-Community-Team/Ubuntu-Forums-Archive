---
title: "HOWTO: Ubuntu internet router: IPTables,DHCP,DNS,&amp; IP Masq"
date: 2006-01-03
forum: Tutorials
---

### Post by Ellias on 2006-01-03
HOWTO-Ubuntu internet router, Firewall,DHCP,DNS,NAT
By: Ellias, special thanks to Mips 
Original Thread: [http://ubuntuforums.org/showthread.php?t=89320](http://ubuntuforums.org/showthread.php?t=89320)

This tutorial will go over all the steps one must take in order to set-up routing on a Linux box. There are some minimum requirements you must have in order to follow this tutorial to its completion. First you need a PC with Linux on it, the examples I will be giving are based off the Ubuntu distribution, but my examples should work on most other Debian based distributions and only slight modifications are needed to get it to work with Red Hat, etc... Second, you need two NICs. In my examples I will be showing how to do this with three NICs, 1 external and 2 internal. You probably need two cross-over cables to connect from PC to PC and one straight-through to connect from PC to modem, router, or switch (that will be on your external NIC). I say probably because some more advanced NICs support automatic conversion between the two. Thirdly, you need a somewhat working knowledge of Linux and networking in general, I will be covering a wide range of networking topics that are necessary to gain router functionality. Now before we get our feet wet, disclaimer time...

I am not responsible for any damage done to your computers and/or network. By following the instructions in this document you agree to these terms and recognize that you are solely responsible for what you do while following the instructions. Furthermore, the scripts provided here should NOT be used for a production and/or business environment. They are not secure and further modification would be needed in order to make them so. These instructions are for home use, educational purposes only.

There, now here is the setup I will be referring to in this document.

Internet
|
L Router (192.168.0.1) ----- PC's connected to router
|
|
Switch (typical 4 port) ----- PC's connect to switch 
|
|
Our Linux Box with Ubuntu Linux (connected to switch as well)
(3 NICs)
L eth2 (192.168.0.103) via DHCP from Router above.
L eth1 (192.168.1.1 ) Statically assigned --------- Connecting PC
L eth2 (192.168.2.1) Statically assigned --------- Connecting PC

Do a quick ifconfig to verify you have the setup correct (subnet mask is 255.255.255.0).

Also, here are a few troubleshooting programs I recommend getting ahold of...
sudo apt-get install traceroute
sudo apt-get install build-essential (C compiler for ethereal)
sudo apt-get install ethereal

Ok, so you've got things setup and ready to go. Now you need a way for the PCs connecting to the Linux box to get an IP address. For this we can use the DHCP server that comes with Linux. If you don't already have this a simple 'sudo apt-get install dhcp3-server' should get it for you just fine.

Once this is done you're going to have to configure it. The base of this configuration file was taken from Sean O'Donnell [http://code.seanodonnell.com](http://code.seanodonnell.com), but modified to fit our configuration here.

So type.... **'vim /etc/dhcp3/dhcpd.conf'**
and put the following in there (numbers may need to be tweaked for your setup)

**dhcpd.conf**
```

# Configuration file for ISC dhcpd (see 'man dhcpd.conf')
#
# For more information regarding the ISC DHCP Daemon,
# please visit: http://www.isc.org/sw/dhcp/
#
##########################################################
#
# Configuration Notes:
#
# This configuration file assumes that you
# have a total of 4 NIC cards installed on your system,
# with eth2 connecting (as a client) to a remote dhcp server. 
#
# This will assign a dhcp subnet to each additional NIC card
# (eth1, eth0), which can be used to create a
# multi-subnet DHCP Server.
#
# Example by: Sean O'Donnell http://code.seanodonnell.com
#
##########################################################
#
# DHCP CLIENT CONFIGURATION SETTINGS
#

# use ad-hoc style name server updating procedures
ddns-update-style ad-hoc; 

# this may be required for some network configurations,
# but seems to work fine without it on my LAN.
option domain-name "my-dhcp-server.com";

#assign the remote dhcp server hostname/ip addresses 
option domain-name-servers 192.168.1.1, 192.168.2.1;

##########################################################
#
# DHCP SERVER CONFIGURATION SETTINGS 
#

# assign the defaul lease time (seconds)
default-lease-time 600000000;

# assign the max lease time (seconds)
max-lease-time 720000000;

# eth0 subnet configuration
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.2 192.168.1.99;
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
}

# eth1 subnet configuration
subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.2 192.168.2.99;
  option routers 192.168.2.1;
  option broadcast-address 192.168.2.255;
}

##########################################################
# end config

```

Now to modify the **/etc/default/dhcp3-server** file to include eth1 at the bottom...

**dhcp3-server**
```

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests? 
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0 eth1"

```

Now restart the DHCP server by typing ' sudo /etc/init.d/dhcp3-server restart '

After that try resolving an IP with the connecting PC's (remember to use crossover cables when connecting). If you got IP's on both of the subnetted PC's great, thats a big step. If not, go back and check that your configs match your current set-up. Use the 'ifconfig' command to check if you are using the right IP addresses.

Once you've got it working your ready to now setup DNS. DNS is a snap, all you should need to do is type, 'sudo apt-get install bind9'. Boom you have a small DNS server on you box! This is so computers connecting to your router will be able to resolve web addresses based on their URL instead of their IP. For example...

instead of typing traceroute 216.239.37.147 you can type traceroute [www.google.com](www.google.com) and still gain the same functionality! (You won't be able to do that quite yet since the connecting PC's don't have internet access, yet).

Now there is just one more thing needed, and thats a script enabling IP Masquerade. I was able to figure this out by consulting.... (by the way I highly recommended reading over their site, it's very comprehensive and was a key part in me figuring out how to get this to work).

[http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/)

by slightly modifying their example script I came up with this...

**masqueradescript.sh**
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
#
#
#
# Log:
#       0.76 - Added comments on why the default policy is ACCEPT
#       0.75 - Added more kernel modules to the comments section 
#       0.74 - the ruleset now uses modprobe vs. insmod
#       0.73 - REJECT is not a legal policy yet; back to DROP
#       0.72 - Changed the default block behavior to REJECT not DROP
#       0.71 - Added clarification that PPPoE users need to use 
#              "ppp0" instead of "eth0" for their external interface
#       0.70 - Added commented option for IRC nat module
#            - Added additional use of environment variables
#            - Added additional formatting 
#       0.63 - Added support for the IRC IPTABLES module
#       0.62 - Fixed a typo on the MASQ enable line that used eth0
#              instead of $EXTIF
#       0.61 - Changed the firewall to use variables for the internal 
#              and external interfaces.
#       0.60 - 0.50 had a mistake where the ruleset had a rule to DROP
#              all forwarded packets but it didn't have a rule to ACCEPT
#              any packets to be forwarded either
#            - Load the ip_nat_ftp and ip_conntrack_ftp modules by default
#       0.50 - Initial draft
#

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
EXTIF="eth2"
INTIF="eth1"
INTIF2="eth0"
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"
echo "   Internal Interface:  $INTIF2" 

EXTIP="your external IP address"
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
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT 
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

Notice the top, you will have to set the external IP address to whatever it is for this to work. In this example it's eth2's IP. I realize that this is quite a long script but I left the comments in there because they explain what's going on in the script (remember the point of this is to learn).
Now run the shell script, 'sh scriptname' and your connecting PCs should have Internet access! If not, check out the script and see if everything is configured appropriately (particularly the path to Iptables). Consult

[http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/)

for further troubleshooting techniques.

Now assuming that everything is in order and working properly, we want to make our new script bootable so we don't have to run the script every time we restart.

Type: cp 'scriptname' /etc/init.d/'scriptname'

This copies the script to the init.d directory where other scripts are run at bootup. Now that that is out of the way, we need to make a symbolic link in the rc2.d directory pointing to the script we stored in the init.d directory.

Type: ln -s /etc/init.d/'scriptname' /etc/rc2.d/S95masquradescript

Presto, restart your computer and test to see if you still have the same functionality. If so then congratulations! If not then make sure you followed the above correctly so the script is bootable.

Additional thanks to the webmasters of the URLs mentioned in this tutorial. Each site was a great aid. I hope this tutorial was an aid in you understanding linux and networking.

Take Care!

---

### Post by Ophiocus on 2006-04-27
Excelent stuff! Got me up and running in >10 minuntes.

one little adition;

taken from [http://www.aboutdebian.com/proxy.htm](http://www.aboutdebian.com/proxy.htm)

you could set

      EXTIP="`/sbin/ifconfig eth0 | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`"

where eth0 is the external NIC to get the most up to date ip assigned by the ISP (this is in the case that like mine, your ISP has a knack for regularly changing your asigned dynamic IP), it also makes the box kinda hot plugable.

---

### Post by auburn on 2006-08-18
It worked for me too. Thank you so much for all the work.

---

### Post by todw1fd on 2006-08-20
To fit your own example, shouldn't that first eth2 be eth0?

> Our Linux Box with Ubuntu Linux (connected to switch as well)
(3 NICs)
L [COLOR="Red"]eth2[/COLOR] (192.168.0.103) via DHCP from Router above.
L eth1 (192.168.1.1 ) Statically assigned --------- Connecting PC
L eth2 (192.168.2.1) Statically assigned --------- Connecting PC


And then again in the masquerade script...where eth2 and eth0 are switched

> EXTIF="[COLOR="Red"]eth2[/COLOR]"
INTIF="eth1"
INTIF2="[COLOR="Red"]eth0[/COLOR]"
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"
echo "   Internal Interface:  $INTIF2" 

EXTIP="your external IP address"

Thanks!  This was just what I was looking for.

---

### Post by willneedshelp... on 2006-09-01
ok well u seem like u know what is going on ... i dont im a noob... ok i have an eth0 and an ath0 and im trying to run the wireless connection from my ath0 to my eth0 to connect it to my ps2 i have the special "switch cable" or whatever but im afraid it doesnt work all the way...all the time...i use firestarter and it all seems to work great ...sometimes see the connection works all the way my ps2 can connect the the internet but DNS fails..it gets to where i can get in the lobby but when i try to view the list of games or join a game it says an error occured ...so it seems that its unstable or something...it gets so close like i can chat and all that but im almost sure its somehting with the DNS cause thats the step it messes up on most of the time.  Sometimes sonys DNAS fails but i dont think thats related... when i try to get into a game it gives me an error of something with the DNS .  my brother told me i needed to ask about masq and get something...i dont know what to get i tried searching in synaptic but i dont really know what to install or really how to use it...i would really appriciate some help.  i am not sure what DHCP or DNS or even Masq really is...thanks

---

### Post by basketcase39 on 2006-09-01
What would it take to make this a more secure solution for a business environment?

---

### Post by Garyu on 2006-09-02
How about a HowTo for setting up Ubuntu as a router for IPv6?

I want to use regular IP (v4?) on the internet side and use IPv6 in my home LAN. But it is really difficult to find info on how to set that up.

---

### Post by mips on 2006-10-01
The last time Ellias posted here was in Jan. Dunno if he still visits here.

---

### Post by mips on 2006-10-01
> **todw1fd said:**
> To fit your own example, shouldn't that first eth2 be eth0?



And then again in the masquerade script...where eth2 and eth0 are switched



Thanks!  This was just what I was looking for.

Does not really matter, it's just a number.

---

### Post by mips on 2006-10-01
> **basketcase39 said:**
> What would it take to make this a more secure solution for a business environment?

I would look at a minimal OpenBSD install and look at hardening the box. The firewall in openbsd is also slightly different. If I was you I would do some googling.

---

### Post by mips on 2006-10-01
> **Garyu said:**
> How about a HowTo for setting up Ubuntu as a router for IPv6?

I want to use regular IP (v4?) on the internet side and use IPv6 in my home LAN. But it is really difficult to find info on how to set that up.


Google for: Debian IPv6 router

That should provide you with some pointers/guides.

Why IPv6 ? Is there any of it's features you require.

---

### Post by anewbieuser on 2006-12-26
hi, first of all, thanks for providing a post on help to setup a router. 
I was trying to follow through the steps and but I couldn't get my network nor the ICS work. I am new to Linux, therefore, I would really appreciate it if anyone can help me out, since I have been trying to set it up for quite a long time.

First or all, I have installed Xubuntu 6.10Desktop on a PII-333 Machines. I got three network cards. eth0, eth1 and eth2. eth0 connects to an ADSL directly. I can use the Internet no problem.

I started to follow the guide by assigning IP statically to eth1 and eth2, the code I used were:

```

$ sudo ifconfig eth1 192.168.1.1
$ sudo ifconfig eth2 192.168.2.1

```

then I found that I didn't have the dhcp3-server, so I downloaded it 

```

$ sudo apt-get install dhcp3-server

```

After that I went ahead and edited the **dhcpd.conf**, and this is the content of the file:


```

# Configuration file for ISC dhcpd (see 'man dhcpd.conf')
#
# For more information regarding the ISC DHCP Daemon,
# please visit: http://www.isc.org/sw/dhcp/
#
##########################################################
#
# Configuration Notes:
#
# This configuration file assumes that you
# have a total of 4 NIC cards installed on your system,
# with eth2 connecting (as a client) to a remote dhcp server. 
#
# This will assign a dhcp subnet to each additional NIC card
# (eth1, eth0), which can be used to create a
# multi-subnet DHCP Server.
#
# Example by: Sean O'Donnell http://code.seanodonnell.com
#
##########################################################
#
# DHCP CLIENT CONFIGURATION SETTINGS
#

# use ad-hoc style name server updating procedures
#ddns-update-style ad-hoc; 

# this may be required for some network configurations,
# but seems to work fine without it on my LAN.
#option domain-name "my-dhcp-server.com";

#assign the remote dhcp server hostname/ip addresses 
#option domain-name-servers 192.168.1.1, 192.168.2.1;

##########################################################
#
# DHCP SERVER CONFIGURATION SETTINGS 
#

# assign the defaul lease time (seconds)
default-lease-time 600000000;

# assign the max lease time (seconds)
max-lease-time 720000000;

# eth1 subnet configuration
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.2 192.168.1.99;
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
}

# eth2 subnet configuration
subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.2 192.168.2.99;
  option routers 192.168.2.1;
  option broadcast-address 192.168.2.255;
}

##########################################################
# end config

```

I took out the lines under the section DHCP CLIENT CONFIGURATION SETTINGS, because I was thinking that I am setting up a DHCP server, so I shouldn't be requiring that client configuration part. 

With that set up, then I edited that **dhcp3-server**  as instructed:


```

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1 eth2"

```

then I restarted the DHCP server by typing ' sudo /etc/init.d/dhcp3-server restart '
on my other two machines (winXP) that connects to eth1 and eth2, I set them to get IP automatically. 

I got IP assigned to both of the PC, but when I tried to PING the IP of one of the WinXP machine on the other WinXP machine, there is not response. But on the Xubuntu Machine I can ping both of them. I am wondering if that's correct, since I think the three machines are in the same Sub Mask and each of them should be able to Ping each other. By the way, I have turned of the fire wall on the XP machines. 

Even though I was not sure if that was totally correct I moved on the download the bind9 and started it by using the command:

```

$ sudo /etc/init.d/bind9

```

And then I went back to the XP machine and repaired the network, but that didn't provide a DNS address for them, once again I am wondering if that's correct.

I then moved on again to write the script for iptables with the code as provided. 

I named the script **IPsteps3.sh**

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
#
#
#
# Log:
#       0.76 - Added comments on why the default policy is ACCEPT
#       0.75 - Added more kernel modules to the comments section 
#       0.74 - the ruleset now uses modprobe vs. insmod
#       0.73 - REJECT is not a legal policy yet; back to DROP
#       0.72 - Changed the default block behavior to REJECT not DROP
#       0.71 - Added clarification that PPPoE users need to use 
#              "ppp0" instead of "eth0" for their external interface
#       0.70 - Added commented option for IRC nat module
#            - Added additional use of environment variables
#            - Added additional formatting 
#       0.63 - Added support for the IRC IPTABLES module
#       0.62 - Fixed a typo on the MASQ enable line that used eth0
#              instead of $EXTIF
#       0.61 - Changed the firewall to use variables for the internal 
#              and external interfaces.
#       0.60 - 0.50 had a mistake where the ruleset had a rule to DROP
#              all forwarded packets but it didn't have a rule to ACCEPT
#              any packets to be forwarded either
#            - Load the ip_nat_ftp and ip_conntrack_ftp modules by default
#       0.50 - Initial draft
#

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

EXTIP="`/sbin/ifconfig eth0 | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`"
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
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT 
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

and then I excecuted it:

```

$ sudo IPstep3.sh

```

I then check the whether the IP is allowed to be forwarded:

```

cat /proc/sys/net/ipv4/ip_forward

```

and I got the value  1

Then I made sure that the internet is working normally on the Xubuntu machine before I check the XPs.
but unfortunately, it didn't work on the XP machines. Now I am wondering where did it went wrong. I would really appreciate it if anyone me some suggestion.

---

### Post by mips on 2006-12-27
1. Please post output of **ifconfig -a**  (Depends on your interface number)
2. Please post output of **route -n**
3. Please post output of **cat /etc/resolv.conf**
4. Please post output of [B]cat /etc/network/interfaces
[/B]5. Please post output of a few **traceroute** between hosts or hosts & router.

---

### Post by anewbieuser on 2006-12-28
Hi mips,

Thanks very much for your reply and attention.

I have went through the process again and here are the output of the commands(ounce again, please note that eth0 connects to the internet and eth1 and eth2 are the interfaces for LAN):



**ifconfig:**

eth0      Link encap:Ethernet  HWaddr 00:50:FC:84:C4:F0  
          inet addr:XXX.XXX.XXX.XXX  Bcast:206.116.223.255  Mask:255.255.224.0
          inet6 addr: fe80::250:fcff:fe84:c4f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6722 errors:0 dropped:0 overruns:0 carrier:0
          collisions:5 txqueuelen:1000 
          RX bytes:5768411 (5.5 MiB)  TX bytes:1480132 (1.4 MiB)
          Interrupt:10 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:50:BA:5B:CC:37  
          inet addr:192.168.1.98  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fe5b:cc37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:906 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:94869 (92.6 KiB)  TX bytes:152022 (148.4 KiB)
          Interrupt:9 

eth2      Link encap:Ethernet  HWaddr 00:50:BF:78:B0:FB  
          inet addr:192.168.2.99  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:fe78:b0fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33444 (32.6 KiB)  TX bytes:21182 (20.6 KiB)
          Interrupt:10 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:383 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35796 (34.9 KiB)  TX bytes:35796 (34.9 KiB)

Please note I didn't show the IP address assigned by DHCP from my ISP.

**route -n:**

Kernel IP routing table
Destination           Gateway                    Genmask           Flags Metric Ref    Use Iface
192.168.2.0           0.0.0.0                      255.255.255.0     U          0      0        0 eth2
192.168.1.0           0.0.0.0                      255.255.255.0     U          0      0        0 eth1
206.116.192.0      0.0.0.0                      255.255.224.0     U          0      0        0 eth0
0.0.0.0                    192.168.2.1             0.0.0.0                 UG         0      0        0 eth2
0.0.0.0                    192.168.1.1             0.0.0.0                 UG         0      0        0 eth1
0.0.0.0                    206.116.192.254    0.0.0.0                 UG         0      0        0 eth0

**cat /etc/resolv.conf:**

search bc.hsia.telus.net
nameserver 154.11.128.59
nameserver 154.11.128.187

Above addresses are from my ISP

**cat /etc/network/interfaces:**

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 198.162.0.1
netmask 255.255.255.0

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

**traceroute 192.168.2.2(client on eth2):**

traceroute to 192.168.2.2 (192.168.2.2), 30 hops max, 40 byte packets
 1  192.168.2.2 (192.168.2.2)  3.365 ms  4.882 ms  1.551 ms
[B]
traceroute 192.168.1.2(client on eth1):[/B]

traceroute to 192.168.1.2 (192.168.1.2), 30 hops max, 40 byte packets
 1  192.168.1.2 (192.168.1.2)  1.734 ms  0.490 ms  0.375 ms

**traceroute 192.168.1.98 (this should be the router on eth1):**

traceroute to 192.168.1.98 (192.168.1.98 ), 30 hops max, 40 byte packets
 1  192.168.1.98 (192.168.1.98 )  0.501 ms  0.274 ms  0.160 ms

**traceroute 192.168.2.99 (this should be the router on eth2):**

traceroute to 192.168.2.99 (192.168.2.99), 30 hops max, 40 byte packets
 1  192.168.2.99 (192.168.2.99)  0.491 ms  0.324 ms  0.160 ms

Hope these are the outputs that gonna be useful. I have also opened my network neighbourhood on my XP machines and can see the Xubuntu Server and the other clients are there, though I couldn't access them and share files, I guess that's another issue which I believe I can use SAMBA to due with. Looking at these outputs I also have a question. Looking at the network settings for the XP machines, I found that the default gateways and the DHCP servers were 192.168.1.1 and 192.168.2.1. Theses are different from the IP that show up for eth1 and eth2 when I run ifconfig. Is that normal? I have also tried to pings these two ips and there were not response, but 192.168.1.98 and 192.168.2.99 would have response. 

Once again, thanks for your help and time!

---

### Post by newpants2003 on 2007-01-01
good

---

### Post by sebbe1991 on 2007-01-01
> **anewbieuser said:**
> 
And then I went back to the XP machine and repaired the network, but that didn't provide a DNS address for them, once again I am wondering if that's correct.

You need to specify the dns servers in the dhcpd config 
```
option domain-name-servers 1.2.3.4;
```
replace 1.2.3.4 with the DNS IP. the dhcpd config

---

### Post by Bruckout22 on 2007-01-01
Hey Ima Noob here I understand wats goin on here but I got lost in the editing process am I to uncomment anything out of the dhcpd.conf file to active wat I want I have the same 3 nic setup jus want to kno how exactly do I edit the file because everything in this tutorial is Commented out Help please

---

### Post by anewbieuser on 2007-01-02
> **sebbe1991 said:**
> You need to specify the dns servers in the dhcpd config 
```
option domain-name-servers 1.2.3.4;
```
replace 1.2.3.4 with the DNS IP. the dhcpd config

Hi, first of all, HAPPY NEW YEAR!!! Thanks for your reply, however, I don't really know what should I put for the DNS IP, should it be something assigned by my ISP or are they they IP of eth1 and eth2? If it is so, I have tried that with Static IPs, but it didn't work.

What I did was that I assigned eth1 to be 192.168.1.1 and eth2 to be 192.168.2.1 and then I set the subnet mask and the DNS on the two XP machines to be these values, the network was working but ICS didn't work either. Please provide further info/instructions. Thanks!

---

### Post by sebbe1991 on 2007-01-02
> **anewbieuser said:**
> Hi, first of all, HAPPY NEW YEAR!!! Thanks for your reply, however, I don't really know what should I put for the DNS IP, should it be something assigned by my ISP or are they they IP of eth1 and eth2? If it is so, I have tried that with Static IPs, but it didn't work.

What I did was that I assigned eth1 to be 192.168.1.1 and eth2 to be 192.168.2.1 and then I set the subnet mask and the DNS on the two XP machines to be these values, the network was working but ICS didn't work either. Please provide further info/instructions. Thanks!

Enter the DNS from your ISP
If you have bind9 installed use 192.168.1.1, 192.168.2.1

---

### Post by anewbieuser on 2007-01-02
> **sebbe1991 said:**
> Enter the DNS from your ISP
If you have bind9 installed use 192.168.1.1, 192.168.2.1

I have added the line in, the DHCP server does resolve the above ips to the clients as DNS server, but the ICS is still not working... also, I have notice that the Default Gateway of the clients(the one that connected to eth1) is 192.168.1.1, but the IP of eth1 is actually 192.168.1.98, is that correct? Also, I am also running SAMBA to share files, does it affect ICS?

---

### Post by sebbe1991 on 2007-01-02
> **anewbieuser said:**
> I have added the line in, the DHCP server does resolve the above ips to the clients as DNS server, but the ICS is still not working... also, I have notice that the Default Gateway of the clients(the one that connected to eth1) is 192.168.1.1, but the IP of eth1 is actually 192.168.1.98, is that correct? Also, I am also running SAMBA to share files, does it affect ICS?

if eth1 has the ip 192.168.1.98 then the gateway ip should be set to 192.168.1.98 on the computer connected to eth1

in dhcpd conf
change ```
option routers 192.168.1.1;
```
to ```
option routers 192.168.1.98;
```
and ```
option routers 192.168.2.1;
```
to ```
option routers 192.168.2.99;
```

EDIT: And samba does not affect ICS

---

### Post by anewbieuser on 2007-01-02
Hi sebbe1991,
You reply really quickly! Thanks for the correction, I actually realized that too.. and since I only have two computers connecting the server, I decided to use static ip instead, at least to get it setup probably for now. Ideally, I guess it will be better to use the DHCP server approach, but for some reason I couldn't get it done, each time the ip assigned to eth1 and eth2 by DHCP might be different, and I was not sure how I can add the  coorect ip to the dhcpd config correctly for DNS. In addition, the way the DHCP server assign the ips to the two interfaces was kinda strange. For example, after I have assigned eth1 and eth2 statically, then when I ran dhcp3-server, it would change the ip for both interfaces, for e.g. to 192.168.1.98 but then on the XP machine, it would say the ip of the DHCP server is 192.168.1.1.

At this moment, I am actually using one of the clients to reply this thread, pretty exciting. I finnaly got both of the computers networked and with ICS running among the three computers. 

However, it seems to me that the outcome of the procedure I took to get it setup was not very consistant, maybe I should try restarting the server and try again. When I got it done this time, I had to assign the ip statically to eth1 and eth2, ran my script for changing iptables and then restarted bind9 and restarted SAMBA to get ICS and network files sharing all work. I am wondering if there is a way to run  these automatically whenever I restart the server. Can I add the following codes into the masqueradescript.sh
that was provided at the beginning of this thread so that it will assign the ips and restart bind9 automatically for me whenever I restart the server?:

Can I add this to the very beginning of the file?

```

$sudo ifconfig eth1 192.168.1.1
$sudo ifconfig eth2 192.168.2.1

```

and the at the end:

```

$sudo /etc/init.d/bind9 restart
$sudo /etc/init.d/samba restart

```

---

### Post by sebbe1991 on 2007-01-03
> **anewbieuser said:**
> 
Can I add this to the very beginning of the file?

```

$sudo ifconfig eth1 192.168.1.1
$sudo ifconfig eth2 192.168.2.1

```


Edit the /etc/network/interfaces file instead..
change ```

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp
```

to
```

auto eth1
iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0

auto eth2
iface eth2 inet static
address 192.168.2.1
netmask 255.255.255.0

```

---

### Post by showe1966 on 2007-01-03
Here is a really good explaination of dns:-

[http://www.howtoforge.com/traditional_dns_howto](http://www.howtoforge.com/traditional_dns_howto)

Have fun !!!

---

### Post by anewbieuser on 2007-01-03
Thanks for everyone's help here!
Yeah, I got the static IPs worked after restart, however I have followed the steps to copy my script to the init.d directory and created a symobolic link to it with the command provided on the first page. 

```

$ cp 'scriptname' /etc/init.d/'scriptname'

$ ln -s /etc/init.d/'scriptname' /etc/rc2.d/S95masquradescript

```

I confirmed that the files were there and the link worked, but when I reboot the computer and check ipforwarding with:

```

cat /proc/sys/net/ipv4/ip_forward

```

I got a value of 0 then I have to manually run the script again...

---

### Post by sebbe1991 on 2007-01-03
```
chmod +x /etc/init.d/'scriptname'
```

---

### Post by anewbieuser on 2007-01-04
Thanks sebbe1991, it worked!!! I am just curious what does that line means actually? Is it for telling the OS that it needs to run that script when it restart? 
I am not wondering if I should open another how to so that the missing steps can be mentioned for other newer users like me.

---

### Post by sebbe1991 on 2007-01-04
> **anewbieuser said:**
> Thanks sebbe1991, it worked!!! I am just curious what does that line means actually? Is it for telling the OS that it needs to run that script when it restart? 
I am not wondering if I should open another how to so that the missing steps can be mentioned for other newer users like me.

chmod change file access permissions
chmod +x "somefile" set the execute flag on "somefile"

for more info about chmod use ```
man chmod
```
man is an interface to the on-line reference manuals

---

### Post by ilbozo on 2007-01-05
Hi guys, i followed the guide obviously adapting to my necessities. I got an ubuntubox with 2 network cards and a notebook with windows XP.
I'll try to explain what i did.
First i modified my dhcpd.conf:

```

ddns-update-style ad-hoc; 
option domain-name "my-dhcp-server.com";
option domain-name-servers 192.18.0.1;
default-lease-time 600000000;
max-lease-time 720000000;
# eth1 subnet configuration
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.2 192.168.1.99;
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
}

```

Then my dhcp3-server:
```
INTERFACES="eth1"
```

And then i wrote the script: (i post only what i changed from ur script)
```
EXTIF="eth0"
INTIF="eth1"
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"

EXTIP="`/sbin/ifconfig eth0 | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`"
echo "   External IP:  $EXTIP"

```

Now, i need to change the last part of the file, what should i do?
Here's what i did. I just commented the lines mentioning INTIF2. Is it right?
```
echo "   FWD: Allow all connections OUT and only existing and related ones IN"
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT 
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
$IPTABLES -A FORWARD -j LOG
#$IPTABLES -A FORWARD -i $EXTIF -o $INTIF2 -m state --state ESTABLISHED,RELATED \-j ACCEPT
#$IPTABLES -A FORWARD -i $INTIF -o $INTIF2 -m state --state ESTABLISHED,RELATED \-j ACCEPT 
#$IPTABLES -A FORWARD -i $INTIF2 -o $INTIF -m state --state ESTABLISHED,RELATED \-j ACCEPT
#$IPTABLES -A FORWARD -i $INTIF2 -o $EXTIF -j ACCEPT
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP
```

---

### Post by christodoulos77 on 2007-01-06
hello there!

I followed up what you did but I have a small problem.
when I connect a second host on my network the network stack, unless i manually 
put the proxy ip : port on the browser

I also started a post 
[http://www.ubuntuforums.org/showthread.php?t=331180](http://www.ubuntuforums.org/showthread.php?t=331180)

i'm asking for some help

thanks

---

### Post by adhesive on 2007-08-09
thanks :D  


this helped me alot :D

i modified this example



ubuntu desktop, a mac book pro  and a connection 

working very good :D

---

### Post by dthai on 2007-08-30
Hi all, I got a problem when running the script: my command is vss@vss:~$ sudo sh /vss/masqueradescript.sh 

```

: not found/masqueradescript.sh: 4: 0.76
: not found/masqueradescript.sh: 38: 
-e 

Loading simple rc.firewall-iptables version ..

: not found/masqueradescript.sh: 40: 
: not found/masqueradescript.sh: 41: 
: not found/masqueradescript.sh: 57: 
: not found/masqueradescript.sh: 58: 
   External Interface:  eth2
   Internal Interface:  eth0
: not found/masqueradescript.sh: 84: 
   External IP:  your external IP address
: not found/masqueradescript.sh: 87: 
: not found/masqueradescript.sh: 90: 
: not found/masqueradescript.sh: 91: 
-en    loading modules: 
: not found/masqueradescript.sh: 93: 
  - Verifying that all kernel modules are ok
: not found/masqueradescript.sh: 97: /sbin/depmod
: not found/masqueradescript.sh: 98: 
: not found/masqueradescript.sh: 109: 
: not found/masqueradescript.sh: 116: 
----------------------------------------------------------------------
: not found/masqueradescript.sh: 118: 
-en ip_tables, 
: not found/masqueradescript.sh: 125: /sbin/modprobe
: not found/masqueradescript.sh: 126: 
: not found/masqueradescript.sh: 127: 
: not found/masqueradescript.sh: 130: 
: not found/masqueradescript.sh: 131: 
-en ip_conntrack,  
: not found/masqueradescript.sh: 144: /sbin/modprobe
: not found/masqueradescript.sh: 145: 
: not found/masqueradescript.sh: 146: 
-en ip_conntrack_ftp,  
: not found/masqueradescript.sh: 152: /sbin/modprobe
: not found/masqueradescript.sh: 153: 
: not found/masqueradescript.sh: 154: 
-en ip_conntrack_irc,  
: not found/masqueradescript.sh: 160: /sbin/modprobe
: not found/masqueradescript.sh: 161: 
: not found/masqueradescript.sh: 162: 
-en iptable_nat, 
: not found/masqueradescript.sh: 169: /sbin/modprobe
: not found/masqueradescript.sh: 170: 
: not found/masqueradescript.sh: 171: 
-en ip_nat_ftp, 
: not found/masqueradescript.sh: 178: /sbin/modprobe
: not found/masqueradescript.sh: 179: 
: not found/masqueradescript.sh: 180: 
: not found/masqueradescript.sh: 188: 
----------------------------------------------------------------------
: not found/masqueradescript.sh: 190: 
: not found/masqueradescript.sh: 237: 
-e    Done loading modules.

: not found/masqueradescript.sh: 239: 
: not found/masqueradescript.sh: 240: 
: not found/masqueradescript.sh: 241: 
   Enabling forwarding..
: Directory nonexistentcript.sh: 252: cannot create /proc/sys/net/ipv4/ip_forward
: not found/masqueradescript.sh: 253: 
: not found/masqueradescript.sh: 254: 
   Enabling DynamicAddr..
: not found/masqueradescript.sh: 263: 
: not found/masqueradescript.sh: 264: 
: not found/masqueradescript.sh: 279: 
: not found/masqueradescript.sh: 280: 
   Clearing any existing rules and setting default policy..
: not found/masqueradescript.sh: 293: /sbin/iptables
: not found/masqueradescript.sh: 294: /sbin/iptables
: not found/masqueradescript.sh: 295: /sbin/iptables
: not found/masqueradescript.sh: 296: /sbin/iptables
: not found/masqueradescript.sh: 297: /sbin/iptables
: not found/masqueradescript.sh: 298: /sbin/iptables
: not found/masqueradescript.sh: 299: /sbin/iptables
: not found/masqueradescript.sh: 300: 
   FWD: Allow all connections OUT and only existing and related ones IN
: not found/masqueradescript.sh: 302: /sbin/iptables
: not found/masqueradescript.sh: 303: /sbin/iptables
: not found/masqueradescript.sh: 304: /sbin/iptables
: not found/masqueradescript.sh: 305: /sbin/iptables
: not found/masqueradescript.sh: 306: /sbin/iptables
: not found/masqueradescript.sh: 307: /sbin/iptables
: not found/masqueradescript.sh: 308: /sbin/iptables
: not found/masqueradescript.sh: 309: /sbin/iptables
: not found/masqueradescript.sh: 310: 
: not found/masqueradescript.sh: 311: 
   Enabling SNAT (MASQUERADE) functionality on eth2
: not found/masqueradescript.sh: 313: /sbin/iptables
: not found/masqueradescript.sh: 314: 
-e 
rc.firewall-iptables v done.

```

One more thing, when I try to manually run all the command in the script, I got an error when running:

vss@vss :~$ sudo iptables -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP
Bad argument `SNAT'
Try `iptables -h' or 'iptables --help' for more information.

Please help me, any help would be greatly appreciate.

---

### Post by Andrew Borem on 2007-09-05
I am confused by this.

I am running a two port computer.  This is going to be put in place of a typical router.  I have 6.06 for what it's worth.  This is standing in-between a T1 router and a windows Server 03 network, so this doesn't need DHCP at all.

I am posting from this computer.  On my extif I am using eth0.  I have my static IP, gateway, and netmask assigned, and I have edited my resolve conf file to put in my ISP's DNS servers.  It works like a charm as long as I am only using eth0.  I can ping anything.

I have eth1 as my intif.  It's a 192.168.6.0/24 network.  (I have a windows Laptop on the otherside, and I can ping both of the linux cards, and I can resolve internet hosts, but when I try to ping it comes back as a destination host unreachable)

So if I do this:

ping [www.google.com](www.google.com) -I eth0

I can ping.  But I do this:

ping [www.google.com](www.google.com) -I eth1

it resolves the name to an IP, and comes back with a destination host unreachable error.  (It times out on my windows laptop.)

this leads me to believe that I have a NAT error.  I have followed the directions in this thread, and I have ran this script.  I just don't understand what I am missing.  Any help would be much appreciated.

---

### Post by mips on 2007-09-06
I cant look now, maybe later.

---

### Post by Andrew Borem on 2007-09-06
All right, I had run a different script mistakenly.  Everything is up and running for me now.

I do need a link to read up on how to set up port forwarding in my linux router.  I can't seem to find any applicable links.  I appreciate the help!

---

### Post by Yes on 2007-09-06
What exactly will this do?  I don't have much time, but if it might solve my sporadic internet connection, then I'll absolutely have to try this.

---

### Post by mips on 2007-09-06
> **Yes said:**
> What exactly will this do?  I don't have much time, but if it might solve my sporadic internet connection, then I'll absolutely have to try this.

It probably wont.

---

### Post by arrrghhh on 2007-10-02
so how do i do something like dmz hosting?  i want to pass all traffic thru to the device... it's a ps3 and is whining about a 'type-3' nat... ports aren't forwarded properly.

---

### Post by airtonix on 2007-10-02
Im confused...

How is this different from using firestarter to share a second network interface on the ubuntu-router?

doing so automatically sets up forwarding.

Thus it allows me to use the ubunt-linux-box as a router to which i confine my housemates connections to.

Providing me unbridled access to the internet. ;)

---

### Post by Ikith on 2007-10-15
A huge question about this. I want to attempt this but I have a question first. By setting this up does it make a web ui that is accessible by everyone or do people in the network have to come to me when they want something done. Also how would you go about port forwarding and setting up SNMP to monitor the network or does all of the above come in the package after its setup?

---

### Post by mips on 2007-10-15
> **Ikith said:**
> A huge question about this. I want to attempt this but I have a question first. By setting this up does it make a web ui that is accessible by everyone or do people in the network have to come to me when they want something done. Also how would you go about port forwarding and setting up SNMP to monitor the network or does all of the above come in the package after its setup?

No.

Look at [Webmin]("http://www.webmin.com/") & [Firewall Builder]("http://www.fwbuilder.org/") if you want a GUI.

There is lots of info out there on port forwarding & snmp.

---

### Post by Ikith on 2007-10-15
I also have a wireless care lying around is there a requirement for the wireless card to broadcast? And how do I set it up?

---

### Post by mips on 2007-10-16
> **Ikith said:**
> I also have a wireless care lying around is there a requirement for the wireless card to broadcast? And how do I set it up?

You will have to explain a bit more as I don't get what you are saying.

---

### Post by Ederico on 2008-02-19
Does this HOWTO work with Ubuntu 7.10?

---

### Post by bhavi on 2008-02-19
> **Ellias said:**
> HOWTO-Ubuntu internet router, Firewall,DHCP,DNS,NAT
By: Ellias, special thanks to Mips 
Original Thread: [http://ubuntuforums.org/showthread.php?t=89320](http://ubuntuforums.org/showthread.php?t=89320)

This tutorial will go over all the steps one must take in order to set-up routing on a Linux box. There are some minimum requirements you must have in order to follow this tutorial to its completion. First you need a PC with Linux on it, the examples I will be giving are based off the Ubuntu distribution, but my examples should work on most other Debian based distributions and only slight modifications are needed to get it to work with Red Hat, etc... Second, you need two NICs. In my examples I will be showing how to do this with three NICs, 1 external and 2 internal. You probably need two cross-over cables to connect from PC to PC and one straight-through to connect from PC to modem, router, or switch (that will be on your external NIC). I say probably because some more advanced NICs support automatic conversion between the two. Thirdly, you need a somewhat working knowledge of Linux and networking in general, I will be covering a wide range of networking topics that are necessary to gain router functionality. Now before we get our feet wet, disclaimer time...

I am not responsible for any damage done to your computers and/or network. By following the instructions in this document you agree to these terms and recognize that you are solely responsible for what you do while following the instructions. Furthermore, the scripts provided here should NOT be used for a production and/or business environment. They are not secure and further modification would be needed in order to make them so. These instructions are for home use, educational purposes only.

There, now here is the setup I will be referring to in this document.

Internet
|
L Router (192.168.0.1) ----- PC's connected to router
|
|
Switch (typical 4 port) ----- PC's connect to switch 
|
|
Our Linux Box with Ubuntu Linux (connected to switch as well)
(3 NICs)
L eth2 (192.168.0.103) via DHCP from Router above.
L eth1 (192.168.1.1 ) Statically assigned --------- Connecting PC
L eth2 (192.168.2.1) Statically assigned --------- Connecting PC

Do a quick ifconfig to verify you have the setup correct (subnet mask is 255.255.255.0).

Also, here are a few troubleshooting programs I recommend getting ahold of...
sudo apt-get install traceroute
sudo apt-get install build-essential (C compiler for ethereal)
sudo apt-get install ethereal

Ok, so you've got things setup and ready to go. Now you need a way for the PCs connecting to the Linux box to get an IP address. For this we can use the DHCP server that comes with Linux. If you don't already have this a simple 'sudo apt-get install dhcp3-server' should get it for you just fine.

Once this is done you're going to have to configure it. The base of this configuration file was taken from Sean O'Donnell [http://code.seanodonnell.com](http://code.seanodonnell.com), but modified to fit our configuration here.

So type.... **'vim /etc/dhcp3/dhcpd.conf'**
and put the following in there (numbers may need to be tweaked for your setup)

**dhcpd.conf**
```

# Configuration file for ISC dhcpd (see 'man dhcpd.conf')
#
# For more information regarding the ISC DHCP Daemon,
# please visit: http://www.isc.org/sw/dhcp/
#
##########################################################
#
# Configuration Notes:
#
# This configuration file assumes that you
# have a total of 4 NIC cards installed on your system,
# with eth2 connecting (as a client) to a remote dhcp server. 
#
# This will assign a dhcp subnet to each additional NIC card
# (eth1, eth0), which can be used to create a
# multi-subnet DHCP Server.
#
# Example by: Sean O'Donnell http://code.seanodonnell.com
#
##########################################################
#
# DHCP CLIENT CONFIGURATION SETTINGS
#

# use ad-hoc style name server updating procedures
ddns-update-style ad-hoc; 

# this may be required for some network configurations,
# but seems to work fine without it on my LAN.
option domain-name "my-dhcp-server.com";

#assign the remote dhcp server hostname/ip addresses 
option domain-name-servers 192.168.1.1, 192.168.2.1;

##########################################################
#
# DHCP SERVER CONFIGURATION SETTINGS 
#

# assign the defaul lease time (seconds)
default-lease-time 600000000;

# assign the max lease time (seconds)
max-lease-time 720000000;

# eth0 subnet configuration
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.2 192.168.1.99;
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
}

# eth1 subnet configuration
subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.2 192.168.2.99;
  option routers 192.168.2.1;
  option broadcast-address 192.168.2.255;
}

##########################################################
# end config

```

Now to modify the **/etc/default/dhcp3-server** file to include eth1 at the bottom...

**dhcp3-server**
```

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests? 
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0 eth1"

```

Now restart the DHCP server by typing ' sudo /etc/init.d/dhcp3-server restart '

After that try resolving an IP with the connecting PC's (remember to use crossover cables when connecting). If you got IP's on both of the subnetted PC's great, thats a big step. If not, go back and check that your configs match your current set-up. Use the 'ifconfig' command to check if you are using the right IP addresses.

Once you've got it working your ready to now setup DNS. DNS is a snap, all you should need to do is type, 'sudo apt-get install bind9'. Boom you have a small DNS server on you box! This is so computers connecting to your router will be able to resolve web addresses based on their URL instead of their IP. For example...

instead of typing traceroute 216.239.37.147 you can type traceroute [www.google.com](www.google.com) and still gain the same functionality! (You won't be able to do that quite yet since the connecting PC's don't have internet access, yet).

Now there is just one more thing needed, and thats a script enabling IP Masquerade. I was able to figure this out by consulting.... (by the way I highly recommended reading over their site, it's very comprehensive and was a key part in me figuring out how to get this to work).

[http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/)

by slightly modifying their example script I came up with this...

**masqueradescript.sh**
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
#
#
#
# Log:
#       0.76 - Added comments on why the default policy is ACCEPT
#       0.75 - Added more kernel modules to the comments section 
#       0.74 - the ruleset now uses modprobe vs. insmod
#       0.73 - REJECT is not a legal policy yet; back to DROP
#       0.72 - Changed the default block behavior to REJECT not DROP
#       0.71 - Added clarification that PPPoE users need to use 
#              "ppp0" instead of "eth0" for their external interface
#       0.70 - Added commented option for IRC nat module
#            - Added additional use of environment variables
#            - Added additional formatting 
#       0.63 - Added support for the IRC IPTABLES module
#       0.62 - Fixed a typo on the MASQ enable line that used eth0
#              instead of $EXTIF
#       0.61 - Changed the firewall to use variables for the internal 
#              and external interfaces.
#       0.60 - 0.50 had a mistake where the ruleset had a rule to DROP
#              all forwarded packets but it didn't have a rule to ACCEPT
#              any packets to be forwarded either
#            - Load the ip_nat_ftp and ip_conntrack_ftp modules by default
#       0.50 - Initial draft
#

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
EXTIF="eth2"
INTIF="eth1"
INTIF2="eth0"
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"
echo "   Internal Interface:  $INTIF2" 

EXTIP="your external IP address"
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
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT 
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

Notice the top, you will have to set the external IP address to whatever it is for this to work. In this example it's eth2's IP. I realize that this is quite a long script but I left the comments in there because they explain what's going on in the script (remember the point of this is to learn).
Now run the shell script, 'sh scriptname' and your connecting PCs should have Internet access! If not, check out the script and see if everything is configured appropriately (particularly the path to Iptables). Consult

[http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/)

for further troubleshooting techniques.

Now assuming that everything is in order and working properly, we want to make our new script bootable so we don't have to run the script every time we restart.

Type: cp 'scriptname' /etc/init.d/'scriptname'

This copies the script to the init.d directory where other scripts are run at bootup. Now that that is out of the way, we need to make a symbolic link in the rc2.d directory pointing to the script we stored in the init.d directory.

Type: ln -s /etc/init.d/'scriptname' /etc/rc2.d/S95masquradescript

Presto, restart your computer and test to see if you still have the same functionality. If so then congratulations! If not then make sure you followed the above correctly so the script is bootable.

Additional thanks to the webmasters of the URLs mentioned in this tutorial. Each site was a great aid. I hope this tutorial was an aid in you understanding linux and networking.

Take Care!

Excellent stuff very informative

---

### Post by Michaira Sakudas on 2008-10-27
Hello, 

I'm running a Ubuntu Server 8 and trying to configure the internet router. The thing is that I always get the next error message:
```
# sudo /etc/init.d/dhcp3-server restart
* Stopping DHCP server dhcpd3 [fail]
* Starting DHCP server dhpcd3 [fail] 
```

I'm using two nicks eht0 as the external and eth1 as the internal, I've modified the dhcpd.conf file to include only the eth1 interface

looks like this is the real problem, I have no idea why dhcp is failing, I'm installing it from apt-get

I know this is an old thread but any help will be thanked

M.S.

---

### Post by dvdljns on 2009-11-05
> **Michaira Sakudas said:**
> Hello, 

I'm running a Ubuntu Server 8 and trying to configure the internet router. The thing is that I always get the next error message:
```
# sudo /etc/init.d/dhcp3-server restart
* Stopping DHCP server dhcpd3 [fail]
* Starting DHCP server dhpcd3 [fail] 
```

I'm using two nicks eht0 as the external and eth1 as the internal, I've modified the dhcpd.conf file to include only the eth1 interface

looks like this is the real problem, I have no idea why dhcp is failing, I'm installing it from apt-get

I know this is an old thread but any help will be thanked

M.S.

ubuntu won't restart server doing sudo I had to do sudo -s then do the restart.):P

---

### Post by Garyu on 2009-11-05
> **dvdljns said:**
> ubuntu won't restart server doing sudo I had to do sudo -s then do the restart.):P

wow, ask a question and get a reply more than 1 year later. that should teach people that there is no use in bumping threads. :p

good of you to help tough. I just found it very funny.

---

### Post by Agarax on 2009-11-06
Sorry if this is really bad necroposting ....

Will this work with a wired card on one side and a wireless card on the other side to create a wireless network?

I really want to do this as my next Linux Frankenstein project but I cant run wires where I'm living at the moment.

---

### Post by tester100 on 2011-08-22
Hi guys

Here is my querie , probably because i am a total newbie i have several questions i will put them all here in one place.


1- My goal here is to use ubuntu 10.04 or newer version as a full router system, as i wish to replace my old router which is allways jamming and crashing, needles to say i can only open a maximum of 32ports on virtual servers and port triggering.
So my idea is to use a old P4 1.6GHZ machine with 2GB ddr2 as a full router machine with firewall, dhcp server, snmpt, QOS and all the other features that the common routers have, but eventually will take too much work load of a common router, not to mention if all active same time will just simply take ages to enter the router WEBinterface.

So first things first....

I have my Adsl+2 Modem running hooked up to my router, i wish instead to use it like this method below in Bridge mode direct from Modem to UBuntu pc router


Modem ADSL => Ubuntu Machine with Eth0 network card hooked up working as a router software = > Then on the same pc the second or Eth1 network card as an output, with cable that goes into port1 => from Switch hub with 24 Ports  = > Then the othe PC machines hooked up in the 24 Port Hub Switch.


So in a simple theory


Modem => Ubuntu router SO + 2 network cards Eth0 for input from modem , and Eth1 as output dhcp server to Hub Switch => And hub switch => workstations connected.


Is this possible ? any tutorials on how to achieve it, i´ve done some searching on the sites and i found this thread but not quite what i was looking for.

thxs 
tester100

---

### Post by confusedstingray on 2011-08-24
> **tester100 said:**
> Hi guys

Here is my querie , probably because i am a total newbie i have several questions i will put them all here in one place.


1- My goal here is to use ubuntu 10.04 or newer version as a full router system, as i wish to replace my old router which is allways jamming and crashing, needles to say i can only open a maximum of 32ports on virtual servers and port triggering.
So my idea is to use a old P4 1.6GHZ machine with 2GB ddr2 as a full router machine with firewall, dhcp server, snmpt, QOS and all the other features that the common routers have, but eventually will take too much work load of a common router, not to mention if all active same time will just simply take ages to enter the router WEBinterface.

So first things first....

I have my Adsl+2 Modem running hooked up to my router, i wish instead to use it like this method below in Bridge mode direct from Modem to UBuntu pc router


Modem ADSL => Ubuntu Machine with Eth0 network card hooked up working as a router software = > Then on the same pc the second or Eth1 network card as an output, with cable that goes into port1 => from Switch hub with 24 Ports  = > Then the othe PC machines hooked up in the 24 Port Hub Switch.


So in a simple theory


Modem => Ubuntu router SO + 2 network cards Eth0 for input from modem , and Eth1 as output dhcp server to Hub Switch => And hub switch => workstations connected.


Is this possible ? any tutorials on how to achieve it, i´ve done some searching on the sites and i found this thread but not quite what i was looking for.

thxs 
tester100
this tutorial will help you, but look at distrowatch.com there is some packaged setups that will make a easy setup, i use pfsense, tried doing it with setting up each service got alot complicated for what i was trying to setup. have kids and wanted to lock them down, preventing badsites. also check out howtoforge.net

---

### Post by x684867 on 2012-07-07
Here's a modified version of the script presented....

#!/bin/bash

#!/bin/sh
#
#firewall-iptables
FWVER= 0.77
#
#               Initial SIMPLE IP Masquerade test for 2.6 / 2.4 kernels
#               using IPTABLES.
#
#               Once IP Masquerading has been tested, with this simple
#               ruleset, it is highly recommended to use a stronger
#               IPTABLES ruleset either given later in this HOWTO or
#               from another reputable resource.
#
#
#
# Log:
#		0.77 - Added a line to automatically detect EXTIP and removed 2nd LAN IF
#       0.76 - Added comments on why the default policy is ACCEPT
#       0.75 - Added more kernel modules to the comments section 
#       0.74 - the ruleset now uses modprobe vs. insmod
#       0.73 - REJECT is not a legal policy yet; back to DROP
#       0.72 - Changed the default block behavior to REJECT not DROP
#       0.71 - Added clarification that PPPoE users need to use 
#              "ppp0" instead of "eth0" for their external interface
#       0.70 - Added commented option for IRC nat module
#            - Added additional use of environment variables
#            - Added additional formatting 
#       0.63 - Added support for the IRC IPTABLES module
#       0.62 - Fixed a typo on the MASQ enable line that used eth0
#              instead of $EXTIF
#       0.61 - Changed the firewall to use variables for the internal 
#              and external interfaces.
#       0.60 - 0.50 had a mistake where the ruleset had a rule to DROP
#              all forwarded packets but it didn't have a rule to ACCEPT
#              any packets to be forwarded either
#            - Load the ip_nat_ftp and ip_conntrack_ftp modules by default
#       0.50 - Initial draft
#

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
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"

EXTIP=$(ifconfig $EXTIF | egrep -o inet\ addr\:[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\} | tr -d inet\ addr\:)
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
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT 
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
$IPTABLES -A FORWARD -j LOG
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP


echo "   Enabling SNAT (MASQUERADE) functionality on $EXTIF"
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

echo -e "\nrc.firewall-iptables v$FWVER done.\n"

---

### Post by griffinmt on 2012-10-16
I am following these instructions on ubuntu 12.04 and plan on running MAAS with a downstream server on the path along eth1 (bridged).
I build the command file (firewall-iptables.sh) and moved it to /etc/init.d/ and set the executable flag.
When I run it manually, it seems to work as expected. Then I added a link to it in /etc/rc2.d/ but when I reboot the system, there are no signs of it running and nothing in syslog that might explain it.
So, obviously I have forgotten to do something right :mad: :confused:

---

