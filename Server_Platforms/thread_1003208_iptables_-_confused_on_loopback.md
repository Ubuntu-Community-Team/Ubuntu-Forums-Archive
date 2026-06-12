---
title: "iptables - confused on loopback"
date: 2008-12-05
forum: Server Platforms
---

### Post by PC_Nerd on 2008-12-05
Hi,

I'm new to iptables - but I think I've got most of it covered.  I am however having trouble allowing programs liek aptitude etc through the firewall - I beleive I need to enable loopback or somethign similar:

here is my current configuration

iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT
(loopback)
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -i ! lo -d 127.0.0.0/8 -j REJECT

default rules:
INPUT=DROP
FORWARD=ACCEPT
OUTPUT=ACCEPT

now I read that I shoudl create/enable a localhost address like :
iptables -I INPUT -s 127.0.0.1 -j ACCEPT, but that doesnt work...


How to I allow all outbound connections and their incoming data to be accepted? ( "ESTABLISHED" comes to mind, however thats where I get really confused).

Thanks,
PC_Nerd

---

### Post by R.Bucky on 2008-12-05
I do not know the specific code to use for iptables. I utiliz Firestarter (firewall) and IPBlock for my iptables management. Both are fairly user friendly.

---

### Post by hictio on 2008-12-05
This is my standard iptables setup for proctecting a server (no routing nor NAT), just a tight iptables firewall for a box with a fixd IP address.
You can add more services creating more chains, if you like.

```

#!/bin/sh

IPT="/sbin/iptables"
NIC="eth0"
HOST="192.168.11.2"
lan="192.168.11.0/24"

######################
## Default policies ##
######################
$IPT -F
$IPT -P INPUT DROP
$IPT -P OUTPUT DROP
$IPT -P FORWARD DROP

## ------------------------------------------------------

############################################
## Established connections are maintained ##
############################################
$IPT -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

##############
## LoopBack ##
##############
$IPT -A INPUT -i lo -j ACCEPT


######################
## BEGIN ICMP chain ##
######################
 $IPT -N PING
 $IPT -t filter -A INPUT -j PING

$IPT -A PING -i $NIC  -s 0/0 -d $HOST -m limit --limit 3/s --limit-burst 8 -p icmp --icmp-type 8 -j ACCEPT
$IPT -A PING -i $NIC1 -s 0/0 -d $HOST -m limit --limit 3/s --limit-burst 8 -p icmp --icmp-type 8 -j ACCEPT

 $IPT -A PING -j RETURN
####################
## END ICMP chain ##
####################

#####################
## BEGIN ssh chain ##
#####################
 $IPT -N SSHALLOW
 $IPT -t filter -A INPUT -j SSHALLOW

$IPT -A SSHALLOW -m state --state NEW -i $NIC -p tcp -s $lan -d $HOST --dport ssh --syn -j ACCEPT

 $IPT -A SSHALLOW -j RETURN
###################
## END ssh chain ##
###################


#######################
## BEGIN HTTPD chain ##
 $IPT -N HTTPD
 $IPT -t filter -A INPUT -j HTTPD

$IPT -A HTTPD -m state --state NEW -i $NIC -p tcp -s 0/0 -d $HOST --dport http --syn -j ACCEPT

$IPT -A HTTPD -m state --state NEW -i $NIC -p tcp -s 0/0 -d $HOST --dport https --syn -j ACCEPT

 $IPT -A HTTPD -j RETURN
## END HTTP chain ##
####################

##############
## Outgoing ##
##############
$IPT -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A OUTPUT -m state --state NEW -o $NIC -j ACCEPT
$IPT -A OUTPUT -o lo -j ACCEPT

# EoF #

```

---

### Post by PC_Nerd on 2008-12-06
Ok thanks,

your code :
$IPT -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
Fixed my issue.  I wasnt allowing established connections inbound...

* just a note though tha tI read somewhere that its best to edit your /etc/network/interfaces file to include the like iptables-restore <[file from iptables-save], because if your running it as a startup script there are a few seconds between when the networking is on and working, and when the firewall loads - which means that teh server is vulnerable.  Anyway - Just an opinion ( I dont personalyl  know).

Thanks for your help.

---

