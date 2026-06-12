---
title: "Need help to create Captive Portals using IPtables rules on Ubuntu"
date: 2010-08-11
forum: Server Platforms
---

### Post by hiprakhar on 2010-08-11
Hi,

I am using this thread to create a captive portal: [http://www.andybev.com/index.php/Using_iptables_and_PHP_to_create_a_captive_portal](http://www.andybev.com/index.php/Using_iptables_and_PHP_to_create_a_captive_portal)

I  am running Ubuntu using VMWare on win 7 in unity mode which is all  working cool, including networking. I have installed all packages to run  apache2, php5, mysql and phpmyadmin and also other packages as listed  in by andybev- (which are also working cool)

#  conntrack
#  sudo
# psmisc
# PHP
# squid

The flat file used to store  details of all registered users is /var/lib/users. Now I have to create  the iptables rules, where I am having problem. Andybev just says the  following iptables rules are required without elaborating "HOW TO CREATE  THESE RULES"

> [INDENT]Firewall rules  required

The following iptables rules are needed in your  firewall:

IPTABLES=/sbin/iptables

# Set the default policy  to drop all forwarded packets
$IPTABLES -P FORWARD DROP

#  Create internet chain
# This is used to authenticate users who have  already signed up
$IPTABLES -N internet -t nat


# Accept  all local traffic
$IPTABLES -t nat -A PREROUTING -i eth0  --destination 10.0.0.0/16 -j ACCEPT

# First send all traffic via  newly created internet chain
# At the prerouting NAT stage this will  DNAT them to the local
# webserver for them to signup if they aren't  authorised
# Packets for unauthorised users are marked for dropping  later
$IPTABLES -t nat -A PREROUTING -j internet


# Now  that we've got to the forward filter, drop all packets
# marked 99 -  these are unknown users. We can't drop them earlier
# as there's no  filter table
$IPTABLES -t filter -A FORWARD -m mark --mark 99 -j DROP

######  INTERNET CHAIN ##########
# Allow authorised clients in, redirect  all others to login webserver
# Add known users to the NAT table to  stop their dest being rewritten
# Ignore MAC address with a * - these  users are blocked
# This awk script goes through the /var/lib/users  flat file line by line
awk 'BEGIN { FS="\t"; } { system("$IPTABLES -t  nat -A internet -m mac --mac-source "$4" -j RETURN"); }' /var/lib/users

#  MAC address not found. Mark the packet 99
$IPTABLES -t nat -A  internet -j MARK --set-mark 99
# Redirects web requests from  Unauthorised users to logon Web Page
$IPTABLES -t nat -A internet -m  mark --mark 99 -p tcp --dport 80 -j DNAT --to-destination 10.0.0.1
################################


#  Enable Internet connection sharing
$IPTABLES -A FORWARD -i ppp0 -o  eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A  FORWARD -i eth0 -o ppp0 -j ACCEPT
$IPTABLES -t nat -A POSTROUTING -o  ppp0 -j MASQUERADE
[/INDENT]I am not able to apply these  rules. I tried to edit the iptables in /sbin/iptables but realised it is  an executable program. I tried running this program on terminal and  then execute each iptable rule as given by Andybev, line by line. But I  highly doubt if it was meant to be done that way.

Please shed  some light on iptables rules and firewall so that I can create the  captive portal.

ps: This captive portal is meant for wired LAN  computers. NOT WIFI.

---

