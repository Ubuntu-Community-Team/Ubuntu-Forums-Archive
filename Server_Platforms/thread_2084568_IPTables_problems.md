---
title: "IPTables problems"
date: 2012-11-15
forum: Server Platforms
---

### Post by Di0g0 on 2012-11-15
Hi

I'm having some problems with my VPS running Ubuntu Server 11.04 x64. 

First I can't use sudo apt-get update, because my ubuntu can't connect to the repositories (iptables is blocking).

And I can't put my TS3 online, because of a DNS related problem (Iptables blocking).

I'm using the follow rules:

```

INPUT DROP
FORWARD DROP
OUTPUT DROP


INPUT:


iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -p tcp --dport 7777 -j ACCEPT
iptables -A INPUT -p udp --dport 7777 -j ACCEPT
iptables -A INPUT -p tcp --dport 9987 -j ACCEPT
iptables -A INPUT -p udp --dport 9987 -j ACCEPT
iptables -A INPUT -p tcp --dport 10011 -j ACCEPT
iptables -A INPUT -p udp --dport 10011 -j ACCEPT
iptables -A INPUT -p tcp --dport 30033 -j ACCEPT
iptables -A INPUT -p udp --dport 30033 -j ACCEPT
iptables -A INPUT -p tcp --dport 25555 -j ACCEPT
iptables -A INPUT -p udp --dport 25555 -j ACCEPT
iptables -A INPUT -p tcp --dport 41144 -j ACCEPT
iptables -A INPUT -p udp --dport 2010 -j ACCEPT
iptables -A INPUT -p tcp --dport 2008 -j ACCEPT
iptables -A INPUT -p tcp -m tcp --sport 53 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -p udp -m udp --sport 53 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT

OUTPUT:


iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 7777 -j ACCEPT
iptables -A OUTPUT -p udp --sport 7777 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 9987 -j ACCEPT
iptables -A OUTPUT -p udp --sport 9987 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 10011 -j ACCEPT
iptables -A OUTPUT -p udp --sport 10011 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 30033 -j ACCEPT
iptables -A OUTPUT -p udp --sport 30033 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 25555 -j ACCEPT
iptables -A OUTPUT -p udp --sport 25555 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 41144 -j ACCEPT
iptables -A OUTPUT -p udp --sport 2010 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 2008 -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --sport 1024:65535 --dport 53 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p udp -m udp --sport 1024:65535 --dport 53 -m state --state NEW,ESTABLISHED -j ACCEPT
```

I only want the necessary ports accepting connectons, I think it's all there (Teamspeak3 ports).

I need all blocked, because before this rules my VPS was being constantly attacked and this can help a lot.

---

### Post by Doug S on 2012-11-15
Hi and welcome to Ubuntu forums.
 
Your iptables rule set is very odd.
There is no return path for an ESTABLSHED RELATED packet created via the OUTPUT chain. I also don't see an OUTPUT path for apt-get to work. 
 
I realize my reply is incomplete. I might came back later and add some.
 
I suggest some further reading about iptables.
Reference: [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)
There are many other good references.
 
Edit: how does your VPS get its IP address? Is it static? (There doesn't seem to be a path for DHCP stuff)

---

### Post by Di0g0 on 2012-11-15
Hi

First I want to thank you for your post.

My VPS have a static IP address. I know that this rules are a sh... But I'm new to the IPTables world, and I searched and searched before make this topic.

Right now I have my VPS with all traffic allowed, but I want to block all the ports again to cut some attacks. I have something like 1Gbit/s bandwith but I'm receiving 100 mbit/s DDoS attacks and because of my IPTables configuration I'm getting DDoSed on all ports (all ports are accepting incoming, right now).

I made these rules to try to stop these attacks, and other type of attacks.

I'd be very grateful if you could help me.

Thanks!

---

### Post by Doug S on 2012-11-15
While odd, I don't understand why your dns lookups are not working.
Could you post the output from:```
sudo iptables -v -x -n -L
```

---

### Post by Di0g0 on 2012-11-15
```
Chain INPUT (policy ACCEPT 6654 packets, 288907 bytes)
    pkts      bytes target     prot opt in     out     source               dest                                                                             ination
    2106   168736 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp dpt:22
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp dpt:7777
 7561839 462969835 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0                                                                             .0/0           udp dpt:7777
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp dpt:9987
 1864794 190943096 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0                                                                             .0/0           udp dpt:9987
    1250    69948 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp dpt:10011
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp dpt:10011
     683    30948 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp dpt:30033
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp dpt:30033
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp dpt:25555
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp dpt:25555
    2699   136520 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp dpt:41144
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp dpt:2010
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp dpt:2008
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:53 dpts:1024:65535 state ESTABLISHED
      95     9480 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp spt:53 dpts:1024:65535 state ESTABLISHED
     772    65091 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               dest                                                                             ination

Chain OUTPUT (policy ACCEPT 12154 packets, 16819685 bytes)
    pkts      bytes target     prot opt in     out     source               dest                                                                             ination
    1849   282687 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:22
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:7777
11689161 1243583286 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.                                                                             0.0/0           udp spt:7777
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:9987
 4473440 524422603 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0                                                                             .0/0           udp spt:9987
     983   518929 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:10011
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp spt:10011
    1059   999059 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:30033
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp spt:30033
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:25555
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp spt:25555
    2699   107960 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:41144
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp spt:2010
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:2008
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spts:1024:65535 dpt:53 state NEW,ESTABLISHED
      96     6321 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp spts:1024:65535 dpt:53 state NEW,ESTABLISHED
    1604   253075 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0

Chain LOGGING (0 references)
    pkts      bytes target     prot opt in     out     source               dest                                                                             ination
    2474   193918 LOG        all  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           limit: avg 2/min burst 5 LOG flags 0 level 7 prefix `IPTables Pack                                                                             et Dropped: '
   41515  3291955 DROP       all  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0

```

7777 = SA:MP server running on my VPS
9987, 2008, 10011, 30033, 41144 = Teamspeak3
2555 = Minecraft Server


Maybe the problem here is:

I can't use apt-get update (can't connect), and ts3 is blocked somehere like that.

TS3 errors:

TS3ANetwork::ResolveHostName failed error: -3 (Temporary failure in name resolution) 11
TS3ANetwork::Connect failed error: 110

And I found this on the web:

"Hello

Check if the 2008 port is still open.
Check if you can ping accouting.teamspeak.com (on the linux system).

If you can't, it sound like a DNS problem (maybe after an update)"

--

I tested, and I can ping.....

---

### Post by Doug S on 2012-11-15
For Teamspeak3 you might want to study some and determine if all incoming ports need to be open, or if your server will actually create the connection via an outgoing packet to start with. I don't know.
 
Below is a quickly created suggestion at an iptables rule set. You will have to set the external IP address, as I have it set for one of my computers for testing. You might want to reduce the number of logging statements to reduce the sizes of your log files.
You need to read and fully understand the script before you try it. Modifications are proably required for your overall situation.```
#!/bin/sh
FWVER=0.01
#
# diogo_firewall 2011.11.15 Ver: 0.01 Attempt 1.
#       See Ubuntu forums post 12356849
#       Quick and dirty
#       diogo: you might want to reduce the logging.
echo "Loading diogo_firewall version $FWVER..\n"
# The location of the iptables program
#
IPTABLES=/sbin/iptables
#Setting the EXTERNAL and INTERNAL interfaces and addresses for the network
#
EXTIF="eth0"
# Temp set to Doug s15 computer. diogo set this right.
EXTIP="192.168.111.112"
UNIVERSE="0.0.0.0/0"
echo "   External Interface: $EXTIF   External IP: $EXTI"
#Clearing any previous configuration
#
echo "  Clearing any existing rules and setting default policy to DROP.."
# maybe default of ACCEPT will be used until sure things are working
$IPTABLES -P INPUT DROP
$IPTABLES -F INPUT
$IPTABLES -P OUTPUT DROP
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD
# Otherwise, I can not seem to delete it later on
$IPTABLES -F log-n-drop
# Delete user defined chains
$IPTABLES -X
# Reset all IPTABLES counters
$IPTABLES -Z
#######################################################################
# USER DEFINED CHAIN SUBROUTINES:
#
# log-n-drop
$IPTABLES -N log-n-drop
$IPTABLES -A log-n-drop -j LOG --log-prefix "GENERIC:" --log-level info
$IPTABLES -A log-n-drop -j DROP
#######################################################################
# INPUT: Incoming traffic from various interfaces.  All rulesets are
#        already flushed and set to a default policy of DROP.
#
# loopback interfaces are valid.
#
$IPTABLES -A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT
# Block specific jerks.
#
# http related
# for example. Put particular annoying IPs directly here:
#$IPTABLES -A INPUT -i $EXTIF -s 93.170.1.53 -j DROP
# A NEW TCP connection requires SYN bit set and FIN,RST,ACK reset.
$IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j LOG --log-prefix "NEW TCP no SYN:" --log-level info
$IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j DROP
# remote interface, RFC 1918, private internet packets, and some others.
# diogo: You might be more relaxed and delete this:
# this one must be removed for testing on Doug internel network:
#$IPTABLES -A INPUT -i $EXTIF -s 192.168.0.0/16 -d $UNIVERSE -j LOG --log-prefix "Sub192:" --log-level info
#$IPTABLES -A INPUT -i $EXTIF -s 192.168.0.0/16 -d $UNIVERSE -j DROP
$IPTABLES -A INPUT -i $EXTIF -s 10.0.0.0/8 -d $UNIVERSE -j LOG --log-prefix "Sub10:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -s 10.0.0.0/8 -d $UNIVERSE -j DROP
$IPTABLES -A INPUT -i $EXTIF -s 172.16.0.0/12 -d $UNIVERSE -j LOG --log-prefix "Sub172:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -s 172.16.0.0/12 -d $UNIVERSE -j DROP
$IPTABLES -A INPUT -i $EXTIF -s 240.0.0.0/5 -d $UNIVERSE -j LOG --log-prefix "Sub240:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -s 240.0.0.0/5 -d $UNIVERSE -j DROP
$IPTABLES -A INPUT -i $EXTIF -s 224.0.0.0/4 -d $UNIVERSE -j LOG --log-prefix "Sub224:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -s 224.0.0.0/4 -d $UNIVERSE -j DROP
$IPTABLES -A INPUT -i $EXTIF -s 169.254.0.0/16 -d $UNIVERSE -j LOG --log-prefix "Sub169:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -s 169.254.0.0/16 -d $UNIVERSE -j DROP
 
# external interface, from any source, for ICMP traffic is valid
#
$IPTABLES -A INPUT -i $EXTIF -p ICMP -s $UNIVERSE -d $EXTIP -j ACCEPT
# Allow any related traffic coming back to the server in.
#
#  STATEFULLY TRACKED
#
$IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state ESTABLISHED,RELATED -j ACCEPT
# ----- Begin OPTIONAL INPUT Section -----
# Secure Shell on port 22.
#
# Dynamic Badguy List. Detect and DROP Bad IPs that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT
# HTTPd - Enable the following lines if you run an EXTERNAL WWW server
#
#$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 80 -j LOG --log-prefix "NEW80:" --log-level info
#$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 80 -j ACCEPT
# E-mail on port 25. Enable the following lines if you run an EXTERNAL e-mail server.
#
#$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -m limit --limit 5/minute --limit-burst 3 -s $UNIVERSE -d $EXTIP --dport 25 -j ACCEPT
# SA:MP server
#
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p udp -s $UNIVERSE -d $EXTIP --dport 7777 -j ACCEPT
# Teamspeak3
#
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p udp -s $UNIVERSE -d $EXTIP --dport 9987 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 10011 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 30033 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 41144 -j ACCEPT
# Minecraft
# Is it 2555 or 25555??? UDP or TCP or both?
#
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p udp -s $UNIVERSE -d $EXTIP --dport 25555 -j ACCEPT
# Catch all rule, all other incoming is denied.
# (Leave the log-n-drop jump here so that in future I can remember how to do it.)
#
$IPTABLES -A INPUT -s $UNIVERSE -d $UNIVERSE -j log-n-drop
# ----- End OPTIONAL INPUT Section -----
#
echo Loading OUTPUT rulesets...
#######################################################################
# OUTPUT: Outgoing traffic from various interfaces.  All rulesets are
#         already flushed and set to a default policy of DROP.
#
# loopback interface is valid.
#
$IPTABLES -A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT
# anything else outgoing on remote interface is valid
#
$IPTABLES -A OUTPUT -o $EXTIF -s $EXTIP -d $UNIVERSE -j ACCEPT
# ----- Begin OPTIONAL OUTPUT Section -----
#
# Catch all rule, all other outgoing is denied.
$IPTABLES -A OUTPUT -s $UNIVERSE -d $UNIVERSE -j LOG --log-prefix "OCATCH:" --log-level info
$IPTABLES -A OUTPUT -s $UNIVERSE -d $UNIVERSE -j DROP
# ----- End OPTIONAL OUTPUT Section -----
#
#######################################################################
echo diogo_firewall $FWVER done.
```(note: cut and pasting took out some of my blank line formatting)

---

### Post by darkod on 2012-11-16
I am not an expert on iptables myself, but i would like to add my opinion:
1. Make the OUTPUT policy ACCEPT. The attacks are coming from outside the server so having an open OUTPUT policy is very little risk. In my humble opinion.

2. In addition to the ESTABLISHED connections being accepted by the INPUT chain, I would add RELATED too, and without limiting the ports. What ever established and related traffic originated from your server you should accept back. Exactly rules like this can stop programs working because the connection they are trying to establish is not accepted back by the INPUT chain. I would use something like:
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

If I'm not mistaken that accepts all traffic originating from your server so that all programs that need internet access can work correctly (this would include DNS requests and apt-get traffic).

---

### Post by Di0g0 on 2012-11-16
> **Doug S said:**
> For Teamspeak3 you might want to study some and determine if all incoming ports need to be open, or if your server will actually create the connection via an outgoing packet to start with. I don't know.
 
Below is a quickly created suggestion at an iptables rule set. You will have to set the external IP address, as I have it set for one of my computers for testing. You might want to reduce the number of logging statements to reduce the sizes of your log files.
You need to read and fully understand the script before you try it. Modifications are proably required for your overall situation.```
#!/bin/sh
FWVER=0.01
#
# diogo_firewall 2011.11.15 Ver: 0.01 Attempt 1.
#       See Ubuntu forums post 12356849
#       Quick and dirty
#       diogo: you might want to reduce the logging.
echo "Loading diogo_firewall version $FWVER..\n"
# The location of the iptables program
#
IPTABLES=/sbin/iptables
#Setting the EXTERNAL and INTERNAL interfaces and addresses for the network
#
EXTIF="eth0"
# Temp set to Doug s15 computer. diogo set this right.
EXTIP="192.168.111.112"
UNIVERSE="0.0.0.0/0"
echo "   External Interface: $EXTIF   External IP: $EXTI"
#Clearing any previous configuration
#
echo "  Clearing any existing rules and setting default policy to DROP.."
# maybe default of ACCEPT will be used until sure things are working
$IPTABLES -P INPUT DROP
$IPTABLES -F INPUT
$IPTABLES -P OUTPUT DROP
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD
# Otherwise, I can not seem to delete it later on
$IPTABLES -F log-n-drop
# Delete user defined chains
$IPTABLES -X
# Reset all IPTABLES counters
$IPTABLES -Z
#######################################################################
# USER DEFINED CHAIN SUBROUTINES:
#
# log-n-drop
$IPTABLES -N log-n-drop
$IPTABLES -A log-n-drop -j LOG --log-prefix "GENERIC:" --log-level info
$IPTABLES -A log-n-drop -j DROP
#######################################################################
# INPUT: Incoming traffic from various interfaces.  All rulesets are
#        already flushed and set to a default policy of DROP.
#
# loopback interfaces are valid.
#
$IPTABLES -A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT
# Block specific jerks.
#
# http related
# for example. Put particular annoying IPs directly here:
#$IPTABLES -A INPUT -i $EXTIF -s 93.170.1.53 -j DROP
# A NEW TCP connection requires SYN bit set and FIN,RST,ACK reset.
$IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j LOG --log-prefix "NEW TCP no SYN:" --log-level info
$IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j DROP
# remote interface, RFC 1918, private internet packets, and some others.
# diogo: You might be more relaxed and delete this:
# this one must be removed for testing on Doug internel network:
#$IPTABLES -A INPUT -i $EXTIF -s 192.168.0.0/16 -d $UNIVERSE -j LOG --log-prefix "Sub192:" --log-level info
#$IPTABLES -A INPUT -i $EXTIF -s 192.168.0.0/16 -d $UNIVERSE -j DROP
$IPTABLES -A INPUT -i $EXTIF -s 10.0.0.0/8 -d $UNIVERSE -j LOG --log-prefix "Sub10:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -s 10.0.0.0/8 -d $UNIVERSE -j DROP
$IPTABLES -A INPUT -i $EXTIF -s 172.16.0.0/12 -d $UNIVERSE -j LOG --log-prefix "Sub172:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -s 172.16.0.0/12 -d $UNIVERSE -j DROP
$IPTABLES -A INPUT -i $EXTIF -s 240.0.0.0/5 -d $UNIVERSE -j LOG --log-prefix "Sub240:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -s 240.0.0.0/5 -d $UNIVERSE -j DROP
$IPTABLES -A INPUT -i $EXTIF -s 224.0.0.0/4 -d $UNIVERSE -j LOG --log-prefix "Sub224:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -s 224.0.0.0/4 -d $UNIVERSE -j DROP
$IPTABLES -A INPUT -i $EXTIF -s 169.254.0.0/16 -d $UNIVERSE -j LOG --log-prefix "Sub169:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -s 169.254.0.0/16 -d $UNIVERSE -j DROP
 
# external interface, from any source, for ICMP traffic is valid
#
$IPTABLES -A INPUT -i $EXTIF -p ICMP -s $UNIVERSE -d $EXTIP -j ACCEPT
# Allow any related traffic coming back to the server in.
#
#  STATEFULLY TRACKED
#
$IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state ESTABLISHED,RELATED -j ACCEPT
# ----- Begin OPTIONAL INPUT Section -----
# Secure Shell on port 22.
#
# Dynamic Badguy List. Detect and DROP Bad IPs that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT
# HTTPd - Enable the following lines if you run an EXTERNAL WWW server
#
#$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 80 -j LOG --log-prefix "NEW80:" --log-level info
#$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 80 -j ACCEPT
# E-mail on port 25. Enable the following lines if you run an EXTERNAL e-mail server.
#
#$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -m limit --limit 5/minute --limit-burst 3 -s $UNIVERSE -d $EXTIP --dport 25 -j ACCEPT
# SA:MP server
#
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p udp -s $UNIVERSE -d $EXTIP --dport 7777 -j ACCEPT
# Teamspeak3
#
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p udp -s $UNIVERSE -d $EXTIP --dport 9987 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 10011 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 30033 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 41144 -j ACCEPT
# Minecraft
# Is it 2555 or 25555??? UDP or TCP or both?
#
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p udp -s $UNIVERSE -d $EXTIP --dport 25555 -j ACCEPT
# Catch all rule, all other incoming is denied.
# (Leave the log-n-drop jump here so that in future I can remember how to do it.)
#
$IPTABLES -A INPUT -s $UNIVERSE -d $UNIVERSE -j log-n-drop
# ----- End OPTIONAL INPUT Section -----
#
echo Loading OUTPUT rulesets...
#######################################################################
# OUTPUT: Outgoing traffic from various interfaces.  All rulesets are
#         already flushed and set to a default policy of DROP.
#
# loopback interface is valid.
#
$IPTABLES -A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT
# anything else outgoing on remote interface is valid
#
$IPTABLES -A OUTPUT -o $EXTIF -s $EXTIP -d $UNIVERSE -j ACCEPT
# ----- Begin OPTIONAL OUTPUT Section -----
#
# Catch all rule, all other outgoing is denied.
$IPTABLES -A OUTPUT -s $UNIVERSE -d $UNIVERSE -j LOG --log-prefix "OCATCH:" --log-level info
$IPTABLES -A OUTPUT -s $UNIVERSE -d $UNIVERSE -j DROP
# ----- End OPTIONAL OUTPUT Section -----
#
#######################################################################
echo diogo_firewall $FWVER done.
```(note: cut and pasting took out some of my blank line formatting)

I'll see it later and say something, but I have some questions:

Where i can put this script?
How to execute the script?

Thank you!

> **darkod said:**
> I am not an expert on iptables myself, but i would like to add my opinion:
1. Make the OUTPUT policy ACCEPT. The attacks are coming from outside the server so having an open OUTPUT policy is very little risk. In my humble opinion.

2. In addition to the ESTABLISHED connections being accepted by the INPUT chain, I would add RELATED too, and without limiting the ports. What ever established and related traffic originated from your server you should accept back. Exactly rules like this can stop programs working because the connection they are trying to establish is not accepted back by the INPUT chain. I would use something like:
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

If I'm not mistaken that accepts all traffic originating from your server so that all programs that need internet access can work correctly (this would include DNS requests and apt-get traffic).

I tried that and now I can use teamspeak 3 without problems, and apt-get. I don't know if that kind of rules are secure, but it's working.. But now I can easly portscan my server with NMap :x

Thanks!

---

### Post by darkod on 2012-11-16
When you say you can scan with nmap, do you mean the ports that you opened for the services, or all ports?

Because the ports that are opened for the services, to all the world, will be picked up by nmap, you can't run away from that as far as I know.

But other ports should be reported as filtered, iptables is blocking them.

You did leave the INPUT policy to DROP, right?

---

### Post by Di0g0 on 2012-11-16
> **darkod said:**
> When you say you can scan with nmap, do you mean the ports that you opened for the services, or all ports?

Because the ports that are opened for the services, to all the world, will be picked up by nmap, you can't run away from that as far as I know.

But other ports should be reported as filtered, iptables is blocking them.

You did leave the INPUT policy to DROP, right?

With the old rules I need to put -Pn on Nmap to sucessfully portscan. With this rules I can scan the Vps without -Pn.

Yes I have INPUT policy to DROP

---

### Post by darkod on 2012-11-16
That -Pn option means nothing, it only treats the host as online in case it can't detect it. It makes no difference whether the port will be reported as opened and closed. At least that's how I understand it from the nmap options.

You also asked about loading the rules at boot. Usually you would do it by create a text file, for example /etc/iptables.rules and then loading this file on boot by adding a command in /etc/network/interfaces.

For example, in the eth0 section (group of commands), you will add:
post-up iptables-restore < /etc/iptables.rules

That will flush the iptables and load the rules from the file specified immediately after the eth0 interface is brought online.

The /etc/iptables.rules file is little bit simpler than the script Doug posted, like:
```
*nat
<any rules you want for the nat chain
ignore this part if you don't need nat rules>
COMMIT

*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]

-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
...continue with all your other rules...
COMMIT
```

In the *filter section you first set the default policies, and then start adding rules. Don't forget to also add rules about ssh if you plan to manage the server over the network. In that case, especially if you are on the same internal network all the time, you can specify to let you in only from your private IP.

Lets say your desktop has the 192.168.1.100 address (you better make it static, not dynamic). Then it would be like:
-A INPUT -p tcp -s 192.168.1.100 --dport 22 -j ACCEPT

That will allow ssh only from your desktop, for additional security.

---

### Post by Doug S on 2012-11-16
You can put my file anywhere. You can execute it by setting it as executable and path/diogo_firewall . You can also automate on startup the same way darko showed above.
I could have done the script in the iptales-restore method, I just didn't.
 
It has the ESTABLISHED, RELATED stuff darko mentioned, for the reasons that darko mentioned.
 
I left OUTPUT default policy as DROP, as that is my own preference. If I covered everything properly, that default policy rule should actually never be hit.

---

### Post by Di0g0 on 2012-11-16
I'm receiving a DDoS attack right now!

With this rules (INPUT Drop, Forw Drop, Output accept) my servers are up and running but with 50% packet loss! (It's better than before I applied this rules).

Is there anyway to decrease the packet loss %?

Before this rules the servers went down...

Thanks.

---

### Post by darkod on 2012-11-16
Well, Doug is a better expert than me, but what do you refer to with "packet loss"?

If you are counting the packets dropped by iptables, then it's normal to drop the packets that shouldn't be allowed in. How big the number will be, depends on the amount of "good" and "bad" traffic.

In any case the ESTABLISHED,RELATED rule should be no problem since it only allows in traffic that originated from your server. If any attacks originate on the server, you have much bigger problems. If you have only "legitimate" traffic on the server, it's no problem to allow in the response to that traffic, right?

During attacks there will be a high number of packets dropped all the time, so don't worry about that number if that gets you worried.

---

### Post by Di0g0 on 2012-11-16
> **darkod said:**
> Well, Doug is a better expert than me, but what do you refer to with "packet loss"?

If you are counting the packets dropped by iptables, then it's normal to drop the packets that shouldn't be allowed in. How big the number will be, depends on the amount of "good" and "bad" traffic.

In any case the ESTABLISHED,RELATED rule should be no problem since it only allows in traffic that originated from your server. If any attacks originate on the server, you have much bigger problems. If you have only "legitimate" traffic on the server, it's no problem to allow in the response to that traffic, right?

During attacks there will be a high number of packets dropped all the time, so don't worry about that number if that gets you worried.

My problem is the bandwith. With packet loss I mean people breaking on teamspeak 3 beacause the server starts loosing packets, and the same happens on the samp server.

[IMG]http://i.imgur.com/uuxYy.png[/IMG]

When the attack reaches 100mbit/s the server starts failing, but when it's only 60mbit/s I have no problems !

Thanks.

---

### Post by Doug S on 2012-11-16
Sorry, I am not following, and I don't understand the two graphs above or what we are supposed to learn from looking at them.
Maybe we need to observe some traffic via a tcpdump capture to be sure bad guy packets are being dealt with in the most effiecient manor. It might be that some direct bad guy drops need to be inserted.
I don't know anything about Teamspeak or samp or minecraft. Is it possible your server is overloading? Do you observe with "top" at all?

---

### Post by Di0g0 on 2012-11-16
> **Doug S said:**
> Sorry, I am not following, and I don't understand the two graphs above or what we are supposed to learn from looking at them.
Maybe we need to observe some traffic via a tcpdump capture to be sure bad guy packets are being dealt with in the most effiecient manor. It might be that some direct bad guy drops need to be inserted.
I don't know anything about Teamspeak or samp or minecraft. Is it possible your server is overloading? Do you observe with "top" at all?

I can explain.

This simple rules helped keep the servers online, but with packet loss, people connected to my VPS starts loosing packets. I think this is happening because my VPS is with only 100mbit/s connection and the attacks are eating all the bandwith.

On the first printscreen you can see the attack. As you can see MDX-MultiGaming is my machine and the right side ip's with :domain in the end are servers attacking my VPS. And as you can see on the print screen they are attacking random ports on my VPS.

The second image shows the Incoming traffic (INPUT) created by this DDoS. 10M means 100mbit/s, when the attack reaches this peak (100mbit/s) all the servers starts failing, but when it's above 10M everything runs fine.

I'm sorry for my english, I don't speak english frequently so... 

Thanks :)

---

### Post by Doug S on 2012-11-16
Could you post a new output for the command from posting #4, so we can see the packet/byte counts for the various paths through iptables.
 
I think Darko explained well in posting #14, what should be occuring in terms of dropping the bad guy traffic.

---

### Post by Di0g0 on 2012-11-16
```
Chain INPUT (policy DROP 16957046 packets, 11531184145 bytes)
    pkts      bytes target     prot opt in     out     source               dest                                                                             ination
    4278   350991 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp dpt:22
      24     1108 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp dpt:7777
33645992 2846439092 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.                                                                             0.0/0           udp dpt:7777
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp dpt:9987
11857137 1150061110 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.                                                                             0.0/0           udp dpt:9987
   12069   675947 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp dpt:10011
     253   169695 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp dpt:10011
    6638   394542 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp dpt:30033
     367   338870 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp dpt:30033
       6      288 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp dpt:25555
     217   138508 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp dpt:25555
    3423   172672 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp dpt:41144
     261   174205 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp dpt:2010
      13      604 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp dpt:2008
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:53 dpts:1024:65535 state ESTABLISHED
    2147   244383 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp spt:53 dpts:1024:65535 state ESTABLISHED
   53285  4458057 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0
   73003 107941145 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0                                                                             .0/0           state RELATED,ESTABLISHED

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               dest                                                                             ination

Chain OUTPUT (policy ACCEPT 50491 packets, 2228699 bytes)
    pkts      bytes target     prot opt in     out     source               dest                                                                             ination
    3959   674028 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:22
      24      960 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:7777
47324442 5027877148 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.                                                                             0.0/0           udp spt:7777
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:9987
33748075 3654322644 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.                                                                             0.0/0           udp spt:9987
    9440  4781557 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:10011
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp spt:10011
    9734  8804487 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:30033
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp spt:30033
       6      240 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:25555
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp spt:25555
    3423   136920 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:41144
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp spt:2010
      13      520 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spt:2008
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           tcp spts:1024:65535 dpt:53 state NEW,ESTABLISHED
    2197   153192 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           udp spts:1024:65535 dpt:53 state NEW,ESTABLISHED
   10352  1369060 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0

Chain LOGGING (0 references)
    pkts      bytes target     prot opt in     out     source               dest                                                                             ination
    2474   193918 LOG        all  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0           limit: avg 2/min burst 5 LOG flags 0 level 7 prefix `IPTables Pack                                                                             et Dropped: '
   41515  3291955 DROP       all  --  *      *       0.0.0.0/0            0.0.0.                                                                             0/0

```

---

### Post by darkod on 2012-11-16
You have a lot of traffic on ports 7777 and 9987, not only INPUT but also OUTPUT.

I can't judge if this is all attacks. Are you sure you don't have very high legitimate traffic too?

---

### Post by Di0g0 on 2012-11-16
> **darkod said:**
> You have a lot of traffic on ports 7777 and 9987, not only INPUT but also OUTPUT.

I can't judge if this is all attacks. Are you sure you don't have very high legitimate traffic too?

The traffic on ports 7777 and 9987 are normal because 9987 = teamspeak 3 and 7777 = samp.

---

### Post by Di0g0 on 2012-11-16
And again... DDoS !! :(

---

### Post by Doug S on 2012-11-16
Yes, but I think the iptables rule set, such as it is, is doing the right thing. A great many Incoming packets are being dropped.
 
I see that your rule set is still somewhat of a mess and the counters have not been reset since yesterday (i.e. we have to subtract yesterday counts from today to know the packets since then).
 
If you want to try eliminate the incoming packets: First realize that you might not be able to; It will take a lot of work; You need to identify why they decide to pick on you in the first place; and so on... the plan would evolve based on results. 
 
For example, there are a lot of ICMP packets. Maybe capture and look at some as to what is going on.
 
I might be tempted to directly drop 62.180.0.0/16 and 80.86.146.222 and 95.172.28.178 and 72.0.47.58. Or Just watch them for awhile looking for clues. It is likely that the source ip for 62.180.x.y is forged, maybe others also.
Does the traffic from204.246.0.9 and 63.245.218.7 (ns2.mozilla.org) make sense to you?
 
And / or get help from your hosting site admins. This attack looks pretty harsh.
 
What are you running that creates the display you showed in your post # 13? I guess it captures packets much like tcpdump.

---

### Post by Di0g0 on 2012-11-16
> **Doug S said:**
> Yes, but I think the iptables rule set, such as it is, is doing the right thing. A great many Incoming packets are being dropped.
 
I see that your rule set is still somewhat of a mess and the counters have not been reset since yesterday (i.e. we have to subtract yesterday counts from today to know the packets since then).
 
If you want to try eliminate the incoming packets: First realize that you might not be able to; It will take a lot of work; You need to identify why they decide to pick on you in the first place; and so on... the plan would evolve based on results. 
 
For example, there are a lot of ICMP packets. Maybe capture and look at some as to what is going on.
 
I might be tempted to directly drop 62.180.0.0/16 and 80.86.146.222 and 95.172.28.178 and 72.0.47.58. Or Just watch them for awhile looking for clues. It is likely that the source ip for 62.180.x.y is forged, maybe others also.
Does the traffic from204.246.0.9 and 63.245.218.7 (ns2.mozilla.org) make sense to you?
 
And / or get help from your hosting site admins. This attack looks pretty harsh.
 
What are you running that creates the display you showed in your post # 13? I guess it captures packets much like tcpdump.

Iftop recommended by my VPS Host.

Thanks.

---

### Post by SeijiSensei on 2012-11-17
It sounds to me like you have a fundamental misunderstanding of what a firewall can do for you.  It cannot do anything about people flooding your IP with DDOS packets.  The firewall can ignore them, but the only one who can do something about the traffic itself is your ISP. If people are having problems staying connected because there's too much traffic being directed at your IP, having a firewall will not help with that.

I'm always amazed by the number of reports of people like you having DOS attacks run against them.  I've run public mail and web servers for years and never see much of this sort of activity.

---

### Post by Doug S on 2012-11-19
Diogo: Why did you remove that iftop screen shot from post #13?
Anyway, did you notice the very high traffic incoming from 168.143.82.104 port 50506 to port 7777, with no outgoing traffic on that screen shot? Didn't that seem a little odd?
 
Seiji is exactly right. The only reason I was suggesting perhaps continuing to investigate from your end was on the chance that the originating set of packets could be identified. If they were dropped, maybe the entire DDos attack might not start. I have succeeded with such an approach in the past, but it took a lot of work. (in my cases, the actual attack bandwidth was extremely low.)
 
For your earlier question, "How to minimize missing real packets": Since your computer gets saturated with packets, I think that all you can do is try to have the most effiecient and minimal iptables rules set possible. Among other things, that means looking up and knowing exactly what ports and for which protocol need to be open. For example for the sa-mp server only 7777 udp needs to be open, so don't bother with 7777 tcp as it adds time to the iptables rule set traversal. It might not make much difference overall, but with this in mind I re-wrote my earlier suggested rule set:```
#!/bin/sh
FWVER=0.02
#
# diogo_firewall 2011.11.18 Ver: 0.02
#       See Ubuntu forums post 12356849
#       Modify for maximum efficency, minimum time
#       to traverse the iptables rule set.
#       To help push out maximum bandwidth limit.
#
# diogo_firewall 2011.11.15 Ver: 0.01 Attempt 1.
#       See Ubuntu forums post 12356849
#       Quick and dirty
#       diogo: you might want to reduce the logging.
echo "Loading diogo_firewall version $FWVER..\n"
# The location of the iptables program
#
IPTABLES=/sbin/iptables
#Setting the EXTERNAL and INTERNAL interfaces and addresses for the network
#
EXTIF="eth0"
# Temp set to Doug s15 computer. diogo set this right.
EXTIP="192.168.111.112"
UNIVERSE="0.0.0.0/0"
echo "   External Interface: $EXTIF   External IP: $EXTI"
#Clearing any previous configuration
#
echo "  Clearing any existing rules and setting default policy to DROP.."
# maybe default of ACCEPT will be used until sure things are working
$IPTABLES -P INPUT DROP
$IPTABLES -F INPUT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD
# Delete user defined chains
$IPTABLES -X
# Reset all IPTABLES counters
$IPTABLES -Z
#######################################################################
# INPUT: Incoming traffic from various interfaces.  All rulesets are
#        already flushed and set to a default policy of DROP.
#
# loopback interfaces are valid.
#
$IPTABLES -A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT
# Block specific jerks.
#
# http related
# for example. Put particular annoying IPs directly here:
#$IPTABLES -A INPUT -i $EXTIF -s 93.170.1.53 -j DROP
# A NEW TCP connection requires SYN bit set and FIN,RST,ACK reset.
#$IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j LOG --log-prefix "NEW TCP no SYN:" --log-level info
$IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j DROP
# external interface, from any source, for ICMP traffic is valid
#
$IPTABLES -A INPUT -i $EXTIF -p ICMP -s $UNIVERSE -d $EXTIP -j ACCEPT
# Allow any related traffic coming back to the server in.
#
#  STATEFULLY TRACKED
#
$IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state ESTABLISHED,RELATED -j ACCEPT
# ----- Begin OPTIONAL INPUT Section -----
# SA-MP server
#
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p udp -s $UNIVERSE -d $EXTIP --dport 7777 -j ACCEPT
# Teamspeak3
#
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p udp -s $UNIVERSE -d $EXTIP --dport 9987 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 10011 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 30033 -j ACCEPT
# Minecraft
# Is it 2555 or 25555??? UDP or TCP or both?
# Web site says 25565 TCP (???)
#
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 25565 -j ACCEPT
# Secure Shell on port 22.
#
# Dynamic Badguy List. Detect and DROP Bad IPs that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT
# ----- End OPTIONAL INPUT Section -----
#
echo Loading OUTPUT rulesets...
#######################################################################
# OUTPUT: Outgoing traffic from various interfaces.  All rulesets are
#         already flushed and set to a default policy of DROP.
#
# Changed to default ACCEPT policy for maximum effiecency
# ----- End OPTIONAL OUTPUT Section -----
#
#######################################################################
echo diogo_firewall $FWVER done.

```Example sudo iptables -v -x -n -L output:```
doug@s15:~$ sudo iptables -v -x -n -L
[sudo] password for doug:
Chain INPUT (policy DROP 19921 packets, 1664560 bytes)
    pkts      bytes target     prot opt in     out     source               destination
     296    14800 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
       8     4744 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags:! 0x17/0x02 state NEW
       0        0 ACCEPT     icmp --  eth0   *       0.0.0.0/0            192.168.111.112
     922   124713 ACCEPT     all  --  eth0   *       0.0.0.0/0            192.168.111.112      state RELATED,ESTABLISHED
       0        0 ACCEPT     udp  --  eth0   *       0.0.0.0/0            192.168.111.112      state NEW udp dpt:7777
       0        0 ACCEPT     udp  --  eth0   *       0.0.0.0/0            192.168.111.112      state NEW udp dpt:9987
       0        0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            192.168.111.112      state NEW tcp dpt:10011
       0        0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            192.168.111.112      state NEW tcp dpt:30033
       0        0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            192.168.111.112      state NEW tcp dpt:25565
       0        0 LOG        all  --  eth0   *       0.0.0.0/0            0.0.0.0/0            recent: UPDATE seconds: 5400 hit_count: 3 name: BADGUY_SSH side: source LOG flags 0 level 6 prefix "SSH BAD:"
       0        0 DROP       all  --  eth0   *       0.0.0.0/0            0.0.0.0/0            recent: UPDATE seconds: 5400 hit_count: 3 name: BADGUY_SSH side: source
       2       92 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22 recent: SET name: BADGUY_SSH side: source
Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
Chain OUTPUT (policy ACCEPT 1771 packets, 469746 bytes)
    pkts      bytes target     prot opt in     out     source               destination
doug@s15:~$

```

---

