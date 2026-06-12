---
title: "[SOLVED] I need help with iptables"
date: 2008-10-24
forum: Security
---

### Post by lovinglinux on 2008-10-24
I'm still using Firestarter as primary iptables manager, but I'm slowly moving to command-line control while I learn more about iptables. So I have basic iptables rules created with Firestarter, in which all ports are closed and outbound traffic is limited. Whenever I need to open a port or allow specific outbound traffic, I use iptables commands. For example, I use the commands below to allow all outbound traffic. I have included some comments to allow anyone willing to help me to see if I understand it correctly:

```
# first I flush the OUTBOUND chain, which is created by Firestarter
iptables -F OUTBOUND

# then I replicate the basic rules created by Firestarter
iptables -A OUTBOUND -p icmp -j ACCEPT
iptables -A OUTBOUND -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTBOUND -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT

# then I add a rule to block this misterious IP which my machine tries to connect from time to time
iptables -A OUTBOUND -d 208.107.188.17 -j LSO

# and add the rule that will allow all remaining connections to go through
iptables -A OUTBOUND -j ACCEPT
```

When I need to reset the iptables rules to my basic configuration I stop and start Firestarter from command-line so it will flush the iptables rules and recreate them or I run the following commands to replicate the basic rules:

```
# first I flush the OUTBOUND chain, which was modified by the previous commands
iptables -F OUTBOUND

# then I replicate the basic rules created by Firestarter
iptables -A OUTBOUND -p icmp -j ACCEPT
iptables -A OUTBOUND -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTBOUND -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT

# then I add the rules  that I need for daily browsing, removing the one that allow all remaining traffic 
iptables -A OUTBOUND -p tcp -m tcp --dport 80 -s 192.168.x.x -j ACCEPT
iptables -A OUTBOUND -p udp -m udp --dport 80 -s 192.168.x.x -j ACCEPT
iptables -A OUTBOUND -p tcp -m tcp --dport 443 -s 192.168.x.x -j ACCEPT
iptables -A OUTBOUND -p udp -m udp --dport 443 -s 192.168.x.x -j ACCEPT
iptables -A OUTBOUND -p tcp -m tcp --dport 993 -s 192.168.x.x -j ACCEPT
iptables -A OUTBOUND -p udp -m udp --dport 993 -s 192.168.x.x -j ACCEPT
iptables -A OUTBOUND -p tcp -m tcp --dport 6667 -s 192.168.x.x -j ACCEPT
iptables -A OUTBOUND -p udp -m udp --dport 6667 -s 192.168.x.x -j ACCEPT
iptables -A OUTBOUND -j LSO
```

So, first I would like to know if I'm doing something wrong?

I have noticed that Firestarter creates some additional chains that I really don't know what they do. I also noticed that Firestarter creates some basic rules in the regular INPUT and OUTPUT chains, but whenever I add a new rule with Firestarter gui, the rule is added to the INBOUND and OUTBOUND chains. 

So, If I stop using Firestarter, could I simply use the rules posted above, replacing the INBOUND and OUTBOUND chains with INPUT and OUTPUT? I guess the LSO rule is related to how Firestarter handles (log or forward) the traffic between chains and should be replaced by REJECT or DROP right?

I read some tutorials about iptables and some of them explain how to create [[COLOR="DarkOrange"]**complex scripts**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=159661&highlight=firewall") that I really don't understand. Are those scripts really needed? Is there anything special to activate the iptables or simply adding rules like those above are enough to control iptables?

---

### Post by koenn on 2008-10-25
it's simple, really.
iptables knows 3 chains by default:
INPUT
OUTPUT
FORWARD (traffic passing through the machine, eg if its acting as a router)

it's possible to define custom chains, which is usually done to organize the rules in complex situations. Say you have a machine that act as a router, and is connected to 3 networks (A, B and C); you could define 3 chains, :
- one to handle traffic between A and B
- one to handle traffic between A and C
- one to handle traffic between B and C

Firestarter apparently creates an INBOUND and OUTBOUND chain, probably to more easily map its GUI representation.
Note that for user-defined chains to work, you need a jump rule in the default chains, something like
-A INPUT .... -j INBOUND

If you want to use iptables without Firestarter, you could just append or insert your rules to the INPUT and OUTPUT chains. 
If you prefer to keep using the INBOUND and OUTBOUND chains without firestarter, you'll need to be sure that these chains actually exists (or create them yourself) and that you have an adequate jump rule to divert traffic to these chains.

---

### Post by lovinglinux on 2008-10-25
My machine does not act like a router and I don't want to use additional chains if not needed, so If understood correctly I could deny all traffic in the FORWARD chain and just create the necessary rules in the INPUT and OUTPUT chains, right?

---

### Post by koenn on 2008-10-25
> **lovinglinux said:**
> My machine does not act like a router and I don't want to use additional chains if not needed, so If understood correctly I could deny all traffic in the FORWARD chain and just create the necessary rules in the INPUT and OUTPUT chains, right?

right.

---

### Post by lovinglinux on 2008-10-25
Thank you again. I will post some rules soon, just to make sure I'm not making any mistakes.

---

### Post by lovinglinux on 2008-10-26
This is what I have so far. It would be very helpful if someone could review and tell me if I'm doing something wrong.

```
iptables -N INBOUND
iptables -N OUTBOUND

iptables -P INPUT DROP 
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

iptables -A INPUT -i eth0 -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth0 -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -s 192.168.x.x -j ACCEPT  #router IP
iptables -A INPUT -s xxx.xxx.x.xx -j ACCEPT  #DNS IP
iptables -A INPUT -s xxx.xxx.x.xxx -j ACCEPT #DNS IP
iptables -A INPUT -i eth0 -d 255.255.255.255 -j DROP
iptables -A INPUT -d 192.168.2.255 -j DROP
iptables -A INPUT -d 224.0.0.0/8 -j DROP
iptables -A INPUT -s 224.0.0.0/8 -j DROP
iptables -A INPUT -s 255.255.255.255 -j DROP
iptables -A INPUT -m state --state INVALID -j DROP
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -p icmp -j INBOUND
iptables -A INPUT -j INBOUND
iptables -A INPUT -j DROP

iptables -A FORWARD -j DROP

iptables -A OUTPUT -o eth0 -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -o eth0 -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 53 -s 192.168.x.x -d xxx.xxx.x.xx -j ACCEPT #DNS 
iptables -A OUTPUT -o eth0 -p udp -m udp --dport 53 -s 192.168.x.x -d xxx.xxx.x.xx -j ACCEPT #DNS
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 53 -s 192.168.x.x -d xxx.xxx.x.xx -j ACCEPT #DNS
iptables -A OUTPUT -o eth0 -p udp -m udp --dport 53 -s 192.168.x.x -d xxx.xxx.x.xx -j ACCEPT #DNS
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 80 -s 192.168.x.x -j ACCEPT
iptables -A OUTPUT -o eth0 -p udp -m udp --dport 80 -s 192.168.x.x -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 443 -s 192.168.x.x -j ACCEPT
iptables -A OUTPUT -o eth0 -p udp -m udp --dport 443 -s 192.168.x.x -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 993 -s 192.168.x.x -j ACCEPT
iptables -A OUTPUT -o eth0 -p udp -m udp --dport 993 -s 192.168.x.x -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 6667 -s 192.168.x.x -j ACCEPT
iptables -A OUTPUT -o eth0 -p udp -m udp --dport 6667 -s 192.168.x.x -j ACCEPT
iptables -A OUTPUT -d 224.0.0.0/8 -j DROP
iptables -A OUTPUT -s 224.0.0.0/8 -j DROP
iptables -A OUTPUT -s 255.255.255.255 -j DROP
iptables -A OUTPUT -m state --state INVALID -j DROP
iptables -A OUTPUT -d 192.168.x.x -j ACCEPT #router IP
iptables -A OUTPUT -d 192.168.x.x -j ACCEPT #notebook
iptables -A OUTPUT -o lo -j ACCEPT
iptables -A OUTPUT -p icmp -j ACCEPT
iptables -A OUTPUT -j OUTBOUND
iptables -A OUTPUT -j DROP

iptables -A INBOUND -j LOG --log-prefix '***  INBOUND  ***' --log-level 4
iptables -A INBOUND -j DROP

iptables -A OUTBOUND -j LOG --log-prefix '***  OUTBOUND  ***' --log-level 4
iptables -A OUTBOUND -j REJECT
```

I expect that these rules will block all inbound connections, except the following:

- related to connections already established
- from my router
- from my ISP DNS servers
- from loopback

They also should block outbound connections, except the following:

- to my ISP DNS servers
- to ports 80,  443, 993 and 6667
- to my router
- to the other computer on my local network
- to the loopback
- outbound icmp packets

Connections that are not dropped in the INPUT or OUTPUT chains are expected to be sent to INBOUND and OUTBOUND chains, where they are all logged and DROPPED/REJECTED respectively.

Are these rules OK? Are there any missing rules that I should include or redundant rules that I could remove?

---

