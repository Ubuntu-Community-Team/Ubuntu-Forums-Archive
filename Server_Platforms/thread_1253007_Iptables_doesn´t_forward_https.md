---
title: "Iptables doesn´t forward https"
date: 2009-08-29
forum: Server Platforms
---

### Post by braiamp on 2009-08-29
So I have a newer Ubuntu Sever 9.04, actualy working at NAT/Firewall/Cache Proxy, using Iptables, squid and dansguardian. But if i get to a https page it dosen´t work and this is because iptables drop packets that are for 443 port. I try to many forms to get that teh port work, but actualy nothing work.

Here is a flush for my aplied iptables rules ( i ran iptables -S command):

-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-A INPUT -s 192.168.2.0/24 -i eth1 -p tcp -m tcp -j ACCEPT
-A INPUT -i eth1 -p tcp -m multiport --dports 123 -m state --state NEW -j ACCEPT
-A INPUT -i eth1 -p tcp -m multiport --dports 80 -m state --state NEW -j ACCEPT
-A INPUT -i eth1 -p tcp -m multiport --dports 2222 -m state --state NEW -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A INPUT -p tcp -m tcp --dport 2222 -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH --rsource -j LOG --log-prefix "SSH_brute_force "
-A INPUT -p tcp -m tcp --dport 2222 -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH --rsource -j DROP
-A INPUT -i lo -j ACCEPT
-A INPUT -j LOG
-A INPUT -i eth1 -p tcp -m multiport --dports 443 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth1 -p tcp -m multiport --dports 443 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth1 -p tcp -m multiport --dports 443 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth1 -p tcp -m multiport --dports 443 -j ACCEPT
-A FORWARD -s 192.168.2.0/24 -d 192.168.1.2/32 -i eth1 -p tcp -m tcp -j ACCEPT
-A FORWARD -s 192.168.2.0/24 -i eth1 -p tcp -m tcp -j ACCEPT
-A FORWARD -i eth1 -o eth0 -p tcp -m multiport --dports 443,21,25,993,110,465,1863 -m state --state NEW -j ACCEPT
-A FORWARD -s 192.168.2.0/24 -d 192.168.1.1/32 -j ACCEPT
-A FORWARD -i eth1 -o eth0 -p tcp -m multiport --dports 443,21,25,993,110,465,1863 -m state --state NEW -j ACCEPT
-A FORWARD -i eth1 -o eth0 -p tcp -m multiport --dports 443 -m state --state NEW -j ACCEPT
-A FORWARD -i eth1 -o eth0 -p tcp -m multiport --dports 443 -m state --state NEW,RELATED -j ACCEPT
-A FORWARD -i eth1 -o eth0 -p tcp -m multiport --dports 443 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -i eth1 -o eth0 -p tcp -m multiport --dports 21 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -s 10.0.0.0/24 -i eth1 -p tcp -m tcp --dport 20:21 -j ACCEPT
-A FORWARD -s 10.0.0.0/24 -i eth1 -p udp -m udp --dport 20:21 -j ACCEPT
-A FORWARD -s 192.168.2.0/24 -i eth1 -p tcp -m tcp --dport 20:21 -j ACCEPT
-A FORWARD -s 192.168.2.0/24 -i eth1 -p udp -m udp --dport 20:21 -j ACCEPT
-A FORWARD -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
-A FORWARD -p tcp -m tcp --dport 1024:65535 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -p icmp -j ACCEPT
-A FORWARD -j LOG
-A FORWARD -j LOG
-A FORWARD -i eth1 -p tcp -m tcp --dport 443 -j ACCEPT
-A FORWARD -i eth1 -p tcp -m tcp --dport 443 -j ACCEPT
-A FORWARD -i eth1 -p tcp -m tcp --dport 443 -j ACCEPT
-A FORWARD -i eth1 -p tcp -m tcp --dport 443 -j ACCEPT
-A OUTPUT -o eth1 -p tcp -m multiport --dports 443 -j ACCEPT
-A OUTPUT -o eth1 -p tcp -m multiport --dports 443 -j ACCEPT
-A OUTPUT -o eth1 -p tcp -m tcp --dport 443 -j ACCEPT
-A OUTPUT -o eth1 -p tcp -m tcp --dport 443 -j ACCEPT

Thanks.

---

### Post by drave on 2009-09-01
there's an ALL jump to LOG right in front of the 443 ports

---

### Post by braiamp on 2009-09-11
i gotit here is my dump:
 
-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-N bad_packets
-N bad_tcp_packets
-N icmp_packets
-N tcp_inbound
-N tcp_outbound
-N udp_inbound
-N udp_outbound
-A INPUT -i lo -j ACCEPT
-A INPUT -j bad_packets
-A INPUT -d 224.0.0.1/32 -j DROP
-A INPUT -s 192.168.2.0/24 -i eth1 -j ACCEPT
-A INPUT -d 192.168.2.255/32 -i eth1 -j ACCEPT
-A INPUT -i eth1 -p udp -m udp --sport 68 --dport 67 -j ACCEPT
-A INPUT -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p tcp -j tcp_inbound
-A INPUT -i eth0 -p udp -j udp_inbound
-A INPUT -i eth0 -p icmp -j icmp_packets
-A INPUT -p udp -m udp --dport 51413 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 51413 -j ACCEPT
-A INPUT -j LOG --log-prefix "fp=INPUT:99 a=DROP "
-A INPUT -m pkttype --pkt-type broadcast -j DROP
-A FORWARD -j bad_packets
-A FORWARD -i eth1 -p tcp -j tcp_outbound
-A FORWARD -i eth1 -p udp -j udp_outbound
-A FORWARD -i eth1 -j ACCEPT
-A FORWARD -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -d 192.168.2.5/32 -i eth0 -p udp -m udp --dport 19118 -j ACCEPT
-A FORWARD -d 192.168.2.5/32 -i eth0 -p tcp -m tcp --dport 19118 -j ACCEPT
-A FORWARD -j LOG --log-prefix "fp=FORWARD:99 a=DROP "
-A OUTPUT -p icmp -m state --state INVALID -j DROP
-A OUTPUT -s 127.0.0.1/32 -j ACCEPT
-A OUTPUT -o lo -j ACCEPT
-A OUTPUT -s 192.168.2.1/32 -j ACCEPT
-A OUTPUT -o eth1 -j ACCEPT
-A OUTPUT -o eth0 -j ACCEPT
-A OUTPUT -j LOG --log-prefix "fp=OUTPUT:99 a=DROP "
-A bad_packets -s 192.168.2.0/24 -i eth0 -j LOG --log-prefix "fp=bad_packets:2 a=DROP "
-A bad_packets -s 192.168.2.0/24 -i eth0 -j DROP
-A bad_packets -m state --state INVALID -j LOG --log-prefix "fp=bad_packets:1 a=DROP "
-A bad_packets -m state --state INVALID -j DROP
-A bad_packets -p tcp -j bad_tcp_packets
-A bad_packets -j RETURN
-A bad_tcp_packets -i eth1 -p tcp -j RETURN
-A bad_tcp_packets -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j LOG --log-prefix "fp=bad_tcp_packets:1 a=DROP "
-A bad_tcp_packets -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j LOG --log-prefix "fp=bad_tcp_packets:2 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,PSH,ACK,URG -j LOG --log-prefix "fp=bad_tcp_packets:3 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,PSH,ACK,URG -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,PSH,URG -j LOG --log-prefix "fp=bad_tcp_packets:4 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,PSH,URG -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,ACK,URG -j LOG --log-prefix "fp=bad_tcp_packets:5 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,ACK,URG -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j LOG --log-prefix "fp=bad_tcp_packets:6 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j LOG --log-prefix "fp=bad_tcp_packets:7 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j DROP
-A bad_tcp_packets -p tcp -j RETURN
-A icmp_packets -p icmp -f -j LOG --log-prefix "fp=icmp_packets:1 a=DROP "
-A icmp_packets -p icmp -f -j DROP
-A icmp_packets -s ! 192.168.2.0/24 -p icmp -m icmp --icmp-type 8 -j DROP
-A icmp_packets -p icmp -m icmp --icmp-type 8 -j LOG --log-prefix "fp=icmp_packets:2 a=ACCEPT "
-A icmp_packets -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A icmp_packets -p icmp -m icmp --icmp-type 8 -j DROP
-A icmp_packets -p icmp -m icmp --icmp-type 11 -j ACCEPT
-A icmp_packets -p icmp -j RETURN
-A tcp_inbound -p tcp -m tcp --dport 80 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 443 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 21 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --sport 20 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 62000:64000 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 25 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 110 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 143 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 995 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 993 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 6891:6900 -j ACCEPT
-A tcp_inbound -p tcp -j RETURN
-A tcp_outbound -p tcp -j ACCEPT
-A udp_inbound -p udp -m udp --dport 137 -j DROP
-A udp_inbound -p udp -m udp --dport 138 -j DROP
-A udp_inbound -p udp -m udp --dport 123 -j ACCEPT
-A udp_inbound -p udp -m udp --dport 53 -j ACCEPT
-A udp_inbound -p udp -m udp --sport 67 --dport 68 -j ACCEPT
-A udp_inbound -p udp -j RETURN
-A udp_outbound -p udp -j ACCEPT
 
Thank u :D

---

### Post by braiamp on 2009-09-11
> **braiamp said:**
> i gotit here is my dump:
 
-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-N bad_packets
-N bad_tcp_packets
-N icmp_packets
-N tcp_inbound
-N tcp_outbound
-N udp_inbound
-N udp_outbound
-A INPUT -i lo -j ACCEPT
-A INPUT -j bad_packets
-A INPUT -d 224.0.0.1/32 -j DROP
-A INPUT -s 192.168.2.0/24 -i eth1 -j ACCEPT
-A INPUT -d 192.168.2.255/32 -i eth1 -j ACCEPT
-A INPUT -i eth1 -p udp -m udp --sport 68 --dport 67 -j ACCEPT
-A INPUT -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p tcp -j tcp_inbound
-A INPUT -i eth0 -p udp -j udp_inbound
-A INPUT -i eth0 -p icmp -j icmp_packets
-A INPUT -p udp -m udp --dport 51413 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 51413 -j ACCEPT
-A INPUT -j LOG --log-prefix "fp=INPUT:99 a=DROP "
-A INPUT -m pkttype --pkt-type broadcast -j DROP
-A FORWARD -j bad_packets
-A FORWARD -i eth1 -p tcp -j tcp_outbound
-A FORWARD -i eth1 -p udp -j udp_outbound
-A FORWARD -i eth1 -j ACCEPT
-A FORWARD -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -d 192.168.2.5/32 -i eth0 -p udp -m udp --dport 19118 -j ACCEPT
-A FORWARD -d 192.168.2.5/32 -i eth0 -p tcp -m tcp --dport 19118 -j ACCEPT
-A FORWARD -j LOG --log-prefix "fp=FORWARD:99 a=DROP "
-A OUTPUT -p icmp -m state --state INVALID -j DROP
-A OUTPUT -s 127.0.0.1/32 -j ACCEPT
-A OUTPUT -o lo -j ACCEPT
-A OUTPUT -s 192.168.2.1/32 -j ACCEPT
-A OUTPUT -o eth1 -j ACCEPT
-A OUTPUT -o eth0 -j ACCEPT
-A OUTPUT -j LOG --log-prefix "fp=OUTPUT:99 a=DROP "
-A bad_packets -s 192.168.2.0/24 -i eth0 -j LOG --log-prefix "fp=bad_packets:2 a=DROP "
-A bad_packets -s 192.168.2.0/24 -i eth0 -j DROP
-A bad_packets -m state --state INVALID -j LOG --log-prefix "fp=bad_packets:1 a=DROP "
-A bad_packets -m state --state INVALID -j DROP
-A bad_packets -p tcp -j bad_tcp_packets
-A bad_packets -j RETURN
-A bad_tcp_packets -i eth1 -p tcp -j RETURN
-A bad_tcp_packets -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j LOG --log-prefix "fp=bad_tcp_packets:1 a=DROP "
-A bad_tcp_packets -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j LOG --log-prefix "fp=bad_tcp_packets:2 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,PSH,ACK,URG -j LOG --log-prefix "fp=bad_tcp_packets:3 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,PSH,ACK,URG -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,PSH,URG -j LOG --log-prefix "fp=bad_tcp_packets:4 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,PSH,URG -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,ACK,URG -j LOG --log-prefix "fp=bad_tcp_packets:5 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,ACK,URG -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j LOG --log-prefix "fp=bad_tcp_packets:6 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j LOG --log-prefix "fp=bad_tcp_packets:7 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j DROP
-A bad_tcp_packets -p tcp -j RETURN
-A icmp_packets -p icmp -f -j LOG --log-prefix "fp=icmp_packets:1 a=DROP "
-A icmp_packets -p icmp -f -j DROP
-A icmp_packets -s ! 192.168.2.0/24 -p icmp -m icmp --icmp-type 8 -j DROP
-A icmp_packets -p icmp -m icmp --icmp-type 8 -j LOG --log-prefix "fp=icmp_packets:2 a=ACCEPT "
-A icmp_packets -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A icmp_packets -p icmp -m icmp --icmp-type 8 -j DROP
-A icmp_packets -p icmp -m icmp --icmp-type 11 -j ACCEPT
-A icmp_packets -p icmp -j RETURN
-A tcp_inbound -p tcp -m tcp --dport 80 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 443 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 21 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --sport 20 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 62000:64000 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 25 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 110 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 143 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 995 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 993 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 6891:6900 -j ACCEPT
-A tcp_inbound -p tcp -j RETURN
-A tcp_outbound -p tcp -j ACCEPT
-A udp_inbound -p udp -m udp --dport 137 -j DROP
-A udp_inbound -p udp -m udp --dport 138 -j DROP
-A udp_inbound -p udp -m udp --dport 123 -j ACCEPT
-A udp_inbound -p udp -m udp --dport 53 -j ACCEPT
-A udp_inbound -p udp -m udp --sport 67 --dport 68 -j ACCEPT
-A udp_inbound -p udp -j RETURN
-A udp_outbound -p udp -j ACCEPT
 
Thank u :D
 
i use a sample script from [https://help.ubuntu.com](https://help.ubuntu.com)

---

