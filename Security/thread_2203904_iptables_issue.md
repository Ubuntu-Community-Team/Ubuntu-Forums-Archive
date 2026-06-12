---
title: "iptables issue"
date: 2014-02-05
forum: Security
---

### Post by ant2ne on 2014-02-05
This first line here has me concerned in my INPUT policy chain.
**ACCEPT     all  --  anywhere             anywhere    **

```
iptables --list
Chain INPUT (policy DROP)
target     prot opt source               destination         
**ACCEPT     all  --  anywhere             anywhere**            
DROP       all  --  researchscan010.eecs.umich.edu  anywhere            
DROP       all  --  mybigmart.com        anywhere            
DROP       all  --  250-240-80-95.ptr.cloud4com.com  anywhere            
DROP       all  --  lhr08s03-in-f15.1e100.net  anywhere            
DROP       all  --  bignay.canonical.com  anywhere            
DROP       all  --  ord08s13-in-f27.1e100.net  anywhere            
DROP       all  --  server-54-230-35-79.stl2.r.cloudfront.net  anywhere            
DROP       all  --  cpe-68-173-127-141.nyc.res.rr.com  anywhere            
LOG        tcp  --  anywhere             anywhere             multiport sports ssh LOG level info prefix "[IPTABLES PORT 22 "
LOG        tcp  --  anywhere             anywhere             multiport sports http LOG level info prefix "[IPTABLES PORT 80 "
LOG        tcp  --  anywhere             anywhere             multiport sports https LOG level info prefix "[IPTABLES PORT 443 "
ACCEPT     icmp --  anywhere             anywhere             icmp echo-reply
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request limit: avg 1/sec burst 5
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:1022
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:1022
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:3000
DROP       tcp  --  anywhere             anywhere             tcp dpt:3000
DROP       all  --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
DROP       all  --  researchscan010.eecs.umich.edu  anywhere            
DROP       all  --  mybigmart.com        anywhere            
DROP       all  --  250-240-80-95.ptr.cloud4com.com  anywhere            
DROP       all  --  lhr08s03-in-f15.1e100.net  anywhere            
DROP       all  --  bignay.canonical.com  anywhere            
DROP       all  --  ord08s13-in-f27.1e100.net  anywhere            
DROP       all  --  server-54-230-35-79.stl2.r.cloudfront.net  anywhere            
DROP       all  --  cpe-68-173-127-141.nyc.res.rr.com  anywhere            
LOG        tcp  --  anywhere             10.1.1.5             state NEW LOG level info prefix "[IPTABLES FORWARD TO SERVER "
LOG        tcp  --  anywhere             10.1.1.1             state NEW LOG level info prefix "[IPTABLES FORWARD TO FIREWALL"
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
DROP       all  --  10.1.1.194           anywhere            
ACCEPT     all  --  anywhere             anywhere    
```

The thing is I don't know what line in my iptables script is causing this potential issue.
```
#!/bin/bash
######################
#
#      Configuring hardware and
#
#  settings up variables for the script
#
######################
echo "setting up variables"
#_ethOUT is DHCP from ISP (outgoing interface)
_ethOUT=eth1
_ethIN=eth0
dhclient -v $_ethOUT
_GATEWAY=$(ifconfig $_ethOUT | grep -v inet6 | grep inet | cut -d : -f 2 | sed 's/Bcast//')
echo "The gateway inteface is $_ethOUT and its IP is $_GATEWAY"
echo "The internal interface is $_ethIN"
_Me=10.1.1.69
_FTP=10.1.1.5
_RUNUO=10.1.1.7
_RUNUO_PORT=8888
_RUNUO2=10.1.1.19
_RUNUO2_PORT=8889
_CYGNENOS=10.1.1.1
_myDNS=$_CYGNENOS
_myDHCP=$_CYGNNOS
_Win2k8Server=10.1.1.9
_OpenDNS=208.67.222.222
_Player=10.1.1.17
_Webdav=$_ethOUT
_Webserver=10.1.1.5
_Unfiltered=10.1.1.1
_Minecraft1=10.1.1.21
_Minecraft2=10.1.1.22

########################
#
#  CRITICAL:  Enable IP forwarding since it is disabled by default
#
echo Enabling forwarding...
echo "1" > /proc/sys/net/ipv4/ip_forward



########################
#
# FLUSHING
#
#
########################
echo "flushing"
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
iptables -F INPUT
iptables -F OUTPUT
iptables -F FORWARD
iptables -t nat -F
iptables -F LOG
iptables -t nat -F PREROUTING
iptables -t nat -F POSTROUTING


########################
#
# BLOCKIG INTERNAL HOST
#
#
########################
# echo Blocking internal IPs
#iptables -A OUTPUT -s 10.1.1.194 -j DROP
#iptables -A FORWARD -s 10.1.1.194 -j DROP
#iptables -A INPUT -s 10.1.1.194 -j DROP


########################
#
# BLOCKIG EXTERNAL IPS
#  THESE GUYS SEEM WAY TO CURIOUS
#
########################
echo Blocking External IPs
_BLOCK=141.212.121.10
#  nslookup $_BLOCK | grep name >> /var/log/iptables_blockedIPs.log
  iptables -A INPUT -s $_BLOCK -i $_ethOUT -j DROP
  iptables -A FORWARD -s $_BLOCK -i $_ethOUT -j DROP
_BLOCK=192.241.165.117
#  nslookup $_BLOCK | grep name >> /var/log/iptables_blockedIPs.log
  iptables -A INPUT -s $_BLOCK -i $_ethOUT -j DROP
  iptables -A FORWARD -s $_BLOCK -i $_ethOUT -j DROP
_BLOCK=95.80.240.250
#  nslookup $_BLOCK | grep name >> /var/log/iptables_blockedIPs.log
  iptables -A INPUT -s $_BLOCK -i $_ethOUT -j DROP
  iptables -A FORWARD -s $_BLOCK -i $_ethOUT -j DROP
_BLOCK=173.194.41.143
#  nslookup $_BLOCK | grep name >> /var/log/iptables_blockedIPs.log
  iptables -A INPUT -s $_BLOCK -i $_ethOUT -j DROP
  iptables -A FORWARD -s $_BLOCK -i $_ethOUT -j DROP
#_BLOCK="74.125.193.154 /16" 
##  nslookup $_BLOCK | grep name >> /var/log/iptables_blockedIPs.log
#  iptables -A INPUT -s $_BLOCK -i $_ethOUT -j DROP
#  iptables -A FORWARD -s $_BLOCK -i $_ethOUT -j DROP
_BLOCK=91.189.95.36
#  nslookup $_BLOCK | grep name >> /var/log/iptables_blockedIPs.log
  iptables -A INPUT -s $_BLOCK -i $_ethOUT -j DROP
  iptables -A FORWARD -s $_BLOCK -i $_ethOUT -j DROP
_BLOCK=173.194.46.123  
#  nslookup $_BLOCK | grep name >> /var/log/iptables_blockedIPs.log
  iptables -A INPUT -s $_BLOCK -i $_ethOUT -j DROP
  iptables -A FORWARD -s $_BLOCK -i $_ethOUT -j DROP
_BLOCK=54.230.35.79
#  nslookup $_BLOCK | grep name >> /var/log/iptables_blockedIPs.log
  iptables -A INPUT -s $_BLOCK -i $_ethOUT -j DROP
  iptables -A FORWARD -s $_BLOCK -i $_ethOUT -j DROP

_BLOCK=68.173.127.141
#  nslookup $_BLOCK | grep name >> /var/log/iptables_blockedIPs.log
  iptables -A INPUT -s $_BLOCK -i $_ethOUT -j DROP
  iptables -A FORWARD -s $_BLOCK -i $_ethOUT -j DROP

########################
#
# LOGGING
#
#
########################
echo "Setting up logging"
# iptables -A INPUT  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES INPUT "
# iptables -A OUTPUT  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES OUTPUT "
# iptables -A FORWARD -i $_ethOUT -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES FORWARD "   

iptables -A FORWARD -i $_ethOUT -o $_ethIN -p tcp -d 10.1.1.5 -m state --state NEW -j LOG --log-prefix "[IPTABLES FORWARD TO SERVER " --log-level info
iptables -A FORWARD -i $_ethOUT -o $_ethIN -p tcp -d 10.1.1.1 -m state --state NEW -j LOG --log-prefix "[IPTABLES FORWARD TO FIREWALL " --log-level info

iptables -A INPUT -i $_ethOUT -p tcp -m multiport --sport 22 -j LOG --log-prefix "[IPTABLES PORT 22 " --log-level info
iptables -A INPUT -i $_ethOUT -p tcp -m multiport --sport 80 -j LOG --log-prefix "[IPTABLES PORT 80 " --log-level info
iptables -A INPUT -i $_ethOUT -p tcp -m multiport --sport 443 -j LOG --log-prefix "[IPTABLES PORT 443 " --log-level info


##########################
#
# ICMP
#
##########################
iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT  -p icmp --icmp-type echo-reply   -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT


# Work around for stupid websites blocking ICMP (just for normal surfing)
 iptables -t mangle -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu
# Allow ICMP for frag notification
# --icmp-type 8 = ping
# iptables -t filter -A INPUT -p icmp -s 0/0 -d $ip_eth2 -m state --state NEW -j ACCEPT


################
#
# Masqurading
#
#################
echo "setting up masqurading"
# only need the one outgoing interface for internet access
iptables -t nat -A POSTROUTING -o $_ethOUT -j MASQUERADE
# iptables -t nat -A POSTROUTING -o $_ethOUT -j SNAT --to $_GATEWAY

################
#
# INPUT
#   - IN TO THIS SERVER
#
###############
echo "setting up INPUT"
# default states
iptables -I INPUT 1 -i lo -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# ssh 
iptables -A INPUT -i $_ethOUT -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -i $_ethOUT -p tcp --dport 1022 -j ACCEPT
iptables -A INPUT -i $_ethIN -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -i $_ethIN -p tcp --dport 1022 -j ACCEPT

# webmin
iptables -A INPUT -i $_ethIN -p tcp --dport 3000 -j ACCEPT
iptables -A INPUT -i $_ethOUT -p tcp --dport 3000 -j DROP


################
#
# OUTPUT
#
################
iptables -A OUTPUT -s 10.1.1.194 -j DROP


###################
#
# FORWARD
#
##################
echo "setting up FORWARD"
iptables -A FORWARD -j ACCEPT



iptables -t nat -A PREROUTING -p tcp --dport 1022 -j DNAT --to 10.1.1.1:22


##################
#
# RUNUO DNAT
#
#################
echo "setting up RUNUO DNAT"
iptables -t nat -A PREROUTING -p tcp --dport $_RUNUO_PORT -j DNAT --to $_RUNUO:$_RUNUO_PORT
iptables -t nat -A POSTROUTING -s $_RUNUO -p tcp --sport $_RUNUO_PORT -j SNAT --to-source $_GATEWAY
iptables -t nat -A PREROUTING -p tcp --dport $_RUNUO2_PORT -j DNAT --to $_RUNUO2:$_RUNUO2_PORT
iptables -t nat -A POSTROUTING -s $_RUNUO2 -p tcp --sport $_RUNUO2_PORT -j SNAT --to-source $_GATEWAY

##########################
#
# RDP NATs
#
#########################
echo "setting up RDP DNAT"
iptables -t nat -A PREROUTING -i $_ethOUT -p tcp --dport 3389 -j DNAT --to $_Player:3389



######################
#
# Webserver DNAT
#
#######################
#iptables -A FORWARD -i $_ethOUT -o $_ethIN -p tcp --dport 80 -d $_Webserver -m state --state NEW -j LOG --log-prefix "[IPTABLES FORWARD 80: " --log-level info
#iptables -t nat -A PREROUTING -p tcp -i  $_ethOUT --dport 80 -j LOG --log-prefix "[IPTABLES FORWARD " --log-level info
iptables -t nat -A PREROUTING -p tcp -i  $_ethOUT --dport 80 -j DNAT --to $_Webserver:80 
#iptables -A FORWARD -i $_ethOUT -o $_ethIN -p tcp --dport 443 -d $_Webserver -m state --state NEW -j LOG --log-prefix "[IPTABLES FORWARD 443: " --log-level info
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT  --dport 443 -j DNAT --to $_Webserver:443 



#####################
#
# OpenDNS DNAT OUTGOING
#
####################
echo "setting up OpenDNS prerouting (the trap)"

iptables -t nat -A PREROUTING  -s $_Me -p udp --dport 53 -j DNAT --to 8.8.8.8:53
iptables -t nat -A PREROUTING  -s $_Me -p tcp --dport 53 -j DNAT --to 8.8.8.8:53

iptables -t nat -A PREROUTING  -s 10.1.1.68 -p udp --dport 53 -j DNAT --to 8.8.8.8:53
iptables -t nat -A PREROUTING  -s 10.1.1.68 -p tcp --dport 53 -j DNAT --to 8.8.8.8:53

iptables -t nat -A PREROUTING  -s $_RUNUO -p udp --dport 53 -j DNAT --to 8.8.8.8:53
iptables -t nat -A PREROUTING  -s $_RUNUO2 -p tcp --dport 53 -j DNAT --to 8.8.8.8:53

iptables -t nat -A PREROUTING ! -s $_myDNS -p udp --dport 53 -j DNAT --to $_OpenDNS:53
iptables -t nat -A PREROUTING ! -s $_myDNS -p tcp --dport 53 -j DNAT --to $_OpenDNS:53


########################
#
#   Default settings end
#   of chain and  rejects
#
########################
echo "setting up defaults for end of chains"
iptables -A INPUT -i $_ethOUT -j DROP
iptables -A INPUT -i $_ethIN -j DROP
iptables -A OUTPUT -j ACCEPT


########################
#
#  OTHER STUFF
#
########################

# iptables -L
 ifconfig eth0 mtu 1500
 ifconfig eth1 mtu 1500
#echo "MTU of eth0"
ifconfig eth0 | grep MTU
#echo "MTU of eth1"
ifconfig eth1 | grep MTU
#/etc/init.d/ntop restart

```

---

### Post by tomearp on 2014-02-06
That rule is created by
```
iptables -I INPUT 1 -i lo -j ACCEPT
```

If you list iptables with
```
iptables -L -n -v
```
you will see that the rule applies to the loop back interface.

---

### Post by ant2ne on 2014-02-07
thank you very much!

You'd think that source and destination wouldn't be anywhere if it was 127.x.x..x.

---

### Post by SeijiSensei on 2014-02-07
The rule 
```
iptables -A INPUT -i lo -j ACCEPT
```
is actually a shorthand for 
```
iptables -A INPUT -i lo -s 0/0 -d 0/0 -j ACCEPT
```
Unless you specify either the source or destination address, or both, iptables assumes you mean all traffic on the lo interface.

In the future, I suggest using "iptables -L -nv" to list your rules.  You'll see the entire rule that way, and things like "anywhere" will be translated to their IP addresses.

---

