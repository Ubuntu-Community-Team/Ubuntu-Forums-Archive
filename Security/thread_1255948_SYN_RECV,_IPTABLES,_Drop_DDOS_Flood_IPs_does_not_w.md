---
title: "SYN_RECV, IPTABLES, Drop DDOS Flood IPs does not work!"
date: 2009-09-02
forum: Security
---

### Post by eurusd on 2009-09-02
SYN_RECV, IPTABLES, Drop DDOS Flood IPs does not work!
I use this command to block ddos ips

while true; do netstat -n -p | grep SYN_REC | awk '{print $5}' | awk -F: '{print $1}' | sort | uniq; netstat -n -p | grep SYN_REC | awk '{print $5}' | awk -F: '{print $1}' | sort | uniq > /tmp/ips.txt;for IP in `cat /tmp/ips.txt`; do iptables -A INPUT -s $IP -j DROP;done;service iptables save; sleep 30; done;

but still all the same ips that SYN RECV DDOS me remain active &#61516;
I tried iptables restart still wont kill those bad connections
How to really drop them so I wont see them again in netstat

You have new mail in /var/spool/mail/root
[root@vbox2fedora11 ~]# sysctl -p
net.ipv4.ip_forward = 0
net.ipv4.tcp_syncookies = 1
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.default.accept_source_route = 0
kernel.sysrq = 0
kernel.core_uses_pid = 1
[root@vbox2fedora11 ~]#

96.49.250.193
iptables: Saving firewall rules to /etc/sysconfig/iptables: [  OK  ]
10.1.231.55
187.146.59.172
188.51.4.221
196.209.198.197
201.165.12.21
201.26.106.227
24.234.86.254
67.167.150.169
69.46.142.122
76.217.95.6
77.183.84.46
77.196.51.125
77.210.98.64
78.50.226.250
82.9.59.77
84.143.187.50
85.157.188.208
87.96.232.60
91.193.220.129
92.153.255.183
94.153.161.250
96.32.251.220
96.49.250.193
iptables: Saving firewall rules to /etc/sysconfig/iptables: [  OK  ]
10.1.231.55
187.146.59.172
196.209.198.197
201.26.106.227
217.201.127.118
24.234.86.254
67.167.150.169
69.111.189.49
69.46.142.122
76.217.95.6
77.183.84.46
77.196.51.125
77.210.98.64
78.50.226.250
82.9.59.77
84.143.187.50
85.157.188.208
86.153.68.53
87.96.232.60
91.193.220.129
92.153.255.183
94.153.161.250
96.32.251.220
96.49.250.193
iptables: Saving firewall rules to /etc/sysconfig/iptables: [  OK  ]


[root@vbox2fedora11 ~]# netstat
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address               Foreign Address             State      
tcp        0      0 :http          S0106001cdf20124e.vc.:52419 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52414 SYN_RECV    
tcp        0      0 :http          a88-112-87-22:pnaconsult-lm SYN_RECV    
tcp        0      0 :http          dsl-187-146-59-172-:houston SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52397 SYN_RECV    
tcp        0      0 :http          dsl-187-146-59-172-:yo-main SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52416 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52420 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52398 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52395 SYN_RECV    
tcp        0      0 :http          static-84-166-145-212:14949 SYN_RECV    
tcp        0      0 :http          5ad0d533.bb.sk:netbill-auth SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52421 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52422 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52417 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52402 SYN_RECV    
tcp        0      0 :http          static.unknown.c:dicom-iscl SYN_RECV    
tcp        0      0 :http          d66-183-27-194.bchsia:60266 SYN_RECV    
tcp        0      0 :http          10.1.231.55:edm-manager     SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52405 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52393 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52411 SYN_RECV    
tcp        0      0 :http          188.51.4.221:46386          SYN_RECV    
tcp        0      0 :http          dsl-144-98-232.telkoma:3404 SYN_RECV    
tcp        0      0 :http          bl7-78-16.dsl.telepac:14020 SYN_RECV    
tcp        0      0 :http          172.16.127.226:houston      SYN_RECV    
tcp        0      0 :http          p548FBB32.dip.t-di:mps-raft SYN_RECV    
tcp        0      0 :http          adsl-76-217-95-6.dsl.:60250 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52401 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52407 SYN_RECV    
tcp        0      0 :http          125.51.196-77.rev.g:netplan SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52408 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52418 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52399 SYN_RECV    
tcp        0      0 :http          d66-183-27-194.bchsia:60285 SYN_RECV    
tcp        0      0 :http          static-84-166-145-212:14950 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52413 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52404 SYN_RECV    
tcp        0      0 :http          mobile-3G-dyn-BC-190-:52242 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52415 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52394 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52409 SYN_RECV    
tcp        0      0 :http          bas3-montreal31-12797:61810 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52396 SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52423 SYN_RECV    
tcp        0      0 :http          217.71.225.75:4497          SYN_RECV    
tcp        0      0 :http          S0106001cdf20124e.vc.:52412 SYN_RECV

---

### Post by The Cog on 2009-09-03
> **eurusd said:**
> service iptables save
There isn't a /etc/init.d/iptables script on my PC - I suspect this command is doing nothing.
> iptables -A INPUT -s $IP -j DROP
This adds the rule at the end of the existoing rules. There may be earlier rules that allow the conection through. I would suggest inserting the new rule at the start of the list instead. Perhaps use **iptables -I INPUT -s $IP -j DROP** instead.

---

