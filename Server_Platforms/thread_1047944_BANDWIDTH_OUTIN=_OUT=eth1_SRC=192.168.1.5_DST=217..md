---
title: "BANDWIDTH_OUT:IN= OUT=eth1 SRC=192.168.1.5 DST=217.9.143.11 LEN=82 TOS=0x00 PREC=0x00"
date: 2009-01-22
forum: Server Platforms
---

### Post by denni on 2009-01-22
What does this mean?

In /var/log/messages I get this ...

tail -f /var/log/syslog
> Jan 23 04:00:07 ns1 kernel: [199228.708365] BANDWIDTH_OUT:IN= OUT=eth1 SRC=192.168.1.5 DST=192.168.1.33 LEN=1500 TOS=0x10 PREC=0x00 TTL=64 ID=36817 DF PROTO=TCP SPT=22 DPT=34892 WINDOW=108 RES=0x00 ACK URGP=0                                                                                              
Jan 23 04:00:07 ns1 kernel: [199228.708375] BANDWIDTH_OUT:IN= OUT=eth1 SRC=192.168.1.5 DST=192.168.1.33 LEN=1500 TOS=0x10 PREC=0x00 TTL=64 ID=36818 DF PROTO=TCP SPT=22 DPT=34892 WINDOW=108 RES=0x00 ACK URGP=0                                                                                              
Jan 23 04:00:07 ns1 kernel: [199228.708384] BANDWIDTH_OUT:IN= OUT=eth1 SRC=192.168.1.5 DST=192.168.1.33 LEN=1500 TOS=0x10 PREC=0x00 TTL=64 ID=36819 DF PROTO=TCP SPT=22 DPT=34892 WINDOW=108 RES=0x00 ACK URGP=0                                                                                              
Jan 23 04:00:07 ns1 kernel: [199228.710326] BANDWIDTH_IN:IN=eth1 OUT= MAC=00:13:d3:e9:a1:d4:00:14:38:0c:22:a4:08:00 SRC=192.168.1.33 DST=192.168.1.5 LEN=52 TOS=0x10 PREC=0x00 TTL=64 ID=22547 DF PROTO=TCP SPT=34892 DPT=22 WINDOW=1705 RES=0x00 ACK URGP=0                                                  
Jan 23 04:00:07 ns1 kernel: [199228.710346] BANDWIDTH_OUT:IN= OUT=eth1 SRC=192.168.1.5 DST=192.168.1.33 LEN=1500 TOS=0x10 PREC=0x00 TTL=64 ID=36820 DF PROTO=TCP SPT=22 DPT=34892 WINDOW=108 RES=0x00 ACK URGP=0                                                                                              
Jan 23 04:00:07 ns1 kernel: [199228.710357] BANDWIDTH_OUT:IN= OUT=eth1 SRC=192.168.1.5 DST=192.168.1.33 LEN=148 TOS=0x10 PREC=0x00 TTL=64 ID=36821 DF PROTO=TCP SPT=22 DPT=34892 WINDOW=108 RES=0x00 ACK PSH URGP=0                                                                                           
Jan 23 04:00:07 ns1 kernel: [199228.712218] BANDWIDTH_IN:IN=eth1 OUT= MAC=00:13:d3:e9:a1:d4:00:14:38:0c:22:a4:08:00 SRC=192.168.1.33 DST=192.168.1.5 LEN=52 TOS=0x10 PREC=0x00 TTL=64 ID=22548 DF PROTO=TCP SPT=34892 DPT=22 WINDOW=1705 RES=0x00 ACK URGP=0                                                  
Jan 23 04:00:07 ns1 kernel: [199228.733544] BANDWIDTH_IN:IN=eth1 OUT= MAC=00:13:d3:e9:a1:d4:00:13:49:3a:45:d7:08:00 SRC=192.55.83.32 DST=192.168.1.5 LEN=164 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=UDP SPT=53 DPT=53 LEN=144                                                                                
Jan 23 04:00:07 ns1 kernel: [199228.733939] BANDWIDTH_OUT:IN= OUT=eth1 SRC=192.168.1.5 DST=216.239.36.10 LEN=82 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53 DPT=53 LEN=62                                                                                                                              
Jan 23 04:00:07 ns1 kernel: [199228.798513] BANDWIDTH_IN:IN=eth1 OUT= MAC=00:13:d3:e9:a1:d4:00:13:49:3a:45:d7:08:00 SRC=216.239.36.10 DST=192.168.1.5 LEN=142 TOS=0x00 PREC=0x00 TTL=54 ID=5453 PROTO=UDP SPT=53 DPT=53 LEN=122                                                                               
Jan 23 04:00:07 ns1 kernel: [199228.850779] BANDWIDTH_OUT:IN= OUT=eth1 SRC=192.168.1.5 DST=224.0.0.251 LEN=93 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=73                                                                                                                           
Jan 23 04:00:07 ns1 kernel: [199228.850801] BANDWIDTH_IN:IN=eth1 OUT= MAC= SRC=192.168.1.5 DST=224.0.0.251 LEN=93 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=73                                                                                                                       
Jan 23 04:00:07 ns1 kernel: [199229.049190] BANDWIDTH_IN:IN=eth1 OUT= MAC=00:13:d3:e9:a1:d4:00:13:49:3a:45:d7:08:00 SRC=66.230.128.15 DST=192.168.1.5 LEN=45 TOS=0x00 PREC=0x00 TTL=46 ID=26084 PROTO=UDP SPT=38080 DPT=53 LEN=25                                                                             
Jan 23 04:00:07 ns1 named[10245]: client 66.230.128.15#38080: query (cache) './NS/IN' denied                                                           
Jan 23 04:00:07 ns1 kernel: [199229.049387] BANDWIDTH_OUT:IN= OUT=eth1 SRC=192.168.1.5 DST=66.230.128.15 LEN=45 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53 DPT=38080 LEN=25                                                                                                                           
Jan 23 04:00:07 ns1 kernel: [199229.060627] BANDWIDTH_OUT:IN= OUT=eth1 SRC=192.168.1.5 DST=209.126.159.118 LEN=71 TOS=0x00 PREC=0x00 TTL=64 ID=47961 DF PROTO=UDP SPT=35093 DPT=53 LEN=51                                                                                                                     
Jan 23 04:00:07 ns1 kernel: [199229.208241] BANDWIDTH_IN:IN=eth1 OUT= MAC=00:13:d3:e9:a1:d4:00:13:49:3a:45:d7:08:00 SRC=209.126.159.118 DST=192.168.1.5 LEN=282 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=53 DPT=35093 LEN=262                                                                          
Jan 23 04:00:07 ns1 kernel: [199229.208507] BANDWIDTH_OUT:IN= OUT=eth1 SRC=192.168.1.5 DST=217.9.143.11 LEN=82 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53 DPT=53 LEN=62                                                                                                                               
Jan 23 04:00:07 ns1 kernel: [199229.217986] BANDWIDTH_IN:IN=eth1 OUT= MAC=00:13:d3:e9:a1:d4:00:13:49:3a:45:d7:08:00 SRC=217.9.143.11 DST=192.168.1.5 LEN=71 TOS=0x00 PREC=0x00 TTL=58 ID=52819 PROTO=UDP SPT=53 DPT=53 LEN=51                                                                                 
Jan 23 04:00:07 ns1 kernel: [199229.218079] BANDWIDTH_OUT:IN= OUT=eth1 SRC=192.168.1.5 DST=217.9.143.11 LEN=71 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53 DPT=53 LEN=51                                                                                                                               
Jan 23 04:00:07 ns1 kernel: [199229.227333] BANDWIDTH_IN:IN=eth1 OUT= MAC=00:13:d3:e9:a1:d4:00:13:49:3a:45:d7:08:00 SRC=217.9.143.11 DST=192.168.1.5 LEN=71 TOS=0x00 PREC=0x00 TTL=58 ID=52820 PROTO=UDP SPT=53 DPT=53 LEN=51                                                                                 
Jan 23 04:00:07 ns1 named[10245]: unexpected RCODE (SERVFAIL) resolving '114.51.15.81.in-addr.arpa/PTR/IN': 217.9.143.11#53                            
Jan 23 04:00:07 ns1 kernel: [199229.227480] BANDWIDTH_OUT:IN= OUT=eth1 SRC=192.168.1.5 DST=217.9.143.12 LEN=82 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53 DPT=53 LEN=62                                                                                                                               
Jan 23 04:00:07 ns1 kernel: [199229.236205] BANDWIDTH_IN:IN=eth1 OUT= 



I am using Shorewall as an firewall and when /etc/init.d/shorewall stop
then it goes away.  It is then a shorewall logging issue.   

Got two questions.    How do I stop the logging and how is it possible to stop this bombardment of data hitting the server?

---

### Post by windependence on 2009-01-23
You can put the shorewall logs in their own log file by changing the configuration file. 

Shorewall is doing what it it SUPPOSED to do by keeping unwanted packets out of your machine. We always hear from n00bs all excited about this. There is nothing to get all worried about. Your logs are compressed and rotated automatically for you by the system. They are useful if you need to see who was where on your system.

The correct way to do this if you want to stop the hammering on your server would be to set up a gateway/firewall box using shorewall, pfsense, untangle or something similar. Then, your unwanted traffic is stopped at the firewall/gateway and doesn't load your CPU on your server.

-Tim

---

### Post by irishdunn on 2009-01-23
I am getting the same thing, and have a RVS4000 in front of the machine. Wondering if there is anything I can do on that to lessen the load... Looks like I am getting hit 10-20 times a second.

---

### Post by denni on 2009-01-23
windependence Thank you for the answer.  Will try to figure out the exact method of doing this by googling "shorewall, pfsense, untangle" and then put it here.

If I change the logging file in config, how will I get that file compressed and rotated automatically without getting many gigs in size?   Lets say /var/log/shorewall.

5 minutes later... got about 7 google pages by googling shorewall pfsense untangle mostly firewall advertises.    So pls. some detailed instruction would be appreciated.

---

### Post by denni on 2009-01-23
> The correct way to do this if you want to stop the hammering on your server would be to set up a gateway/firewall box using shorewall, pfsense, untangle or something similar. Then, your unwanted traffic is stopped at the firewall/gateway and doesn't load your CPU on your server.


A am lacking the know how to do this in shorewall. So pls.

---

### Post by denni on 2009-01-23
Now this after commenting out in start file.

> Jan 23 21:29:32 ns1 named[10801]: client 63.217.28.226#58351: query (cache) './NS/IN' denied
Jan 23 21:29:32 ns1 named[10801]: client 63.217.28.226#18547: query (cache) './NS/IN' denied
Jan 23 21:29:33 ns1 named[10801]: client 63.217.28.226#47497: query (cache) './NS/IN' denied
Jan 23 21:29:34 ns1 named[10801]: client 63.217.28.226#57768: query (cache) './NS/IN' denied
Jan 23 21:29:36 ns1 named[10801]: client 63.217.28.226#26822: query (cache) './NS/IN' denied
Jan 23 21:29:36 ns1 named[10801]: client 63.217.28.226#17062: query (cache) './NS/IN' denied
Jan 23 21:29:36 ns1 named[10801]: client 63.217.28.226#48953: query (cache) './NS/IN' denied
Jan 23 21:29:38 ns1 named[10801]: client 63.217.28.226#14576: query (cache) './NS/IN' denied
Jan 23 21:29:39 ns1 named[10801]: client 63.217.28.226#44048: query (cache) './NS/IN' denied
Jan 23 21:29:39 ns1 named[10801]: client 63.217.28.226#47249: query (cache) './NS/IN' denied
Jan 23 21:29:40 ns1 named[10801]: client 63.217.28.226#20022: query (cache) './NS/IN' denied
Jan 23 21:29:41 ns1 named[10801]: client 76.9.16.171#10632: query (cache) './NS/IN' denied


---

### Post by denni on 2009-01-25
SOLVED!

My contribution to The Linux and Ubuntu community 

/etc/bind/named.conf or /var/lib/named/etc/bind   look at the bold text

**acl dumpthem { 63.217.28.226; 206.71.158.30; 66.230.160.1; };**
options {
        pid-file "/var/run/bind/run/named.pid";
        directory "/etc/bind";
        auth-nxdomain no;
        /*
         * If there is a firewall between you and nameservers you want
         * to talk to, you might need to uncomment the query-source
         * directive below.  Previous versions of BIND always asked
         * questions using port 53, but BIND 8.1 uses an unprivileged
         * port by default.
         */
       //  query-source address * port 53;
  
   **blackhole {dumpthem;};**
};

---

