---
title: "Iptables help"
date: 2009-04-26
forum: Security
---

### Post by yeleek on 2009-04-26
Hi,

In this laptop I have one 10/100 Nic and one wifi connection, at times either of them can be connected to the network.

How can i configure IPtables so that any traffic is allowed out, nothing is allowed in (other than std stateful firewall replies), no icmp and that the fw logs any attempts to connect to the laptop?

V.grateful for any advice.

Thanks

---

### Post by Titan8990 on 2009-04-26
sudo iptables -P INPUT DROP
sudo iptables -P OUTPUT ACCEPT
sudo iptables -F


Although, for your purposes I would recommend a packet analyzer such as tcpdump or wireshark.

---

### Post by bodhi.zazen on 2009-04-26
See also : [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

If yo uset the input policy to DROP , you will need to specify the traffic you wish to allow in (such as related and established connections).

---

### Post by yeleek on 2009-04-28
Hi,
Thanks for replies - I've tried to create an iptables config as per below (on a fresh install of Jaunty)

Chain INPUT (policy DROP 903 packets, 71056 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   97 14278 LOG        all  --  any    any     anywhere             anywhere            limit: avg 5/min burst 5 LOG level debug prefix `iptables denied: ' 
 3304 2165K existing-connections  all  --  any    any     anywhere             anywhere            
  903 71056 allowed    all  --  any    any     anywhere             anywhere            

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 2507 packets, 369K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain allowed (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain existing-connections (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  lo     any     anywhere             anywhere            
 2401 2094K ACCEPT     all  --  any    any     anywhere             anywhere            state ESTABLISHED 
    0     0 ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED 


Is this right?  Because I can't find any logging going on.

For the record I used this [http://www.physics.umd.edu/pnce/user-docs/Linux/firewall.html](http://www.physics.umd.edu/pnce/user-docs/Linux/firewall.html)

Thank you

---

### Post by yeleek on 2009-04-28
Scrap that - found it in syslog instead of messages....

How do the rules look?  Is it ok?  Nmap can't seem to get anything.

Thanks

---

