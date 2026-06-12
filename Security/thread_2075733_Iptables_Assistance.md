---
title: "Iptables Assistance"
date: 2012-10-24
forum: Security
---

### Post by knichel on 2012-10-24
I have been using iptables for a bit now allong with squid/dansguardian as proxy/content filter.  I have 3 nic's in my server. 
eth0 = my LAN (Students)
eth1 = ISP
eth2 = another LAN (Admin)

My Needs:
[LIST]
[*]I need to allow certain traffic into my network so I can get to my computer at my desk from home.
[*]I need to allow my computer to access the network off of eth2 to access a mssql server.
[*]I need to allow certain computers (2 small blocks of addresses) unfiltered access to the internet.
[/LIST]

Here is my iptables -L -v output for Filter and Nat tables.  I have nothing in Mangle so I omitted it.

```

********************
*** FILTER TABLE ***
********************
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
70820   20M ACCEPT     all  --  lo     any     anywhere             anywhere            
 7386   10M ACCEPT     all  --  eth1   any     anywhere             anywhere            state RELATED,ESTABLISHED 
  460  161K ACCEPT     all  --  eth2   any     anywhere             anywhere            
71614   40M ACCEPT     all  --  eth0   any     anywhere             anywhere
# Allow specific protocols into my network            
    3   180 ACCEPT     tcp  --  eth1   any     anywhere             anywhere            tcp dpt:www 
    1    60 ACCEPT     tcp  --  eth1   any     anywhere             anywhere            tcp dpt:ssh 
    0     0 ACCEPT     tcp  --  eth1   any     anywhere             anywhere            tcp dpt:webmin 
    0     0 ACCEPT     tcp  --  eth1   any     anywhere             anywhere            tcp dpt:smtp 
    0     0 ACCEPT     tcp  --  eth1   any     anywhere             anywhere            tcp dpt:imap2 
    5   240 ACCEPT     tcp  --  eth1   any     anywhere             anywhere            tcp dpt:https 
    0     0 ACCEPT     tcp  --  eth1   any     anywhere             anywhere            tcp dpt:38000 
    0     0 ACCEPT     tcp  --  eth1   any     anywhere             anywhere            tcp dpt:10180 
    0     0 ACCEPT     tcp  --  eth1   any     anywhere             anywhere            tcp dpt:13389 
    0     0 ACCEPT     tcp  --  eth1   any     anywhere             anywhere            tcp dpt:10122 
    0     0 ACCEPT     tcp  --  eth1   any     anywhere             anywhere            tcp dpt:ms-sql-s 
    0     0 DROP       tcp  --  eth0   any     anywhere             anywhere            tcp dpt:https 
    0     0 DROP       tcp  --  eth0   any     anywhere             anywhere            tcp dpt:ircd 
  181 44587 LOG        all  --  any    any     anywhere             anywhere            LOG level warning 
  181 44587 DROP       all  --  any    any     anywhere             anywhere            

Chain FORWARD (policy ACCEPT 28166 packets, 36M bytes)
 pkts bytes target     prot opt in     out     source               destination  
# Allow my laptop to go to the Admin Network       
    0     0 ACCEPT     all  --  eth0   eth2    {private ip address} anywhere            
# Allow the VirtualMachine on my laptop to go to the Admin Network       
    0     0 ACCEPT     all  --  eth0   eth2    {private ip address} anywhere   
# Allow all workstations on my network to go to the internet         
17972 1747K ACCEPT     all  --  eth0   eth1    {private net ID}/24  anywhere
# Allow traffic from outside to come into my network            
    0     0 ACCEPT     all  --  eth0   !eth2   anywhere             anywhere  
# Allow traffic from Admin Network to get to my network or the internet          
    0     0 ACCEPT     all  --  eth2   any     anywhere             anywhere            
# Deny traffic from my network to the Admin Network
    0     0 DROP       all  --  eth0   eth2    anywhere             anywhere            

Chain OUTPUT (policy ACCEPT 4629 packets, 451K bytes)
 pkts bytes target     prot opt in     out     source               destination         
70820   20M ACCEPT     all  --  any    lo      anywhere             anywhere            
82912   20M ACCEPT     all  --  any    eth0    anywhere             anywhere            
  371  116K ACCEPT     all  --  any    eth2    anywhere             anywhere            


*****************
*** NAT TABLE ***
*****************
Chain PREROUTING (policy ACCEPT 10721 packets, 1041K bytes)
 pkts bytes target     prot opt in     out     source               destination   
# I use this next rule to bypass proxy when needed.    Do Nothing by default I change to Accept when needed.  
10292  618K            tcp  --  eth0   any     {private net ID}/24       anywhere            tcp 
# This next one is for a set of lab computers that students use for practice installs etc.  Always need access to internet without proxy
    0     0 ACCEPT     tcp  --  eth0   any     {private subnet ID}/27     anywhere            tcp 
# This next one is for a group of computers that also ALWAYS need acces to the internet without proxy
 1057 63420 ACCEPT     tcp  --  eth0   any     {private subnet ID}/27     anywhere            tcp 
# Some port forwarding rules for my from outside
    0     0 DNAT       tcp  --  eth1   any     anywhere              tcp dpt:10180 to:{my private ip address}:80 
    0     0 DNAT       tcp  --  eth1   any     anywhere             {my public ip address} tcp dpt:10122 to:{my private ip address}:22 
    0     0 DNAT       tcp  --  eth1   any     anywhere             {my public ip address} tcp dpt:38000 to:{my private ip address}:38000 
    0     0 DNAT       tcp  --  eth1   any     anywhere             {my public ip address} tcp dpt:13389 to:{my private ip address}:3389 
    0     0 DNAT       tcp  --  eth1   any     anywhere             {my public ip address} tcp dpt:ms-sql-s to:{my mssql ip address}:1433 
 6277  377K DNAT       tcp  --  eth0   any     anywhere             anywhere            tcp dpt:www to:{my proxy/filter ip address}:8080 
    0     0 REDIRECT   tcp  --  eth0   any     anywhere             anywhere            tcp dpt:3128 redir ports 8080 

Chain POSTROUTING (policy ACCEPT 8753 packets, 553K bytes)
 pkts bytes target     prot opt in     out     source               destination         
 6404  407K MASQUERADE  all  --  any    eth1    anywhere             anywhere            
  188 16194 MASQUERADE  all  --  any    eth2    anywhere             anywhere            

Chain OUTPUT (policy ACCEPT 10235 packets, 651K bytes)
 pkts bytes target     prot opt in     out     source               destination         


```

I do not really know a lot about iptables and seek advice/input as to the effectiveness of this configuration.

Thanks in advance.

---

### Post by Doug S on 2012-10-25
Your question is not that easy to answer. It somewhat depends on yourself and how rigourous you want to be and how much time you like to spend reviewing your log files. For example, myself I look at my logs constantly, therefore I include lots of iptables rules that log information, with unique identifier strings. Anyway, I have a couple of comments, but keep in mind thay are just my opinion and other very respected forum contributers might have different options.
 
I would suggest a default policy of DROP for all 3 main chains, INPUT, FORWARD, and OUTPUT. That forces you to specifically deal with every senario within those chains. I even have a catch all rule, with logging, at the end of those chains. I.E. I always expect the default packet and byte counters to be 0.
 
For your FORWARD chain, I would expect to see a "RELATED, ESTABLISHED" accept rule for stuff from the outside world.
 
I do not understand why you have a DROP rule for https from eth0. However, it isn't clear to me that path would ever be taken anyhow.
 
Suggest some sort of limiting type rules on your SSH access from the outside world. For example:```
# Secure Shell on port 22.
#
# Dynamic Badguy List. Detect and DROP idiots that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:"$
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT

```Note: Some prefer to use "REJECT" rather than "DROP".
Do you really want to be able to access webmin from the outside world? (Note: I don't use webmin, so don't know as to the wisedom of external access).

---

