---
title: "iptables spesific rule"
date: 2017-02-12
forum: Server Platforms
---

### Post by secoonder on 2017-02-12
Hello
my firewall iptables+squid on ubuntu 14.04,i want to add one rule.my purpose is:

 [SIZE=3]_***5 seconds timeout when 500 connections are received from x.x.x.x ip address***_[/SIZE]

""iptables &#8211;A INPUT -s x.x.x.x &#8211;m limit &#8211;-limit 500/second &#8211;-limit-burst 1000 &#8211;j DROP""" rule is not my purpose.i tried it.

And  "iptables hit count" command is not my purpose too.

How can I write a rule? What can i do? 

Thank you very much for your help.

---

### Post by The Cog on 2017-02-12
I don't understand what you want the rule to do. Two questions come to mind:

500 connections received: Is that 500 concurrent connections, 500 connections per second, 500 connections since the server rebooted, or something else?

5 seconds timeout: What happens when the timeout expires?

---

### Post by secoonder on 2017-02-14
The Cog
Yes ,since the server is rebooted 500 connections per second.
second questions; The server is not tired.
How can I write a rule? is it possible timeout in iptables?
Thank you very much

---

### Post by Doug S on 2017-02-15
> **secoonder said:**
> The Cog
Yes ,since the server is rebooted 500 connections per second.
second questions; The server is not tired.
How can I write a rule? is it possible timeout in iptables?
Thank you very muchI still do not understand what you want. Please be clear.

---

### Post by secoonder on 2017-02-15
Hello Doug S
i want to rule  "**5 seconds timeout when 500 connections are received from x.x.x.x ip address" ** in iptables.
is it possible in iptables?

---

### Post by SeijiSensei on 2017-02-15
Is this a legitimate host you're trying to throttle, or a attacker?  If the latter, why not just block the IP address entirely?

---

### Post by secoonder on 2017-02-16
SeijiSensei
this is a legitimate host.
On the other hand, 
&#304; guess it is not "**5 seconds timeout when 500 connections are received from x.x.x.x ip address" ** in iptables.
is it true

---

### Post by Doug S on 2017-02-16
The best I can figure out is a 5 second timeout if there are 255 new connections from x.x.x.x in one second.
The 5 second timeout would reset for any connection attempt within that time.

Would that serve your requirement?

---

### Post by secoonder on 2017-02-16
Doug S
Absolutely yes

---

### Post by Doug S on 2017-02-16
While the following stands on it own, I assume you will have to somehow merge it into whatever existing iptables rule set you currently have.
I use this technique of a different trigger time (1 second in your case) and timeout time ( 5 seconds in your case) on my server, for port 80 stuff.
I tested this on one of my test computers, but with a 100 second trigger time and a 300 second timeout, because I don't have a way to test 1 second and 5 seconds.

```
#!/bin/sh
FWVER=0.01
#
# forum2352391 rule set. Smythies 2017.02.15 Ver:0.01
#       My best guess at what is wanted.
#
#       Requires a larger (100 X 255) than default (100 X 20)
#       xt_recent table size.
#       Note: 255 was chosen, becuase it is the maximum allowed.
#
#       See here:
#       https://ubuntuforums.org/showthread.php?t=2352391
#
#       run as sudo
#

echo "Loading forum2352391 rule set version $FWVER..\n"

# The location of the iptables program
#
IPTABLES=/sbin/iptables

#Setting the EXTERNAL and INTERNAL interfaces and addresses for the network
#
# Smythies (for testing)
EXTIF="enp9s0"
EXTIP="192.168.111.104"
# The IP address to keep track of. X.X.X.X in the forum post
#
MONIP="192.168.111.112"

UNIVERSE="0.0.0.0/0"

#Clearing any previous configuration
#
echo "  Clearing any existing rules and setting default policies.."
$IPTABLES -P INPUT ACCEPT
$IPTABLES -F INPUT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD ACCEPT
$IPTABLES -F FORWARD
$IPTABLES -F ip_ban
# Delete user defined chains
$IPTABLES -X
# Reset all IPTABLES counters
$IPTABLES -Z

# We want to force load the xt_recent module, so that we can
# override the default maximum table length. We want 255
# (the maximum) whereas the default is 20.
# I do not know the extra CPU burden of such a long table.
# Unload first, so that any new settings will actually work.
#(i.e. for times when different settings are being tried.)
#
modprobe -r xt_recent
modprobe xt_recent ip_pkt_list_tot=255

#######################################################################
# USER DEFINED CHAIN SUBROUTINES:
#
# ip_ban
#
# Excessive NEW Connections per second from MONIP have been detected.
#
# carry forward to the actual ban timeout:
# Increment this count.
# Probably don't need to remove the previous count, left as a comment.
#
# Custom tables must exist before being referenced, hence the order
# of these sub-routines.
#
$IPTABLES -N ip_ban
#$IPTABLES -A ip_ban -m recent --remove --name MON_IP
$IPTABLES -A ip_ban -j LOG --log-prefix "MONIP timeout:" --log-level info
$IPTABLES -A ip_ban -m recent --set --name LIM_IP
$IPTABLES -A ip_ban -j DROP

# loopback interfaces are valid.
#
$IPTABLES -A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT

# A NEW TCP connection requires SYN bit set and FIN,RST,ACK reset.
#
$IPTABLES -A INPUT -m limit --limit 1/s --limit-burst 2 -p tcp ! --syn -m state --state NEW -j LOG --log-prefix "NEW TCP no SYN:" --log-level info
$IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j REJECT

# Just DROP invalid packets.
#
$IPTABLES -A INPUT -i $EXTIF -m limit --limit 1/s --limit-burst 2 -p tcp -m state --state INVALID -j LOG --log-prefix "IINVALID:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -p tcp -m state --state INVALID -j DROP

# Allow any related traffic coming back to the server in.
#
$IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -m state --state ESTABLISHED,RELATED -j ACCEPT

# If MONIP is in a timeout, then DROP the packet.
# Only MONIP is on the list, so no need to check by ip address here.
#
$IPTABLES -A INPUT -i $EXTIF -m limit --limit 1/m --limit-burst 2 -m recent --update --hitcount 1 --seconds 5 --name LIM_IP --rsource -j LOG --log-prefix "IP-LIM:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 1 --seconds 5 --name LIM_IP --rsource -j DROP

# Check if MONIP needs to be put into a timeout
# Note that a NEW state check is not needed here, because it should be NEW anyhow.
#
$IPTABLES -A INPUT -i $EXTIF -s $MONIP -m recent --update --hitcount 255 --seconds 1 --name MON_IP -j ip_ban
$IPTABLES -A INPUT -i $EXTIF -s $MONIP -m recent --set --name MON_IP

# At this point carry on. You (secoonder) need to merge this into your existing iptables rule set.
#

echo forum2352391 rule set version $FWVER done.

```

EDIT: It turns out that my simple telnet loop test script does work fast enough to test the 1 second and 5 second settings. So, tested.
EDIT 2: I forgot that I had hping3 installed on the sending test computer, so I was actually able to test very precisely.

---

### Post by Doug S on 2017-03-03
So, did that help?

---

