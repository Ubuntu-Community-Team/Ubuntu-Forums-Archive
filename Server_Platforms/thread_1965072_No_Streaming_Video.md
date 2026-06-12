---
title: "No Streaming Video"
date: 2012-04-25
forum: Server Platforms
---

### Post by Thilips on 2012-04-25
Ok, I feel a little embarassed since I have been working with Ubuntu since I started with Linux years ago though I usually do not work with Ubuntu Server but Centos. That being said here is my issue:
I setup Ubuntu Server 10.04 between my wireless router and ISP modem
to route all traffic through my remote proxy server which is in 
the U.S (I will be living in Europe for awhile in a company 
apartment). The Ubuntu Server is acting as a DHCP server to my 
wireless router and a router routing all traffic to my proxy. It's 
functioning properly except for a few https sites (namely my 
companies webmail) and, the biggest problem and reason for this 
thread Netflix and Amazon. It seems I cannot stream video from these 
two sites. I can receive video from "Youtube" and "Hulu" just not 
Netflix and Amazon. Now before I started using the Ubuntu Server I 
was able to place the proxy settings in whatever web browser I was 
using and they worked but now that I changed settings in the proxy to 
transparent and started using the Ubuntu server it does not work. The 
proxy settings I have edited in the remote server (which is Centos) 
and IPTABLES rules I in the Ubuntu serve are below. All help an ideas
are appreciated experienced and novice alike since you learn from
ideas and that's what Linux us about. Thanks.

IPTABLES SETTINGS:
pkts bytes target prot opt in out source destination 

0 0 ACCEPT udp -- any any anywhere anywhere 
multiport dports 1024:3000 
0 0 ACCEPT tcp -- any any anywhere anywhere 
multiport dports https,nntps 
0 0 ACCEPT tcp -- any any anywhere anywhere 
multiport dports 7070,8000,8001,rtsp 
0 0 ACCEPT udp -- any any anywhere anywhere 
multiport dports 9000:9001 

Chain FORWARD (policy ACCEPT 189K packets, 39M bytes)
pkts bytes target prot opt in out source destination 

1520K 1960M ACCEPT all -- eth0 any anywhere anywhere 
0 0 ACCEPT all -- eth0 any anywhere anywhere 
0 0 ACCEPT all -- eth0 any anywhere anywhere 
0 0 ACCEPT all -- eth0 any anywhere anywhere
0 0 ACCEPT tcp -- eth1 any anywhere {IP Addr. of xxx.blahblahblah.com SQUID server} tcp dpt:6402 
0 0 ACCEPT tcp -- eth0 any anywhere {IP Addr. of xxx.blahblahblah.com SQUID server} tcp dpt:6402 
720K 51M ACCEPT tcp -- any any anywhere xxx.blahblahblah.com tcp dpt:6402

-P INPUT ACCEPT -c 287103 251434980
-P FORWARD ACCEPT -c 189430 38902607
-P OUTPUT ACCEPT -c 44355 8591199
-A INPUT -p udp -m multiport --dports 1024:3000 -c 0 0 -j ACCEPT 
-A INPUT -p tcp -m multiport --dports 443,563 -c 0 0 -j ACCEPT 
-A INPUT -p tcp -m multiport --dports 7070,8000,8001,554 -c 0 0 -j ACCEPT 
-A INPUT -p udp -m multiport --dports 9000:9001 -c 0 0 -j ACCEPT 
-A FORWARD -i eth0 -c 1519579 1960182111 -j ACCEPT 
-A FORWARD -i eth0 -c 0 0 -j ACCEPT 
-A FORWARD -i eth0 -c 0 0 -j ACCEPT 
-A FORWARD -i eth0 -c 0 0 -j ACCEPT 
-A FORWARD -d {IP Addr. of xxx.blahblahblah.com SQUID server}/32 -i eth1 -p tcp -m tcp --dport 6402 -c 0 0 -j ACCEPT 
-A FORWARD -d {IP Addr. of xxx.blahblahblah.com SQUID server}/32 -i eth0 -p tcp -m tcp --dport 6402 -c 0 0 -j ACCEPT 
-A FORWARD -d {IP Addr. of xxx.blahblahblah.com SQUID server}/32 -p tcp -m tcp --dport 6402 -c 719721 51210240 -j ACCEPT


SQUID PROXY SETTINGS (that where edited):
acl SSL_ports port 443 563
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 # https
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl Safe_ports port 7070
acl Safe_ports port 8000
acl Safe_ports port 8001
acl Safe_ports port 554
acl Safe_ports port 6970-6999
acl Safe_ports port 7000-9999

acl blahblah src 123.45.67.89 89.76.54.0/24
http_access allow blahblah
http_access allow localhost
http_access deny all

http_port 23.45.67.89:1234 transparent

https_port 23.45.67.89:1238 transparent cert=/etc/pki/tls/certs/xxx.blahblahblah.com.cert key=/etc/pki/tls/private/xxx.blahblahblah.com.key protocol=https

---

