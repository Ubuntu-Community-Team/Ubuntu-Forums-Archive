---
title: "PIA on IPv6 leaks. Secure?"
date: 2016-02-15
forum: Security
---

### Post by mikodo on 2016-02-15
I was hoping someone would analyze what my VPN, Private Internet Access (PIA), is doing with IPv6. 

In Firefox I set in about:config **> network.dns.disableIPv6** > Set it to** true**

Does this output indicate PIA is rejecting IPv6 safely "by itself"? I don't know how much I need to show here. It does mention PIA IPV6LEAK_OUTPUT_RULES:```
[B]
sudo ufw show raw

[/B]IPV6:
Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
     113    26161 ufw6-before-logging-input  all      *      *       ::/0                 ::/0                
     113    26161 ufw6-before-input  all      *      *       ::/0                 ::/0                
       0        0 ufw6-after-input  all      *      *       ::/0                 ::/0                
       0        0 ufw6-after-logging-input  all      *      *       ::/0                 ::/0                
       0        0 ufw6-reject-input  all      *      *       ::/0                 ::/0                
       0        0 ufw6-track-input  all      *      *       ::/0                 ::/0                

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ufw6-before-logging-forward  all      *      *       ::/0                 ::/0                
       0        0 ufw6-before-forward  all      *      *       ::/0                 ::/0                
       0        0 ufw6-after-forward  all      *      *       ::/0                 ::/0                
       0        0 ufw6-after-logging-forward  all      *      *       ::/0                 ::/0                
       0        0 ufw6-reject-forward  all      *      *       ::/0                 ::/0                
       0        0 ufw6-track-forward  all      *      *       ::/0                 ::/0                

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
      ** 2      152 PIA_IPV6LEAK_OUTPUT_RULES  all      *      *       ::/0                 ::/0   **             
     123    26869 ufw6-before-logging-output  all      *      *       ::/0                 ::/0                
     123    26869 ufw6-before-output  all      *      *       ::/0                 ::/0                
      25     3634 ufw6-after-output  all      *      *       ::/0                 ::/0                
      25     3634 ufw6-after-logging-output  all      *      *       ::/0                 ::/0                
      25     3634 ufw6-reject-output  all      *      *       ::/0                 ::/0                
      25     3634 ufw6-track-output  all      *      *       ::/0                 ::/0                

**Chain PIA_IPV6LEAK_OUTPUT_RULES (1 references)**
    pkts      bytes target     prot opt in     out     source               destination         
       2      152 DROP       all      *      *       ::/0                 ::/0                
       0        0 DROP       all      *      *       ::/0                 ::/0                

Chain ufw6-after-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw6-after-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ufw6-skip-to-policy-input  udp      *      *       ::/0                 ::/0                 udp dpt:137
       0        0 ufw6-skip-to-policy-input  udp      *      *       ::/0                 ::/0                 udp dpt:138
       0        0 ufw6-skip-to-policy-input  tcp      *      *       ::/0                 ::/0                 tcp dpt:139
       0        0 ufw6-skip-to-policy-input  tcp      *      *       ::/0                 ::/0                 tcp dpt:445
       0        0 ufw6-skip-to-policy-input  udp      *      *       ::/0                 ::/0                 udp dpt:546
       0        0 ufw6-skip-to-policy-input  udp      *      *       ::/0                 ::/0                 udp dpt:547

Chain ufw6-after-logging-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all      *      *       ::/0                 ::/0                 limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw6-after-logging-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all      *      *       ::/0                 ::/0                 limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw6-after-logging-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw6-after-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw6-before-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DROP       all      *      *       ::/0                 ::/0                 rt type:0 segsleft:0
       0        0 ACCEPT     all      *      *       ::/0                 ::/0                 ctstate RELATED,ESTABLISHED
       0        0 ACCEPT     icmpv6    *      *       ::/0                 ::/0                 ipv6-icmptype 1
       0        0 ACCEPT     icmpv6    *      *       ::/0                 ::/0                 ipv6-icmptype 2
       0        0 ACCEPT     icmpv6    *      *       ::/0                 ::/0                 ipv6-icmptype 3
       0        0 ACCEPT     icmpv6    *      *       ::/0                 ::/0                 ipv6-icmptype 4
       0        0 ACCEPT     icmpv6    *      *       ::/0                 ::/0                 ipv6-icmptype 128
       0        0 ufw6-user-forward  all      *      *       ::/0                 ::/0                

Chain ufw6-before-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
      97    23171 ACCEPT     all      lo     *       ::/0                 ::/0                
       0        0 DROP       all      *      *       ::/0                 ::/0                 rt type:0 segsleft:0
       0        0 ACCEPT     icmpv6    *      *       ::/0                 ::/0                 ipv6-icmptype 135 HL match HL == 255
       0        0 ACCEPT     icmpv6    *      *       ::/0                 ::/0                 ipv6-icmptype 136 HL match HL == 255
       0        0 ACCEPT     icmpv6    *      *       ::/0                 ::/0                 ipv6-icmptype 133 HL match HL == 255
       0        0 ACCEPT     icmpv6    *      *       ::/0                 ::/0                 ipv6-icmptype 134 HL match HL == 255
       0        0 ACCEPT     all      *      *       ::/0                 ::/0                 ctstate RELATED,ESTABLISHED
       0        0 ACCEPT     icmpv6    *      *       fe80::/10            ::/0                 ipv6-icmptype 129
       0        0 ufw6-logging-deny  all      *      *       ::/0                 ::/0                 ctstate INVALID
       0        0 DROP       all      *      *       ::/0                 ::/0                 ctstate INVALID
       0        0 ACCEPT     icmpv6    *      *       ::/0                 ::/0                 ipv6-icmptype 1
       0        0 ACCEPT     icmpv6    *      *       ::/0                 ::/0                 ipv6-icmptype 2
       0        0 ACCEPT     icmpv6    *      *       ::/0                 ::/0                 ipv6-icmptype 3
       0        0 ACCEPT     icmpv6    *      *       ::/0                 ::/0                 ipv6-icmptype 4
       0        0 ACCEPT     icmpv6    *      *       ::/0                 ::/0                 ipv6-icmptype 128
       0        0 ACCEPT     udp      *      *       fe80::/10            fe80::/10            udp spt:547 dpt:546
      16     2990 ACCEPT     udp      *      *       ::/0                 ff02::fb             udp dpt:5353
       0        0 ACCEPT     udp      *      *       ::/0                 ff02::f              udp dpt:1900
       0        0 ufw6-user-input  all      *      *       ::/0                 ::/0                

Chain ufw6-before-logging-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw6-before-logging-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw6-before-logging-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw6-before-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
      97    23171 ACCEPT     all      *      lo      ::/0                 ::/0                
       0        0 DROP       all      *      *       ::/0                 ::/0                 rt type:0 segsleft:0
       1       64 ACCEPT     icmpv6    *      *       ::/0                 ::/0                 ipv6-icmptype 135 HL match HL == 255
       0        0 ACCEPT     icmpv6    *      *       ::/0                 ::/0                 ipv6-icmptype 136 HL match HL == 255
       0        0 ACCEPT     all      *      *       ::/0                 ::/0                 ctstate RELATED,ESTABLISHED
      25     3634 ufw6-user-output  all      *      *       ::/0                 ::/0                

Chain ufw6-logging-allow (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all      *      *       ::/0                 ::/0                 limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW ALLOW] "

Chain ufw6-logging-deny (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 RETURN     all      *      *       ::/0                 ::/0                 ctstate INVALID limit: avg 3/min burst 10
       0        0 LOG        all      *      *       ::/0                 ::/0                 limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw6-reject-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw6-reject-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw6-reject-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw6-skip-to-policy-forward (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DROP       all      *      *       ::/0                 ::/0                

Chain ufw6-skip-to-policy-input (6 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DROP       all      *      *       ::/0                 ::/0                

Chain ufw6-skip-to-policy-output (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all      *      *       ::/0                 ::/0                

Chain ufw6-track-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw6-track-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw6-track-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp      *      *       ::/0                 ::/0                 ctstate NEW
      16     2990 ACCEPT     udp      *      *       ::/0                 ::/0                 ctstate NEW

Chain ufw6-user-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw6-user-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw6-user-limit (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all      *      *       ::/0                 ::/0                 limit: avg 3/min burst 5 LOG flags 0 level 4 prefix "[UFW LIMIT BLOCK] "
       0        0 REJECT     all      *      *       ::/0                 ::/0                 reject-with icmp6-port-unreachable

Chain ufw6-user-limit-accept (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all      *      *       ::/0                 ::/0                

Chain ufw6-user-logging-forward (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw6-user-logging-input (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw6-user-logging-output (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw6-user-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

```

---

