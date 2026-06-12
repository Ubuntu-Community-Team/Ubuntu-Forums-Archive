---
title: "What  is messing up my iptables?"
date: 2009-08-29
forum: Security
---

### Post by xgm541 on 2009-08-29
So i installed guarddog firewall
I set my samba server to allow only 192.168.1.x connections
made xampp run on startup
rebooted

now my iptables is messed up. I cannot go online unless i turn off my firewall. 

I have ushed iptables -F, no help. Reinstalled guarddog, clicked "restore defaults" no help. So for now I have uninstalled iptables all together. I want to reinstall it but i am going away from home for a few weeks. But i need remote access to my server. 

So what now?

---

### Post by bodhi.zazen on 2009-08-29
Hard to know, but you probably mis-configured guard dog or something else. DHCP and DNS come to mind.

When you can not connect to the internet look at your rules :

```
sudo iptables -L -v
```

---

### Post by xgm541 on 2009-08-30
> 
sudo iptables -L -v
[sudo] password for user: 
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    6   272 ACCEPT     all  --  lo     any     anywhere             anywhere            
    0     0 ACCEPT     all  --  eth0   any     192.168.1.65         192.168.1.255       
    0     0 logaborted  tcp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED tcp flags:RST/RST 
    0     0 ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp destination-unreachable 
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp time-exceeded 
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp parameter-problem 
   25  1950 nicfilt    all  --  any    any     anywhere             anywhere            
   25  1950 srcfilt    all  --  any    any     anywhere             anywhere            

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp destination-unreachable 
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp time-exceeded 
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp parameter-problem 
    0     0 srcfilt    all  --  any    any     anywhere             anywhere            

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    6   272 ACCEPT     all  --  any    lo      anywhere             anywhere            
    0     0 ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp destination-unreachable 
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp time-exceeded 
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp parameter-problem 
  131 12658 s1         all  --  any    any     anywhere             anywhere            

Chain f0to1 (4 references)
 pkts bytes target     prot opt in     out     source               destination         
   25  1950 logdrop    all  --  any    any     anywhere             anywhere            

Chain f1to0 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  131 12658 logdrop    all  --  any    any     anywhere             anywhere            

Chain logaborted (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 logaborted2  all  --  any    any     anywhere             anywhere            limit: avg 1/sec burst 10 
    0     0 LOG        all  --  any    any     anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 

Chain logaborted2 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `ABORTED ' 
    0     0 ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 

Chain logdrop (4 references)
 pkts bytes target     prot opt in     out     source               destination         
   75  7460 logdrop2   all  --  any    any     anywhere             anywhere            limit: avg 1/sec burst 10 
    2   173 LOG        all  --  any    any     anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 
   81  7148 DROP       all  --  any    any     anywhere             anywhere            

Chain logdrop2 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   75  7460 LOG        all  --  any    any     anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `DROPPED ' 
   75  7460 DROP       all  --  any    any     anywhere             anywhere            

Chain logreject (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 logreject2  all  --  any    any     anywhere             anywhere            limit: avg 1/sec burst 10 
    0     0 LOG        all  --  any    any     anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 
    0     0 REJECT     tcp  --  any    any     anywhere             anywhere            reject-with tcp-reset 
    0     0 REJECT     udp  --  any    any     anywhere             anywhere            reject-with icmp-port-unreachable 
    0     0 DROP       all  --  any    any     anywhere             anywhere            

Chain logreject2 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `REJECTED ' 
    0     0 REJECT     tcp  --  any    any     anywhere             anywhere            reject-with tcp-reset 
    0     0 REJECT     udp  --  any    any     anywhere             anywhere            reject-with icmp-port-unreachable 
    0     0 DROP       all  --  any    any     anywhere             anywhere            

Chain nicfilt (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   25  1950 RETURN     all  --  eth0   any     anywhere             anywhere            
    0     0 RETURN     all  --  eth0   any     anywhere             anywhere            
    0     0 RETURN     all  --  lo     any     anywhere             anywhere            
    0     0 RETURN     all  --  ppp0   any     anywhere             anywhere            
    0     0 logdrop    all  --  any    any     anywhere             anywhere            

Chain s0 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 f0to1      all  --  any    any     anywhere             192.168.1.65        
   25  1950 f0to1      all  --  any    any     anywhere             192.168.1.255       
    0     0 f0to1      all  --  any    any     anywhere             localhost           
    0     0 f0to1      all  --  any    any     anywhere             (my public IP here)
    0     0 logdrop    all  --  any    any     anywhere             anywhere            

Chain s1 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  131 12658 f1to0      all  --  any    any     anywhere             anywhere            

Chain srcfilt (2 references)
 pkts bytes target     prot opt in     out     source               destination         
   25  1950 s0         all  --  any    any     anywhere             anywhere            


there you go.

---

### Post by Rubicon_82 on 2009-08-30
It appears that you're only letting imcp traffic out through your firewall.  To solve this, I'd suggest doing either of the following, preferably A:

**A:**
*Don't restrict outgoing traffic*
If you change the default policy of the OUTPUT chain to ACCEPT, you will be able to initiate connections from your computer.  At the moment, you're only accepting established, related outgoing connections.  However, you have no rule allowing new outgoing connections to be created.

**Or, B:**
*Create rules to allow outgoing traffic based on protocol*
You will need to add rules to your output chain based on protocols you want to use.  The following rules will enable DNS, HTTP, HTTPS, SMTP, and POP3 (you may want to add additional rules based on the services that you actually use.

*Rules given in iptables-save format*

```

 -I OUTPUT -p udp -m udp --dport 53 -j ACCEPT
 -I OUTPUT -p tcp -m tcp --dport 53 -j ACCEPT

 -I OUTPUT -p tcp -m tcp --dport 80 -j ACCEPT

 -I OUTPUT -p tcp -m tcp --dport 443 -j ACCEPT

 -I OUTPUT -p tcp -m tcp --dport 25 -j ACCEPT

 -I OUTPUT -p tcp -m tcp --dport 110 -j ACCEPT

```


The rules must be added *before* your current rule: > 
0 0 s1 all -- any any anywhere anywhere 

This leads directly to your logdrop chain, resulting in packets being dropped.  This explains my use of the '-I' tag to add my rules at the start of your OUTPUT chain.  You could instead use the '-A' tag to append the rules to the end of the OUTPUT chain, but you must first remove your reference to the s1 chain.

---

