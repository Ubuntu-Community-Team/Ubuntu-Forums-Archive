---
title: "UFW woes - filtering legitimate packets"
date: 2015-11-01
forum: Security
---

### Post by damatta2 on 2015-11-01
Hello.

I'm using trusy tahr as the latest lubuntu freezes my laptop all the time.
Regardless to what version I use, UFW when configured with GUFW keeps blocking certain packets from, I believe, already established connections.
This results in webpages not loading, which is a pain because it happens basically all the time.
MY syslog gets filled up with this:
```
Nov  1 20:50:40 desktop kernel: [ 1556.068124] [UFW BLOCK] IN=wlan0 OUT= MAC=5c:c9:d3:51:20:45:f8:e9:03:9c:d6:71:08:00 SRC=91.189.89.153 DST=192.168.25.7 LEN=89 TOS=0x04 PREC=0x00 TTL=52 ID=11588 DF PROTO=TCP SPT=443 DPT=45564 WINDOW=54 RES=0x00 ACK PSH URGP=0 
Nov  1 20:51:00 desktop kernel: [ 1575.963926] [UFW BLOCK] IN=wlan0 OUT= MAC=5c:c9:d3:51:20:45:f8:e9:03:9c:d6:71:08:00 SRC=91.189.89.153 DST=192.168.25.7 LEN=89 TOS=0x04 PREC=0x00 TTL=52 ID=11589 DF PROTO=TCP SPT=443 DPT=45564 WINDOW=54 RES=0x00 ACK PSH URGP=0 
Nov  1 20:51:42 desktop kernel: [ 1617.596353] [UFW BLOCK] IN=wlan0 OUT= MAC=5c:c9:d3:51:20:45:f8:e9:03:9c:d6:71:08:00 SRC=91.189.89.153 DST=192.168.25.7 LEN=89 TOS=0x04 PREC=0x00 TTL=52 ID=11590 DF PROTO=TCP SPT=443 DPT=45564 WINDOW=54 RES=0x00 ACK PSH URGP=0 


```
 As you can see this basically blocks youtube videos from loading properly.
All packets have URGP=0, at least.
Some people online say there is a problem with the firewall handling established connections.
Could this be related to conntrack? Are you experiencing similar issues? Is there something I can do to stay protected without losing compatibility?
I believe changing iptables rules will not do anything.
Thank you in advance.

FYI my iptables rule as set by GUFW:
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-input  all  --  0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:137
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:138
ufw-skip-to-policy-input  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:139
ufw-skip-to-policy-input  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:445
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:67
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:68
ufw-skip-to-policy-input  all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 3
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 4
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 11
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 12
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8
ufw-user-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0            ctstate INVALID
DROP       all  --  0.0.0.0/0            0.0.0.0/0            ctstate INVALID
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 3
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 4
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 11
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 12
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
ufw-not-local  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     udp  --  0.0.0.0/0            224.0.0.251          udp dpt:5353
ACCEPT     udp  --  0.0.0.0/0            239.255.255.250      udp dpt:1900
ufw-user-input  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ufw-user-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW ALLOW] "

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ctstate INVALID limit: avg 3/min burst 10
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type LOCAL
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type MULTICAST
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-track-forward (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            ctstate NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            ctstate NEW

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
DROP       all  --  0.0.0.0/0            224.0.0.1           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:35622
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:35622

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 5 LOG flags 0 level 4 prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination 

```

---

