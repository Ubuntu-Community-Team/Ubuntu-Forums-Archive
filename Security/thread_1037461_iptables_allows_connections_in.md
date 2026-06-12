---
title: "iptables allows connections in"
date: 2009-01-11
forum: Security
---

### Post by havok2 on 2009-01-11
I am trying to secure my box and during testing of my iptables I find that anytime I have a rule as follows:

iptables -A INPUT -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
or
iptables -A INPUT -p tcp -m state --state ESTABLISHED -j ACCEPT

The ESTABLISHED,RELATED allows all connections to be permitted.  This should only occur if the connection already exists in the connection tracking table.  

I read some articles and put in the following combinations:

iptables -A INPUT -p tcp -m state --state ESTABLISHED -j check-state
iptables -N check-state
iptables -A check-state -m state --state NEW -j DROP
iptables -A check-state -m state --state INVALID -j DROP
iptables -A check-state -m state --state ESTABLISHED,RELATED -j ACCEPT

and get the following output when I ssh to he box (have no rule to allow ssh btw:

Chain check-state (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  any    any     anywhere             anywhere            state NEW 
    0     0 DROP       all  --  any    any     anywhere             anywhere            state INVALID 
 2216 2080K ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 

I have tried many combinations to include using the --syn or !--syn as I have seen in some documentation and get nothing.  With this problem it really defeats the purpose of having a firewall. 

If anyone can assist it would be greatly appreciated.

---

### Post by gombadi on 2009-01-11
What is the default policy set to?

Have a look at your rules and policy with -
```

sudo iptables -vnL

```

If default policy is Accept then your ssh connection will be accepted as you describe.

---

### Post by havok2 on 2009-01-12
I set my default policies to DROP.

Chain INPUT (policy DROP 1 packets, 48 bytes)

---

### Post by havok2 on 2009-01-12
I actually made INPUT, FORWARD and OUTPUT default policy DROP as to not miss anything.

---

### Post by The Cog on 2009-01-12
Your INPUT chain should always permit packets with a source interface of lo, otherwise several things like print spooling break because the computer can't talk to itself when it needs to. If course, having a rule that allows the computer to connect to itself means that you can't reliably test the firewalls from the same computer. I wonder if that's why you think that ESTABLISHED,RELATED is allowing more than it should.

I don't think setting new rules clears its memory of existing connections. This may be another reason that you seem to be getting more permitted than you expect.

I have to say that I think you have a configuration problem or a problem with what you expect iptables to be doing. I really don't think there is a basic problem with iptables itself. It has been pretty thoroughly tested by lots of people such as yourself. A basic bug would have been spotted a long time ago.

---

### Post by havok2 on 2009-01-12
I actually have a rule in to allow lo connections and that works fine.  The reason I think it is not working is that when I take the established,related rule out I cannot ssh to the box (as I am trying to accomplish), but as soon as I put the rule in I can get to it and it hits that rule (as seen by hit counter in the email).  I also use iptstate to see that the session clears before trying to do another with a new configuration.  Another note, it is not specific to ssh either I can do that on any service in the box.  

Actually I have seen reference to a problem of them putting in a instance so that if you were running multiple firewalls it would take a new connection into another firewall so that the session is not disconnected in case of a firewall failure.

I have been through the docs and established is only to allow connections that are already in the state table (this is my expectation) and related is for apps like FTP (but I have put the established in by itself as well and get the same.

In the spirit of learning maybe what I am doing wrong I will put my firewall rules and the outputs after I tried ssh to the box.

#!/bin/sh
echo "Loading iptables rules..."


# DEFINE FORWARD CHAIN
/sbin/iptables -P FORWARD DROP

# DEFINE a LOGDROP CHAIN
/sbin/iptables -N LOGDROP
/sbin/iptables -A LOGDROP -j LOG --log-prefix "FW: DROP " --log-level debug
/sbin/iptables -A LOGDROP -j DROP

# DEFINE a LOGPASS CHAIN
/sbin/iptables -N LOGPASS
/sbin/iptables -A LOGPASS -j LOG --log-prefix "FW: PASS " --log-level debug
/sbin/iptables -A LOGPASS -j ACCEPT

# DEFINE a check-state CHAIN
/sbin/iptables -N check-state
/sbin/iptables -A check-state -m state --state NEW -j DROP
/sbin/iptables -A check-state -m state --state INVALID -j DROP
/sbin/iptables -A check-state -m state --state ESTABLISHED,RELATED -j ACCEPT

# DEFINE INPUT CHAIN 
/sbin/iptables -P INPUT DROP
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A INPUT -p tcp --syn -j ACCEPT
/sbin/iptables -A INPUT -p tcp -m state --state ESTABLISHED -j check-state
/sbin/iptables -A INPUT -p tcp -j LOGDROP

/sbin/iptables -A INPUT -p udp --dport 67:68 --sport 67:68 -j ACCEPT
/sbin/iptables -A INPUT -p udp -s 0/0 --sport 53 -j ACCEPT
/sbin/iptables -A INPUT -p udp -s 0/0 --sport isakmp -j ACCEPT
/sbin/iptables -A INPUT -p udp -i vmnet8 --dport 12345 -j ACCEPT
/sbin/iptables -A INPUT -p udp --dport 3000:6000 --sport 3000:6000 -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A INPUT -p udp -j LOGDROP 

# DEFINE OUTPUT CHAIN
/sbin/iptables -P OUTPUT DROP
/sbin/iptables -A OUTPUT -p ip -m state --state NEW,ESTABLISHED -j ACCEPT



OUTPUT:

Chain INPUT (policy DROP 1 packets, 48 bytes)
 pkts bytes target     prot opt in     out     source               destination         
41061  102M ACCEPT     all  --  lo     any     anywhere             anywhere            
    2   128 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
85564  108M check-state  tcp  --  any    any     anywhere             anywhere            state ESTABLISHED 
    0     0 LOGDROP    tcp  --  any    any     anywhere             anywhere            
   35 11491 ACCEPT     udp  --  any    any     anywhere             anywhere            udp spts:bootps:bootpc dpts:bootps:bootpc 
  637  170K ACCEPT     udp  --  any    any     anywhere             anywhere            udp spt:domain 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp spt:isakmp 
    0     0 ACCEPT     udp  --  vmnet8 any     anywhere             anywhere            udp dpt:12345 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp spts:3000:x11 dpts:3000:x11 state RELATED,ESTABLISHED 
  169 32892 LOGDROP    udp  --  any    any     anywhere             anywhere            

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy DROP 6 packets, 1563 bytes)
 pkts bytes target     prot opt in     out     source               destination         
88600  106M ACCEPT     all  --  any    any     anywhere             anywhere            state NEW,ESTABLISHED 

Chain LOGDROP (2 references)
 pkts bytes target     prot opt in     out     source               destination         
  169 32892 LOG        all  --  any    any     anywhere             anywhere            LOG level debug prefix `vrmr: DROP ' 
  169 32892 DROP       all  --  any    any     anywhere             anywhere            

Chain LOGPASS (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere            LOG level debug prefix `vrmr: PASS ' 
    0     0 ACCEPT     all  --  any    any     anywhere             anywhere            

Chain check-state (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  any    any     anywhere             anywhere            state NEW 
    0     0 DROP       all  --  any    any     anywhere             anywhere            state INVALID 
85564  108M ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED

---

### Post by bodhi.zazen on 2009-01-12
Can you post the output of :

```
iptables -L -v
```

Also, are you connecting from the local host ?

Can you show the ssh connection from the command line ?

---

### Post by The Cog on 2009-01-12
Unless I'm mistaken, this line (third line in the INPUT chain) says to accept all new connections:
> /sbin/iptables -A INPUT -p tcp --syn -j ACCEPT
All the later lines in your INPUT chain have no effect because you have already decided to accept the incoming connection.

---

### Post by havok2 on 2009-01-12
That is not the line getting any hits on my ssh or http into the box (which aren't supposed to be allowed cause they are new).  The hits are coming in on the established rule.  Look at packet count there that is all ssh and http.

---

### Post by koenn on 2009-01-12
> **The Cog said:**
> Unless I'm mistaken, this line (third line in the INPUT chain) says to accept all new connections:

All the later lines in your INPUT chain have no effect because you have already decided to accept the incoming connection.

I agree with this one.

You have ```
/sbin/iptables -A INPUT -p tcp --syn -j ACCEPT 
``` so that the incoming SYN packets are accepted, and a corresponding rule that allows SYN and ACK on OUTPUT. Therefore, you allow a tcp handshake initiated by a remote host. A successful tcp handshake means a connection is established, so all following packets in that connection are marked ESTABLISHED, and allowed by your
```
/sbin/iptables -A INPUT -p tcp -m state --state ESTABLISHED -j check-state
/sbin/iptables -A check-state -m state --state ESTABLISHED,RELATED -j ACCEPT
```

These packages don't have their SYN flag set, so without the ESTABLISHED rule, they'd be dropped.That's why it looks as if the established rule is doing to much, while actually it's a result of that  --syn ACCEPT.

---

### Post by The Cog on 2009-01-12
> **havok2 said:**
> That is not the line getting any hits on my ssh or http into the box (which aren't supposed to be allowed cause they are new).  The hits are coming in on the established rule.  Look at packet count there that is all ssh and http.

In your posting above, that rule has two hits. That will bw two new connections - two SYN packets. Any further packets for each of those two new connections will be allowed by the established rule. The SYN - the connect request - establishes the connection.

---

### Post by havok2 on 2009-01-12
Your right, that was the problem.  I only noticed the counters on the established and had not taken notice of the counter (cause it was only 1 per attempt).  Makes sense as that was just the initialization packet and the rest was the established session which would be all the data.  Thanks for the help.

---

