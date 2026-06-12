---
title: "Changed from firestarter to Gufw...conflicts"
date: 2011-03-11
forum: Security
---

### Post by Riddermark on 2011-03-11
Just want to stealth ports on my laptop.  Had problems with firestarter when I installed in on 10.10.  Set Firestater back to defaults and then dumped it with:


```
sudo apt-get purge firestarter

```Set up Gufw to defaults and now am not sure what I am seeing with iptables.  

iptables -L shows

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            state INVALID limit: avg 3/min burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination
```Do these settings look correct for default settings for Gufw?  or do I still have some problems with the old firestarter settings not being removed.  All I want is all ports stealthed.  I know that ping is enabled but I believe that is a default setting in ufw.  Could I restore iptables to default with:

```
sudo iptables -F
```and then enable Gufw and set default?


Thanks in advance for your help

Kevin

---

### Post by skraps on 2011-03-11
use the gufw firewall gui to adjust settings with the gui utillity.

This is the script I use for my firewall. Its really basic. drop every thing comming in except ssh, and allow all outgoing connections from this machine that are established or related. and log anything else that is droped. 


```

#!/bin/bash

IPT="/sbin/iptables"

DEVS=( "lo" "eth1" )

LOIP=`/sbin/ifconfig ${DEVS[0]} | awk 'NR == 2 {print $2}' | sed -e 's/:/ /g' | awk '{print $2}'`
    
ETH1IP=`/sbin/ifconfig ${DEVS[1]} | awk 'NR == 2 {print $2}' | sed -e 's/:/ /g' | awk '{print $2}'`
ETH1MASK=`/sbin/ifconfig ${DEVS[1]} | awk 'NR == 2 {print $3}' | sed -e 's/:/ /g' | awk '{print $2}'`
ETH1MAC=`ifconfig ${DEVS[1]} | awk 'NR == 1 {print $5}'`

SSH="1"
TELNET="23"

# Shortcuts
OK="-j ACCEPT"
NO="-j DROP"
TCP="-p tcp"
UDP="-p udp"



# You go toyota!!!
$IPT --flush


# Drop ICMP echo-request messages sent to broadcast or multicast addresses
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

# Drop source routed packets
echo 0 > /proc/sys/net/ipv4/conf/all/accept_source_route

# Enable TCP SYN cookie protection from SYN floods
echo 1 > /proc/sys/net/ipv4/tcp_syncookies

# Don't accept ICMP redirect messages
echo 0 > /proc/sys/net/ipv4/conf/all/accept_redirects

# Don't send ICMP redirect messages
echo 0 > /proc/sys/net/ipv4/conf/all/send_redirects

# Enable source address spoofing protection
echo 1 > /proc/sys/net/ipv4/conf/all/rp_filter

# Log packets with impossible source addresses
echo 1 > /proc/sys/net/ipv4/conf/all/log_martians

$IPT -A INPUT -m state --state ESTABLISHED,RELATED $OK
$IPT -A OUTPUT -m state --state NEW,ESTABLISHED,RELATED $OK

$IPT --policy INPUT DROP
$IPT --policy OUTPUT DROP 
$IPT --policy FORWARD DROP

# sshd baby
$IPT -I INPUT -i ${DEV[1]} $TCP -s 0/0 -d $ETH1IP --dport $SSH $OK


# allow all outgoing connections from this machine
$IPT -I OUTPUT -o ${DEV[1]} $TCP -s $ETH1IP -d 0/0 $OK

$IPT -I INPUT -i ${DEV[0]} $TCP -s $LO $OK
$IPT -I OUTPUT -o ${DEV[0]} $TCP -s $LO $OK

$IPT -A INPUT -m limit --limit 15/minute -j LOG --log-level 7 --log-prefix "[INPUT] Dropped: "
$IPT -A OUTPUT -m limit --limit 15/minute -j LOG --log-level 7 --log-prefix "[OUTPUT]Dropped: "
$IPT -A FORWARD -m limit --limit 15/minute -j LOG --log-level 7 --log-prefix "[FORWARD]Dropped: "

```

---

### Post by Riddermark on 2011-03-12
Would like to restore iptables back to default settings, accept all, and start over.  If I use:
```
$ sudo iptables -F
```would that work?  Also should I purge Gufw before I reset iptables?  Any help would be appreciated, as you can tell I am not experienced with iptables and I realize that I should not mess with it too much given my skill level.


Thanks

---

### Post by skraps on 2011-03-12
```

iptables -F
iptables --policy INPUT ACCEPT
iptables --policy OUTPUT ACCEPT
iptables --policy FORWARD ACCEPT

```

You will need to set the default policy of your main chains back to acccept.

---

### Post by Riddermark on 2011-03-15
Thanks for the help.  One thing I would still like to know is if the settings that I posted in iptables are default for Gufw?  I know it is alot to look at.  Just want to make sure that I don't have any conflicts with having firestarter installed before using Gufw.  

Thanks

---

### Post by bodhi.zazen on 2011-03-16
ufw / gufw all set rules for iptables.

iptables is s front end for net filter.

You should not "mix and match" the tools you use to configure iptables.

To enable ufw:

```
sudo ufw enable
```

To disable it:

```
sudo ufw disable
```

You can manually flush the rules if you wish, with iptables -F, but you then need to use -X for the empty chains. Well, you do not *need* to use -X as the chain is empty after the -F .

See:

	[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
	[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
	[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

As long as you purged firestarter you will be fine ;)

---

