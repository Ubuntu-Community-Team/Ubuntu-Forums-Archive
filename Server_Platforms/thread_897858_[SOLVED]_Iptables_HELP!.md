---
title: "[SOLVED] Iptables HELP!"
date: 2008-08-22
forum: Server Platforms
---

### Post by de0xyrib0se on 2008-08-22
I have a server that is connected to the internet and also to a local switch via a second interface, it also has a tunnel interface tun1 (created by vpnc) and i want to forward 20 and 21 incomming on that interface to an internal machine, the IP of the interface is 192.168.99.27, i've put in the following rules but its not working when i try accessing from the other side of the tunnel, what am i dong wrong?

iptables -A PREROUTING -t nat -i tun1 -p tcp -d 192.168.99.27 --dport 21 -j DNAT --to 192.168.69.100:21
iptables -A PREROUTING -t nat -i tun1 -p tcp -d 192.168.99.27 --dport 20 -j DNAT --to 192.168.69.100:20

iptables -A INPUT -p tcp -m state --state NEW --dport 21 -i tun1 -j ACCEPT

iptables -A INPUT -p tcp -m state --state NEW --dport 20 -i tun1 -j ACCEPT

iptables -A FORWARD -i tun1 -p tcp -d 192.168.69.100 --dports 20 -j ACCEPT
iptables -A FORWARD -i tun1 -p tpc -d 192.168.69.100 --dports 21 -j ACCEPT


Full iptables config is bellow:


Chain PREROUTING (policy ACCEPT)
target prot opt source destination
DNAT icmp -- anywhere 89.XXX.XXX.XXX to:192.168.69.1
DNAT udp -- anywhere 89.XXX.XXX.XXX udp dpt:9749 to:192.168.69.96:9749
DNAT tcp -- anywhere 89.XXX.XXX.XXX tcp dpt:9749 to:192.168.69.96:9749
DNAT udp -- anywhere 89.XXX.XXX.XXX udp dpt:41577 to:192.168.69.100:41577
DNAT tcp -- anywhere 89.XXX.XXX.XXX tcp dpt:41577 to:192.168.69.100:41577
DNAT tcp -- anywhere 89.XXX.XXX.XXX tcp dpt:15601 to:192.168.69.100:15601
DNAT udp -- anywhere 89.XXX.XXX.XXX udp dpt:15601 to:192.168.69.100:15601
DNAT tcp -- anywhere 89.XXX.XXX.XXX tcp dpt:12428 to:192.168.69.100:12428
DNAT udp -- anywhere 89.XXX.XXX.XXX udp dpt:12428 to:192.168.69.100:12428
DNAT tcp -- anywhere 89.XXX.XXX.XXX tcp dpt:7711 to:192.168.69.96:7711
DNAT udp -- anywhere 89.XXX.XXX.XXX udp dpt:7711 to:192.168.69.96:7711
DNAT tcp -- anywhere 89.XXX.XXX.XXX tcp dpt:www to:192.168.69.97:80
DNAT udp -- anywhere 89.XXX.XXX.XXX udp dpt:www to:192.168.69.97:80
DNAT tcp -- anywhere 89.XXX.XXX.XXX tcp dpt:8069 to:192.168.69.97:80
DNAT udp -- anywhere 89.XXX.XXX.XXX udp dpt:8069 to:192.168.69.97:80
DNAT tcp -- anywhere 89.XXX.XXX.XXX tcp dpt:12428 to:192.168.69.100:12428
DNAT udp -- anywhere 89.XXX.XXX.XXX udp dpt:12428 to:192.168.69.100:12428
TRIGGER 0 -- anywhere 89.XXX.XXX.XXX TRIGGER type:dnat match:0 relate:0
DNAT tcp -- anywhere 192.168.99.27 tcp dpt:ftp-data to:192.168.69.100:20
DNAT tcp -- anywhere 192.168.99.27 tcp dpt:ftp to:192.168.69.100:21

Chain POSTROUTING (policy ACCEPT)
target prot opt source destination
MASQUERADE 0 -- anywhere anywhere
RETURN 0 -- anywhere anywhere PKTTYPE = broadcast
MASQUERADE 0 -- 192.168.69.0/24 192.168.69.0/24
MASQUERADE 0 -- anywhere anywhere
MASQUERADE 0 -- anywhere anywhere
MASQUERADE 0 -- anywhere anywhere

Chain OUTPUT (policy ACCEPT)
target prot opt source destination

Chain INPUT (policy ACCEPT)
target prot opt source destination
ACCEPT 0 -- 192.168.1.0/24 anywhere
ACCEPT 0 -- anywhere anywhere state RELATED,ESTABLISHED
ACCEPT tcp -- anywhere anywhere tcp dpt:1723
ACCEPT gre -- anywhere anywhere
DROP udp -- anywhere anywhere udp dpt:route
DROP udp -- anywhere anywhere udp dpt:route
ACCEPT udp -- anywhere anywhere udp dpt:route
DROP icmp -- anywhere anywhere
DROP igmp -- anywhere anywhere
ACCEPT 0 -- anywhere anywhere state NEW
logaccept 0 -- anywhere anywhere state NEW
DROP 0 -- anywhere anywhere
ACCEPT tcp -- anywhere anywhere state NEW tcp dpt:ftp
ACCEPT tcp -- anywhere anywhere state NEW tcp dpt:ftp-data

Chain FORWARD (policy ACCEPT)
target prot opt source destination
TCPMSS tcp -- anywhere anywhere tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU
ACCEPT 0 -- 192.168.1.0/24 anywhere
ACCEPT 0 -- anywhere 192.168.1.0/24
ACCEPT gre -- 192.168.69.0/24 anywhere
ACCEPT tcp -- 192.168.69.0/24 anywhere tcp dpt:1723
ACCEPT 0 -- anywhere anywhere
logdrop 0 -- anywhere anywhere state INVALID
TCPMSS tcp -- anywhere anywhere tcp flags:SYN,RST/SYN tcpmss match 1461:65535 TCPMSS set 1460
lan2wan 0 -- anywhere anywhere
ACCEPT 0 -- anywhere anywhere state RELATED,ESTABLISHED
ACCEPT udp -- anywhere PC01.mydomain.local udp dpt:9749
ACCEPT tcp -- anywhere PC01.mydomain.local tcp dpt:9749
ACCEPT udp -- anywhere PC02.mydomain.local udp dpt:41577
ACCEPT tcp -- anywhere PC02.mydomain.local tcp dpt:41577
ACCEPT tcp -- anywhere PC02.mydomain.local tcp dpt:15601
ACCEPT udp -- anywhere PC02.mydomain.local udp dpt:15601
ACCEPT tcp -- anywhere PC02.mydomain.local tcp dpt:12428
ACCEPT udp -- anywhere PC02.mydomain.local udp dpt:12428
ACCEPT tcp -- anywhere PC01.mydomain.local tcp dpt:7711
ACCEPT udp -- anywhere PC01.mydomain.local udp dpt:7711
ACCEPT tcp -- anywhere 192.168.69.97 tcp dpt:www
ACCEPT udp -- anywhere 192.168.69.97 udp dpt:www
ACCEPT tcp -- anywhere 192.168.69.97 tcp dpt:www
ACCEPT udp -- anywhere 192.168.69.97 udp dpt:www
ACCEPT tcp -- anywhere PC02.mydomain.local tcp dpt:12428
ACCEPT udp -- anywhere PC02.mydomain.local udp dpt:12428
TRIGGER 0 -- anywhere anywhere TRIGGER type:in match:0 relate:0
trigger_out 0 -- anywhere anywhere
ACCEPT 0 -- anywhere anywhere state NEW
DROP 0 -- anywhere anywhere
ACCEPT 0 -- anywhere anywhere
ACCEPT 0 -- anywhere anywhere
ACCEPT 0 -- anywhere anywhere
ACCEPT 0 -- anywhere anywhere

Chain OUTPUT (policy ACCEPT)
target prot opt source destination
ACCEPT 0 -- anywhere 192.168.1.0/24

Chain lan2wan (1 references)
target prot opt source destination

Chain logaccept (1 references)
target prot opt source destination
ACCEPT 0 -- anywhere anywhere

Chain logdrop (1 references)
target prot opt source destination
DROP 0 -- anywhere anywhere

Chain logreject (0 references)
target prot opt source destination
REJECT tcp -- anywhere anywhere tcp reject-with tcp-reset

Chain trigger_out (1 references)
target prot opt source destination

---

