---
title: "Apache does not respond - firewall?"
date: 2011-02-26
forum: Server Platforms
---

### Post by avicarmi on 2011-02-26
Hi,


I set up apache to listen on ports 80, 8080, 8008 (plus few others 8042 2420)

I can access the apache sever via localhost, 127.0.0.1 and via [http://10.0.0.3](http://10.0.0.3) (and 10.0.0.3:8080 etc.) BUT only from my own machine!

trying to access it via [http://10.0.0.3](http://10.0.0.3) but from say 10.0.0.2 and it times out!!! 

same timeout if I try to access it from external IP


I set up port forwarding rules, and I do see these entries in the netgear log file, which seems to indicate that the traffic is forwarded to 10.0.03 

[LAN access from remote] from 70.32.122.27:53468 to 10.0.0.3:80 Friday, Feb 25,2011 23:05:02
[LAN access from remote] from 70.32.122.27:53398 to 10.0.0.3:8008 Friday, Feb 25,2011 23:04:54
[LAN access from remote] from 70.32.122.27:53384 to 10.0.0.3:8080 Friday, Feb 25,2011 23:04:47

so from this it seems that the ISP (Verizon DSL) is not blocking, and traffic does get to the WNR3500L router...

apache does seem to listen on these ports:
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      14136/apache2   
tcp        0      0 0.0.0.0:80               0.0.0.0:*               LISTEN      14136/apache2   
tcp        0      0 0.0.0.0:8008            0.0.0.0:*               LISTEN      14136/apache2   

which should be obvious, as it is accepting connection when I use the internal ip 10.0.0.3:8080  Yet 10.0.0.3 only works when I am on the same local host. BUT not from anywhere else on my internal network...


trying to access other random ports results in an immediate error message, probably since the router does not let these through. yet 10.0.0.3:8080 requests from outside the machine take a long time to timeout

so it seems that there is some sort of firewall running on Ubuntu, but I was not able to find it :-(

or is apache mis-configured??? though this does not make sense, as it is responding to localhost/127.0.0.1 and 10.0.0.3 from the same machine...

any ideas?  

-avi

---

### Post by Kljuka on 2011-02-26
Default Ubuntu configuration doesn't have any firewalls.
I don't believe Apache is the problem here (if it responds, it is working). You should double check your network (router configuration, network configurations).

I would first check your Ubuntu box for the IP it is configured to use:
```
ifconfig
```
eth0 (or something like that sould have a correct ip address (10.0.0.3 or whatever you said is your lan ip)

Then I would ping Ubuntu box. First from another machine in the same network. If it works, I would try http requests (from Firefox). If it works, then Ubuntu box is responding correctly. I would then test connecting from internet. If it doesn't respond, you might have misconfigured your router (probably NAT or Firewall rules).

You could also try traceroute 10.0.0.3 (from inside of your network, to see which routers are on the way of your request).

Hope this helps

---

### Post by avicarmi on 2011-02-26
Thank you so much.

I figured that there is no firewll running on Ubuntu, as I could not find one...  

However, I do think that it is the Ubuntu network configuration that is the problem.

I can access apache via [http://10.0.0.3](http://10.0.0.3) 

BUT only from itself, i.e. from 10.0.0.3 to 10.0.0.3  (I can also access using localhost and 127.0.0.1)

However, if I try accessing it from another machine on the LAN, say, 10.0.0.2 I get the same "timed out" reply as when I attempt to access it from outside my LAN.

I am using wireless to connect to the Netgear router so eth0 is NOT connected.

Could that be the problem? i.e. do I have to be hardwired to the router?

Does Ubuntu treat wireless connection any different than wired connection? i.e. more filtering? 

How do I make Ubuntu / Apache "listen" to connections from the "outside" on the wireless connection?

here it the output from ifconfig:

```
# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:dc:c0:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:525542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:525542 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22174235 (22.1 MB)  TX bytes:22174235 (22.1 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:a2:06:d8  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fea2:6d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:289907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:247006 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:130075952 (130.0 MB)  TX bytes:34933992 (34.9 MB)
```

I can ping it from 10.0.0.2:

```
# ping -c 10 10.0.0.3
PING 10.0.0.3 (10.0.0.3): 56 data bytes
64 bytes from 10.0.0.3: icmp_seq=0 ttl=64 time=0.935 ms
64 bytes from 10.0.0.3: icmp_seq=1 ttl=64 time=0.809 ms
64 bytes from 10.0.0.3: icmp_seq=2 ttl=64 time=0.777 ms
64 bytes from 10.0.0.3: icmp_seq=3 ttl=64 time=0.797 ms
64 bytes from 10.0.0.3: icmp_seq=4 ttl=64 time=0.807 ms
64 bytes from 10.0.0.3: icmp_seq=5 ttl=64 time=0.961 ms
64 bytes from 10.0.0.3: icmp_seq=6 ttl=64 time=0.826 ms
64 bytes from 10.0.0.3: icmp_seq=7 ttl=64 time=0.834 ms
64 bytes from 10.0.0.3: icmp_seq=8 ttl=64 time=1.042 ms
64 bytes from 10.0.0.3: icmp_seq=9 ttl=64 time=1.134 ms

--- 10.0.0.3 ping statistics ---
10 packets transmitted, 10 packets received, 0% packet loss
round-trip min/avg/max/stddev = 0.777/0.892/1.134/0.115 ms
```

traceroute only work with -I (ICMP ECHO)
```
# traceroute 10.0.0.3
traceroute to 10.0.0.3 (10.0.0.3), 64 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * ^C

# traceroute -I 10.0.0.3
traceroute to 10.0.0.3 (10.0.0.3), 64 hops max, 60 byte packets
 1  10.0.0.3 (10.0.0.3)  1.784 ms  1.005 ms  0.831 ms

```

but most telling is telnet to port 80 (or 8080 etc) times out:

```
# telnet 10.0.0.3 8080
Trying 10.0.0.3...
telnet: connect to address 10.0.0.3: Operation timed out
telnet: Unable to connect to remote host

```

---

### Post by CharlesA on 2011-02-26
Can you post the output of this please:

```
sudo iptables -L
```

---

### Post by avicarmi on 2011-02-26
Thank you so much for helping, here is the output:
```
# sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  google-public-dns-a.google.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  google-public-dns-a.google.com  anywhere            
ACCEPT     tcp  --  4.2.2.4              anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  4.2.2.4              anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             10.0.0.255          
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  avi-v1700            google-public-dns-a.google.com tcp dpt:domain 
ACCEPT     udp  --  avi-v1700            google-public-dns-a.google.com udp dpt:domain 
ACCEPT     tcp  --  avi-v1700            4.2.2.4             tcp dpt:domain 
ACCEPT     udp  --  avi-v1700            4.2.2.4             udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            

```

---

### Post by CharlesA on 2011-02-26
It looks like you have a firewall enabled, can you post the output of this:

```
sudo ufw status
```

---

### Post by avicarmi on 2011-02-26
```
# sudo ufw status
Status: inactive

```

I also found these in the /var/log/kern.log:
```
Feb 26 19:05:01 avi-v1700 kernel: [90234.325597] Inbound IN=wlan0 OUT= MAC=00:1f:3c:a2:06:d8:30:46:9a:9a:75:aa:08:00 SRC=70.32.122.27 DST=10.0.0.3 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=50750 DF PROTO=TCP SPT=45252 DPT=8008 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 26 19:05:04 avi-v1700 kernel: [90237.940565] Inbound IN=wlan0 OUT= MAC=00:1f:3c:a2:06:d8:30:46:9a:9a:75:aa:08:00 SRC=70.32.122.27 DST=10.0.0.3 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=8587 DF PROTO=TCP SPT=45311 DPT=8042 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 26 19:05:07 avi-v1700 kernel: [90240.323665] Inbound IN=wlan0 OUT= MAC=00:1f:3c:a2:06:d8:30:46:9a:9a:75:aa:08:00 SRC=70.32.122.27 DST=10.0.0.3 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=50752 DF PROTO=TCP SPT=45252 DPT=8008 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 26 19:05:07 avi-v1700 kernel: [90240.939564] Inbound IN=wlan0 OUT= MAC=00:1f:3c:a2:06:d8:30:46:9a:9a:75:aa:08:00 SRC=70.32.122.27 DST=10.0.0.3 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=8589 DF PROTO=TCP SPT=45311 DPT=8042 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 26 19:05:10 avi-v1700 kernel: [90243.822478] Inbound IN=wlan0 OUT= MAC=00:1f:3c:a2:06:d8:30:46:9a:9a:75:aa:08:00 SRC=70.32.122.27 DST=10.0.0.3 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=13082 DF PROTO=TCP SPT=45234 DPT=8080 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 26 19:05:13 avi-v1700 kernel: [90246.689145] Inbound IN=wlan0 OUT= MAC=00:1f:3c:a2:06:d8:30:46:9a:9a:75:aa:08:00 SRC=71.109.168.227 DST=10.0.0.3 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=10815 DF PROTO=TCP SPT=52168 DPT=8042 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 26 19:05:13 avi-v1700 kernel: [90246.939628] Inbound IN=wlan0 OUT= MAC=00:1f:3c:a2:06:d8:30:46:9a:9a:75:aa:08:00 SRC=70.32.122.27 DST=10.0.0.3 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=8591 DF PROTO=TCP SPT=45311 DPT=8042 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 26 19:05:17 avi-v1700 kernel: [90250.849761] Inbound IN=wlan0 OUT= MAC=00:1f:3c:a2:06:d8:30:46:9a:9a:75:aa:08:00 SRC=71.109.168.227 DST=10.0.0.3 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=8170 DF PROTO=TCP SPT=48188 DPT=8080 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 26 19:05:19 avi-v1700 kernel: [90252.322587] Inbound IN=wlan0 OUT= MAC=00:1f:3c:a2:06:d8:30:46:9a:9a:75:aa:08:00 SRC=70.32.122.27 DST=10.0.0.3 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=50754 DF PROTO=TCP SPT=45252 DPT=8008 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 26 19:05:22 avi-v1700 kernel: [90255.905047] Inbound IN=wlan0 OUT= MAC=00:1f:3c:a2:06:d8:30:46:9a:9a:75:aa:08:00 SRC=71.109.168.227 DST=10.0.0.3 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=42530 DF PROTO=TCP SPT=44261 DPT=8008 WINDOW=5840 RES=0x00 SYN URGP=0 

```

---

### Post by CharlesA on 2011-02-26
Are you using firestarter?

I know there's a a firewall in place, but I don't know which one is being used.

You could flush the rules but the default policy is drop, so that wouldn't work.

---

### Post by avicarmi on 2011-02-26
how can I find out which/what firewall is running, and disable it?

---

### Post by CharlesA on 2011-02-26
It sounds like you have firestarter running.

Try this:

```
ps aux | grep fire
```

---

### Post by avicarmi on 2011-02-26
Thank you so much,

after you mentioned firestarter, I went to the software center and installed it.

I added rule to let any traffic on port 80, 8080 and 8008.

it works now!!!

I am still curious how come something blocked the traffic when firestarter was not running? 

is there a "built in" firewall/rules for Ubuntu?

thanks you.

-avi

---

### Post by avicarmi on 2011-02-27
Thanks to all who helped.

here is my final analysis of what happened:

Initially I had "double NAT" with the netgear behind the Verizon DSL modem/router.

While trying to figure out what's wrong, I apparently turned on the Ubuntu firewall, so that after I converted the Verizon DSL into a bridge, and the netgear got its IP directly from Verizon, I still had firewall rules blocking access.

What threw me off initially was that I was able to access the web server via the machine's external IP (10.0.0.3). but once I realized that I could not access it from another machine on the internal network, it made me realize that it must be the Ubuntu network configuration, and that the router is fine.

Thanks again to all who helped.

-avi

---

