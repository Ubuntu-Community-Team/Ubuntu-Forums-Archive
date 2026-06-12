---
title: "OpenVPN connects to VPN but no internet (Ubuntu 10.10 64-bit)"
date: 2011-01-05
forum: Security
---

### Post by MedianN on 2011-01-05
Hello,

I use vpntunnel.se and followed their tutorial for OpenVPN and it connects and assigns an IP. However, once the sequence is initiated and I open my browser I cannot connect to a  webpage and get a "cannot resolve" error. 

I e-mailed their support and they suggested I change the DNS of my network settings. I did that but the same problem. Once I close OpenVPN my internet works again. 

It works in windows, so I know it is not my router...

I use a wireless connection with my router. I don't know if this has something to do with anything...

I would really appreciate some assistance I have been on forums the last few days but I couldn't find anything that solved my problem.

Hoping someone can help me as this is a serious headache for me. .

---

### Post by spynappels on 2011-01-06
It sounds like your default route is not being set correctly when your VPN connection is brought up.

Can you post your routing table when no VPN connection is connected and when it is connected, and we can have a look where the problem lies.

---

### Post by MedianN on 2011-01-06
Firstly, thank you for your reply. 

I am attaching the conf file I input into network manager -- but as I said it seems to connect correctly. I just added 8.8.4.4  as suggested by someone else as a dns server but it seems not to work. 

As for the information requested, could you please assist me in how to find that information for you :redface:

I am not as newbie as I seem, I just haven't used Linux in almost a decade lol. Slackware 6.0 I think was the last distro I used.

---

### Post by MedianN on 2011-01-06
Found the routing table, first instance is without the VPN enabled, the second with.


user@ubuntu:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0

user@ubuntu:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
178.73.212.226  192.168.1.1     255.255.255.255 UGH       0 0          0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
178.73.206.0    0.0.0.0         255.255.255.0   U         0 0          0 tap0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         178.73.206.1    0.0.0.0         UG        0 0          0 tap0

---

### Post by spynappels on 2011-01-06
I'll have another look, but the second routing table does not seem quite right to me. I have to go now, but I'll have a look at it later.

Any chance you could also show the output of 
```
ifconfig tap0
```
and
```
ifconfig eth0
```
both while the VPN is connected so I can see what settings are applied to the different network adapters.

---

### Post by MedianN on 2011-01-06
Here is tap0, eth0 and wlan0 all whilst the vpn is connected. [I am on a laptop using a wireless connection to my router.]

user@ubuntu:~$ ifconfig tap0
tap0      Link encap:Ethernet  HWaddr ca:38:8a:c8:d9:54  
          inet addr:188.126.69.187  Bcast:188.126.69.255  Mask:255.255.255.0
          inet6 addr: fe80::c838:8aff:fec8:d954/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:392 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:19043 (19.0 KB)  TX bytes:3043 (3.0 KB)

users@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:26:22:e9:50:1b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0xe000 

users@ubuntu:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:26:b6:6f:f6:91  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b6ff:fe6f:f691/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:273595 errors:0 dropped:0 overruns:0 frame:0
          TX packets:343586 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104642162 (104.6 MB)  TX bytes:25816458 (25.8 MB)

---

### Post by GGabor74 on 2011-01-06
I've got the same problem, strill trying to resolve with google but no result yet
 
[http://ubuntuforums.org/showthread.php?t=1658384](http://ubuntuforums.org/showthread.php?t=1658384)

---

### Post by The Cog on 2011-01-07
Please can you post the output from these commands, both without the VPN running and then with it running:
```
ifconfig
route -n
cat /etc/resolv.conf
ping -c3 91.189.94.186
ping -c3 ubuntuforums.com
```
Also, are you running a firewall? If so, do things work if you disable it?

---

### Post by MedianN on 2011-01-07
Thank you for joining the discussion!

I don't run a firewall, except if its programmed into the Ubuntu install, then I have the default settings enabled for that. If you want me to test that please let me know how to disable and re-enable it.

**Without VPN enabled:**
```

user@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:e9:50:1b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4496 (4.4 KB)  TX bytes:4496 (4.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:b6:6f:f6:91  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b6ff:fe6f:f691/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:900 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:623181 (623.1 KB)  TX bytes:138933 (138.9 KB)



```

```

user@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```

```

user@ubuntu:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 8.8.8.8
nameserver 8.8.4.4

```

```

user@ubuntu:~$ ping -c3 91.189.94.186
PING 91.189.94.186 (91.189.94.186) 56(84) bytes of data.
64 bytes from 91.189.94.186: icmp_req=1 ttl=48 time=287 ms
64 bytes from 91.189.94.186: icmp_req=2 ttl=48 time=287 ms
64 bytes from 91.189.94.186: icmp_req=3 ttl=48 time=288 ms

--- 91.189.94.186 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 287.442/287.818/288.566/0.814 ms

```

```

user@ubuntu:~$ ping -c3 ubuntuforums.com
PING ubuntuforums.com (91.189.94.186) 56(84) bytes of data.
64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_req=1 ttl=48 time=286 ms
64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_req=2 ttl=48 time=287 ms
64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_req=3 ttl=48 time=285 ms

--- ubuntuforums.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 285.630/286.637/287.592/0.801 ms


```


**With VPN enabled:**

```

user@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:e9:50:1b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5312 (5.3 KB)  TX bytes:5312 (5.3 KB)

tap0      Link encap:Ethernet  HWaddr 12:c4:e3:d3:4b:3b  
          inet addr:178.73.209.186  Bcast:178.73.209.255  Mask:255.255.255.0
          inet6 addr: fe80::10c4:e3ff:fed3:4b3b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:634 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:40375 (40.3 KB)  TX bytes:3043 (3.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:b6:6f:f6:91  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b6ff:fe6f:f691/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:822348 (822.3 KB)  TX bytes:187811 (187.8 KB)


```

```

user@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
178.73.212.230  192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
178.73.209.0    0.0.0.0         255.255.255.0   U     0      0        0 tap0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         178.73.209.1    0.0.0.0         UG    0      0        0 tap0


```

```

user@ubuntu:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 80.67.0.2
nameserver 91.213.246.2
nameserver 8.8.8.8


```

```

user@ubuntu:~$ ping -c3 91.189.94.186
PING 91.189.94.186 (91.189.94.186) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 91.189.94.186 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2005ms


```

```

user@ubuntu:~$ ping -c3 ubuntuforums.com
ping: unknown host ubuntuforums.com


```

---

### Post by The Cog on 2011-01-08
OK, looking at your results, I can see the following:

Starting the VPN has created a tap interface and given it a valid IP address. Good.

Your new routing table looks good: Default route over the VPN, but there is a specific route to the VPN server over the wireless interface so that OpenVPN can still reach the server.

Resolv.conf shows that the VPN has changed your nameserver to their own.
You have lost the original 8.8.4.4 nameserver, so presumably when you end the VPN, you won't have a backup name server any more. Mildly bad, but not the cause of your problems. 

Ping to a specific IP address fails. Bad. I expected this to work. It seems that you are unable to send packets out over the VPN. This would prevent the name lookup in the next test from working. I found this thread: [http://ubuntuforums.org/showthread.php?t=345251](http://ubuntuforums.org/showthread.php?t=345251) which suggests this is a firewall configuration issue. Please can you also post the output of the command
```
sudo iptables-save -c
```
both with and without the VPN connected.

---

### Post by MedianN on 2011-01-08
Thank you for your reply.

**VPN disabled:**
```

# Generated by iptables-save v1.4.4 on Sat Jan  8 14:48:14 2011
*nat
:PREROUTING ACCEPT [354:67213]
:OUTPUT ACCEPT [1573:97080]
:POSTROUTING ACCEPT [764:43779]
COMMIT
# Completed on Sat Jan  8 14:48:14 2011
# Generated by iptables-save v1.4.4 on Sat Jan  8 14:48:14 2011
*mangle
:PREROUTING ACCEPT [32085:6917274]
:INPUT ACCEPT [31243:6805624]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [7373:945937]
:POSTROUTING ACCEPT [6539:890321]
COMMIT
# Completed on Sat Jan  8 14:48:14 2011
# Generated by iptables-save v1.4.4 on Sat Jan  8 14:48:14 2011
*filter
:INPUT DROP [5:716]
:FORWARD DROP [0:0]
:OUTPUT DROP [815:53382]
:INBOUND - [0:0]
:LOG_FILTER - [0:0]
:LSI - [0:0]
:LSO - [0:0]
:OUTBOUND - [0:0]
[0:0] -A INPUT -s 8.8.8.8/32 -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -j ACCEPT 
[435:59091] -A INPUT -s 8.8.8.8/32 -p udp -j ACCEPT 
[0:0] -A INPUT -s 8.8.4.4/32 -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -j ACCEPT 
[18:2333] -A INPUT -s 8.8.4.4/32 -p udp -j ACCEPT 
[22:1188] -A INPUT -i lo -j ACCEPT 
[12:2752] -A INPUT -p icmp -m limit --limit 10/sec -j ACCEPT 
[10:3282] -A INPUT -d 255.255.255.255/32 -i wlan0 -j DROP 
[26:2330] -A INPUT -d 192.168.1.255/32 -j DROP 
[0:0] -A INPUT -s 224.0.0.0/8 -j DROP 
[158:25409] -A INPUT -d 224.0.0.0/8 -j DROP 
[0:0] -A INPUT -s 255.255.255.255/32 -j DROP 
[0:0] -A INPUT -d 0.0.0.0/32 -j DROP 
[3:120] -A INPUT -m state --state INVALID -j DROP 
[0:0] -A INPUT -f -m limit --limit 10/min -j LSI 
[30554:6708403] -A INPUT -i wlan0 -j INBOUND 
[5:716] -A INPUT -j LOG_FILTER 
[5:716] -A INPUT -j LOG --log-prefix "Unknown Input" --log-level 6 
[0:0] -A FORWARD -p icmp -m limit --limit 10/sec -j ACCEPT 
[0:0] -A FORWARD -j LOG_FILTER 
[0:0] -A FORWARD -j LOG --log-prefix "Unknown Forward" --log-level 6 
[0:0] -A OUTPUT -s 192.168.1.2/32 -d 8.8.8.8/32 -p tcp -m tcp --dport 53 -j ACCEPT 
[453:29569] -A OUTPUT -s 192.168.1.2/32 -d 8.8.8.8/32 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A OUTPUT -s 192.168.1.2/32 -d 8.8.4.4/32 -p tcp -m tcp --dport 53 -j ACCEPT 
[18:1148] -A OUTPUT -s 192.168.1.2/32 -d 8.8.4.4/32 -p udp -m udp --dport 53 -j ACCEPT 
[22:1188] -A OUTPUT -o lo -j ACCEPT 
[0:0] -A OUTPUT -s 224.0.0.0/8 -j DROP 
[15:2074] -A OUTPUT -d 224.0.0.0/8 -j DROP 
[0:0] -A OUTPUT -s 255.255.255.255/32 -j DROP 
[0:0] -A OUTPUT -d 0.0.0.0/32 -j DROP 
[4:160] -A OUTPUT -m state --state INVALID -j DROP 
[6046:858416] -A OUTPUT -o wlan0 -j OUTBOUND 
[815:53382] -A OUTPUT -j LOG_FILTER 
[815:53382] -A OUTPUT -j LOG --log-prefix "Unknown Output" --log-level 6 
[4681:3784249] -A INBOUND -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT 
[25863:2923168] -A INBOUND -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT 
[10:986] -A INBOUND -j LSI 
[10:986] -A LSI -j LOG_FILTER 
[0:0] -A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6 
[0:0] -A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -j DROP 
[0:0] -A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK RST -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6 
[0:0] -A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK RST -j DROP 
[0:0] -A LSI -p icmp -m icmp --icmp-type 8 -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6 
[0:0] -A LSI -p icmp -m icmp --icmp-type 8 -j DROP 
[10:986] -A LSI -m limit --limit 5/sec -j LOG --log-prefix "Inbound " --log-level 6 
[10:986] -A LSI -j DROP 
[0:0] -A LSO -j LOG_FILTER 
[0:0] -A LSO -m limit --limit 5/sec -j LOG --log-prefix "Outbound " --log-level 6 
[0:0] -A LSO -j REJECT --reject-with icmp-port-unreachable 
[897:124638] -A OUTBOUND -p icmp -j ACCEPT 
[4650:700628] -A OUTBOUND -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT 
[201:19842] -A OUTBOUND -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT 
[298:13308] -A OUTBOUND -j ACCEPT 
COMMIT
# Completed on Sat Jan  8 14:48:14 2011


```

```

# Generated by iptables-save v1.4.4 on Sat Jan  8 14:50:52 2011
*nat
:PREROUTING ACCEPT [379:70696]
:OUTPUT ACCEPT [1686:103809]
:POSTROUTING ACCEPT [815:46580]
COMMIT
# Completed on Sat Jan  8 14:50:52 2011
# Generated by iptables-save v1.4.4 on Sat Jan  8 14:50:52 2011
*mangle
:PREROUTING ACCEPT [33083:7150971]
:INPUT ACCEPT [32227:7032574]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [7867:1001249]
:POSTROUTING ACCEPT [6969:941271]
COMMIT
# Completed on Sat Jan  8 14:50:52 2011
# Generated by iptables-save v1.4.4 on Sat Jan  8 14:50:52 2011
*filter
:INPUT DROP [5:716]
:FORWARD DROP [0:0]
:OUTPUT DROP [879:57744]
:INBOUND - [0:0]
:LOG_FILTER - [0:0]
:LSI - [0:0]
:LSO - [0:0]
:OUTBOUND - [0:0]
[0:0] -A INPUT -s 8.8.8.8/32 -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -j ACCEPT 
[450:60766] -A INPUT -s 8.8.8.8/32 -p udp -j ACCEPT 
[0:0] -A INPUT -s 8.8.4.4/32 -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -j ACCEPT 
[20:2501] -A INPUT -s 8.8.4.4/32 -p udp -j ACCEPT 
[35:2004] -A INPUT -i lo -j ACCEPT 
[24:4464] -A INPUT -p icmp -m limit --limit 10/sec -j ACCEPT 
[11:3610] -A INPUT -d 255.255.255.255/32 -i wlan0 -j DROP 
[26:2330] -A INPUT -d 192.168.1.255/32 -j DROP 
[0:0] -A INPUT -s 224.0.0.0/8 -j DROP 
[180:28500] -A INPUT -d 224.0.0.0/8 -j DROP 
[0:0] -A INPUT -s 255.255.255.255/32 -j DROP 
[0:0] -A INPUT -d 0.0.0.0/32 -j DROP 
[3:120] -A INPUT -m state --state INVALID -j DROP 
[0:0] -A INPUT -f -m limit --limit 10/min -j LSI 
[31473:6927563] -A INPUT -i wlan0 -j INBOUND 
[5:716] -A INPUT -j LOG_FILTER 
[5:716] -A INPUT -j LOG --log-prefix "Unknown Input" --log-level 6 
[0:0] -A FORWARD -p icmp -m limit --limit 10/sec -j ACCEPT 
[0:0] -A FORWARD -j LOG_FILTER 
[0:0] -A FORWARD -j LOG --log-prefix "Unknown Forward" --log-level 6 
[0:0] -A OUTPUT -s 192.168.1.2/32 -d 8.8.8.8/32 -p tcp -m tcp --dport 53 -j ACCEPT 
[470:30584] -A OUTPUT -s 192.168.1.2/32 -d 8.8.8.8/32 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A OUTPUT -s 192.168.1.2/32 -d 8.8.4.4/32 -p tcp -m tcp --dport 53 -j ACCEPT 
[20:1268] -A OUTPUT -s 192.168.1.2/32 -d 8.8.4.4/32 -p udp -m udp --dport 53 -j ACCEPT 
[35:2004] -A OUTPUT -o lo -j ACCEPT 
[0:0] -A OUTPUT -s 224.0.0.0/8 -j DROP 
[15:2074] -A OUTPUT -d 224.0.0.0/8 -j DROP 
[0:0] -A OUTPUT -s 255.255.255.255/32 -j DROP 
[0:0] -A OUTPUT -d 0.0.0.0/32 -j DROP 
[4:160] -A OUTPUT -m state --state INVALID -j DROP 
[6444:907415] -A OUTPUT -o wlan0 -j OUTBOUND 
[879:57744] -A OUTPUT -j LOG_FILTER 
[879:57744] -A OUTPUT -j LOG --log-prefix "Unknown Output" --log-level 6 
[4995:3935835] -A INBOUND -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT 
[26468:2990742] -A INBOUND -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT 
[10:986] -A INBOUND -j LSI 
[10:986] -A LSI -j LOG_FILTER 
[0:0] -A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6 
[0:0] -A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -j DROP 
[0:0] -A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK RST -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6 
[0:0] -A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK RST -j DROP 
[0:0] -A LSI -p icmp -m icmp --icmp-type 8 -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6 
[0:0] -A LSI -p icmp -m icmp --icmp-type 8 -j DROP 
[10:986] -A LSI -m limit --limit 5/sec -j LOG --log-prefix "Inbound " --log-level 6 
[10:986] -A LSI -j DROP 
[0:0] -A LSO -j LOG_FILTER 
[0:0] -A LSO -m limit --limit 5/sec -j LOG --log-prefix "Outbound " --log-level 6 
[0:0] -A LSO -j REJECT --reject-with icmp-port-unreachable 
[897:124638] -A OUTBOUND -p icmp -j ACCEPT 
[4961:741244] -A OUTBOUND -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT 
[257:26603] -A OUTBOUND -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT 
[329:14930] -A OUTBOUND -j ACCEPT 
COMMIT
# Completed on Sat Jan  8 14:50:52 2011


```

---

### Post by The Cog on 2011-01-08
There's your problem (probably). You are running a firewall. I have no idea which one though. The rules do not allow using the VPN interface, and are not being changed (I wouldn't expect them to) when the VPN is started. 

The two most common firewalls I read about are UFW and firestarter. Perhaps you should look in synaptic and see which one is installed, then do a complete removal.

A quick test would be to use very simple firewall rules with this series of commands (this will replace your existing firewall rules until next reboot):
```
sudo iptables -F
sudo iptables -X
sudo iptables -P INPUT DROP
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD DROP
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
```

---

### Post by MedianN on 2011-01-08
I removed Firestarter. 

I also used your code and the following happened:

Still no websites, but it connected longer, almost as if there was a time out eventually. The chrome error is still RESOLV though. I then input a manual DNS into the IPv4 still no cigar. Sigh :-(

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
178.73.212.230  192.168.1.1     255.255.255.255 UGH       0 0          0 wlan0
178.73.209.0    0.0.0.0         255.255.255.0   U         0 0          0 tap0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         178.73.209.1    0.0.0.0         UG        0 0          0 tap0

```

---

### Post by MedianN on 2011-01-08
OMG! It works now! After trying the terminal version of OpenVPN.

Thank you so much!

How do I make this a permanent fix though, will my firewall revert or stay the same? Also -- am I safe with this firewall setup!

THANK YOU!

---

### Post by The Cog on 2011-01-08
The little firewall script I gave you should be safe - it blocks all incoming connections but allows all outbound connections.

But you really should sort out your existing firewall setup. I generally argue that Ubuntu doesn't need a firewall because it doesn't have any unwanted and unstoppable listening services running. So I suggest that you identify and remove the firewall that's there now.

If you really feel you want firewall rules, try these 
```
# Firewall configuration
# Clear out the old crap
/sbin/iptables -F
/sbin/iptables -X
/sbin/ip6tables -F
/sbin/ip6tables -X

# Default policy
/sbin/iptables -P INPUT DROP
/sbin/iptables -P OUTPUT ACCEPT
/sbin/iptables -P FORWARD DROP
/sbin/ip6tables -P INPUT DROP
/sbin/ip6tables -P OUTPUT DROP
/sbin/ip6tables -P FORWARD DROP

# Allow existing connections to continue
/sbin/iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
/sbin/ip6tables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 

# Allow packets from loopback interface
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/ip6tables -A INPUT -i lo -j ACCEPT

```
Put them in a script (perhaps /etc/firewall.sh)
make it executable: **sudo chmod +x /etc/firewall.sh**
make it owned by root: **sudo chown root:root /etc/firewall.sh**

Then you can run it any time with **sudo /etc/firewall.sh** or add the it to /etc/rc.local to have it run when the PC boots.

But you must find out what is configuring your current firewall rules first, and stop that. Having two different programs fighting over what is in iptables is going to bring trouble.

---

### Post by pi3ch on 2011-04-07
The other piece of cake solution is to 

[LIST=1]
[*]Import your VPN config file in NetworkManager
[*]Edit the VPN connection
[*]Go to IP Settings tab (IP4Settings)
[*]Click on Routes
[*]Check "Use this connection only for resources on its network"
[*]Restart the connection.
[/LIST]
This will no allow the VPN connection to mess up your routing table.

---

### Post by dsegarra on 2011-05-29
Hi there. I hope I can get some help here. I am having the same problem. My clients cant connect to the internet. I know it is a firewall issue because I can disable it and it works. However, my server was hacked and I am very paranoid and so far my iptables have been working. Can you help me out here?

iptables-save -c posts this:
> # Generated by iptables-save v1.4.10 on Sat May 28 21:58:04 2011
*mangle
:PREROUTING ACCEPT [24462:6638243]
:INPUT ACCEPT [6685:833190]
:FORWARD ACCEPT [31031:10152425]
:OUTPUT ACCEPT [6053:1821729]
:POSTROUTING ACCEPT [37275:11997938]
[0:0] -A POSTROUTING -o virbr0 -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill 
[0:0] -A POSTROUTING -o virbr0 -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill 
[0:0] -A POSTROUTING -o virbr0 -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill 
[0:0] -A POSTROUTING -o virbr0 -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill 
[0:0] -A POSTROUTING -o virbr0 -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill 
[0:0] -A POSTROUTING -o virbr0 -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill 
[0:0] -A POSTROUTING -o virbr0 -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill 
[0:0] -A POSTROUTING -o virbr0 -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill 
[0:0] -A POSTROUTING -o virbr0 -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill 
[0:0] -A POSTROUTING -o virbr0 -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill 
[0:0] -A POSTROUTING -o virbr0 -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill 
[0:0] -A POSTROUTING -o virbr0 -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill 
[0:0] -A POSTROUTING -o virbr0 -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill 
COMMIT
# Completed on Sat May 28 21:58:04 2011
# Generated by iptables-save v1.4.10 on Sat May 28 21:58:04 2011
*filter
:INPUT DROP [0:0]
:FORWARD ACCEPT [30945:10146890]
:OUTPUT ACCEPT [6053:1821729]
:TCP - [0:0]
:UDP - [0:0]
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 67 -j ACCEPT 
[0:0] -A INPUT -s 127.0.0.0/8 -i eth0 -j DROP 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 53 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p udp -m udp --dport 67 -j ACCEPT 
[0:0] -A INPUT -i virbr0 -p tcp -m tcp --dport 67 -j ACCEPT 
[0:0] -A INPUT -p tcp -m tcp --dport 10000 -j ACCEPT 
[213:18424] -A INPUT -i lo -j ACCEPT 
[0:0] -A INPUT -m state --state INVALID -j DROP 
[5889:745165] -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
[3:180] -A INPUT -p icmp -m icmp --icmp-type 8 -m state --state NEW -j ACCEPT 
[487:66357] -A INPUT -p udp -m state --state NEW -j UDP 
[44:2268] -A INPUT -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j TCP 
[13:4296] -A INPUT -p udp -j REJECT --reject-with icmp-port-unreachable 
[28:1408] -A INPUT -p tcp -j REJECT --reject-with tcp-reset 
[60:1764] -A INPUT -j REJECT --reject-with icmp-proto-unreachable 
[0:0] -A INPUT -p tcp -m tcp --dport 10000 -j ACCEPT 
[0:0] -A INPUT -i eth0 -p tcp -m tcp --dport 22 -m state --state NEW -m recent --set --name SSH --rsource 
[0:0] -A INPUT -i eth0 -p tcp -m tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name SSH --rsource -j DROP 
[0:0] -A INPUT -i tun+ -j ACCEPT 
[0:0] -A FORWARD -d 192.168.122.0/24 -o virbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
[0:0] -A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT 
[0:0] -A FORWARD -i virbr0 -o virbr0 -j ACCEPT 
[0:0] -A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -d 192.168.122.0/24 -o virbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
[0:0] -A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT 
[0:0] -A FORWARD -i virbr0 -o virbr0 -j ACCEPT 
[0:0] -A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -d 192.168.122.0/24 -o virbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
[0:0] -A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT 
[0:0] -A FORWARD -i virbr0 -o virbr0 -j ACCEPT 
[0:0] -A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -d 192.168.122.0/24 -o virbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
[0:0] -A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT 
[0:0] -A FORWARD -i virbr0 -o virbr0 -j ACCEPT 
[0:0] -A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -d 192.168.122.0/24 -o virbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
[0:0] -A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT 
[0:0] -A FORWARD -i virbr0 -o virbr0 -j ACCEPT 
[0:0] -A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -d 192.168.122.0/24 -o virbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
[0:0] -A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT 
[0:0] -A FORWARD -i virbr0 -o virbr0 -j ACCEPT 
[0:0] -A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -d 192.168.122.0/24 -o virbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
[0:0] -A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT 
[0:0] -A FORWARD -i virbr0 -o virbr0 -j ACCEPT 
[0:0] -A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -d 192.168.122.0/24 -o virbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
[0:0] -A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT 
[0:0] -A FORWARD -i virbr0 -o virbr0 -j ACCEPT 
[0:0] -A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -d 192.168.122.0/24 -o virbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
[0:0] -A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT 
[0:0] -A FORWARD -i virbr0 -o virbr0 -j ACCEPT 
[0:0] -A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -d 192.168.122.0/24 -o virbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
[0:0] -A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT 
[0:0] -A FORWARD -i virbr0 -o virbr0 -j ACCEPT 
[0:0] -A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -d 192.168.122.0/24 -o virbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
[0:0] -A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT 
[0:0] -A FORWARD -i virbr0 -o virbr0 -j ACCEPT 
[0:0] -A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -d 192.168.122.0/24 -o virbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
[0:0] -A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT 
[0:0] -A FORWARD -i virbr0 -o virbr0 -j ACCEPT 
[0:0] -A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -d 192.168.122.0/24 -o virbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
[0:0] -A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT 
[0:0] -A FORWARD -i virbr0 -o virbr0 -j ACCEPT 
[0:0] -A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -d 192.168.122.0/24 -o virbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
[0:0] -A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT 
[0:0] -A FORWARD -i virbr0 -o virbr0 -j ACCEPT 
[0:0] -A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable 
[86:5535] -A FORWARD -i tun+ -j ACCEPT 
[3:144] -A TCP -p tcp -m tcp --dport 80 -j ACCEPT 
[0:0] -A TCP -p tcp -m tcp --dport 53 -j ACCEPT 
[2:120] -A TCP -p tcp -m tcp --dport 22 -j ACCEPT 
[0:0] -A TCP -p tcp -m tcp --dport 135 -j ACCEPT 
[2:96] -A TCP -p tcp -m tcp --dport 139 -j ACCEPT 
[3:152] -A TCP -p tcp -m tcp --dport 445 -j ACCEPT 
[0:0] -A TCP -p tcp -m tcp --dport 8000 -j ACCEPT 
[0:0] -A TCP -p tcp -m tcp --dport 443 -j ACCEPT 
[0:0] -A TCP -p tcp -m tcp --dport 49531 -j ACCEPT 
[6:348] -A TCP -p tcp -m tcp --dport 1720 -j ACCEPT 
[337:28176] -A UDP -p udp -m udp --dport 137 -j ACCEPT 
[137:33885] -A UDP -p udp -m udp --dport 138 -j ACCEPT 
[0:0] -A UDP -p udp -m udp --dport 443 -j ACCEPT 
COMMIT
# Completed on Sat May 28 21:58:04 2011
# Generated by iptables-save v1.4.10 on Sat May 28 21:58:04 2011
*nat
:PREROUTING ACCEPT [1549:257979]
:INPUT ACCEPT [27:3003]
:OUTPUT ACCEPT [158:16355]
:POSTROUTING ACCEPT [1143:127708]
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535 
[2:192] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE 
[0:0] -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE 
[0:0] -A POSTROUTING -s 192.168.10.0/24 -o eth0 -j MASQUERADE 
[0:0] -A POSTROUTING -s 192.168.10.0/24 -o eth0 -j MASQUERADE 
COMMIT


this are my TCP iptables rules:
> 1    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
2    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:53 
3    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22 
4    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:135 
5    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:139 
6    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:445 
7    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:8000 
8    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
9    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:49531 
10   ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:1720

my UDP ones:
> 1    ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:137 
2    ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:138 
3    ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:443 


I am running a virtual win7 host on my server as well...and this is my ifconfig:

> br0       Link encap:Ethernet  HWaddr 00:25:90:0B:1C:26  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:90ff:fe0b:1c26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5988 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1248508 (1.1 Mb)  TX bytes:1904878 (1.8 Mb)

eth0      Link encap:Ethernet  HWaddr 00:25:90:0B:1C:26  
          inet6 addr: fe80::225:90ff:fe0b:1c26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7628 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6759152 (6.4 Mb)  TX bytes:2673370 (2.5 Mb)
          Interrupt:16 Memory:fb5e0000-fb600000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:265 errors:0 dropped:0 overruns:0 frame:0
          TX packets:265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22968 (22.4 Kb)  TX bytes:22968 (22.4 Kb)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.168.10.1  P-t-P:192.168.10.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:423 (423.0 b)  TX bytes:0 (0.0 b)

virbr0    Link encap:Ethernet  HWaddr DA:17:D3:F1:C9:17  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:13202 (12.8 Kb)

vnet0     Link encap:Ethernet  HWaddr FE:54:00:FE:8F:91  
          inet6 addr: fe80::fc54:ff:fefe:8f91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:585 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15616 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:101446 (99.0 Kb)  TX bytes:5285829 (5.0 Mb)

vnet1     Link encap:Ethernet  HWaddr FE:54:00:06:67:7A  
          inet6 addr: fe80::fc54:ff:fe06:677a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:872158 (851.7 Kb)  TX bytes:5173377 (4.9 Mb)


I appreciate if you could help. This is killing me.

Kind Regards,

Dan

---

### Post by ryukent on 2011-10-29
Has anyone successfully managed to get VPNTunnel.se set up with Ubuntu. I can connect but a lot of pages like gmail and paypal don't work.

---

### Post by lightwarrior on 2011-10-29
Excellent iptables and vpn thread!

---

### Post by pvocong on 2012-02-22
Hello,

Thank you very much for the indications. I have spent 3 days to figure out what's happening with openvpn not being able to browse the web.
Desktop Ubuntu 10.4 LTS; ISP Box (France).
Just following the rules for iptables and launching openvpn by command line, and here I am with VPN. I am using it right now.
 :popcorn:

Cheers

---

### Post by undecidable on 2012-03-16
For simple humans (like me) who want to keep firestarter but who will understand iptables about 3 weeks after hell grows cold:

"Firestarter 1.0 does not support VPN configurations without some tweaking. VPN capability in Firestarter is currently planned for version 1.1."
11.04 has Firestarter 1.0.3

To fix for open vpn, copy the lines below and paste them into the /etc/firestarter/user-pre file on the firewall host (likely your client machine for a simple setup)
```
# Allow traffic on the OpenVPN inteface
$IPT -A INPUT -i tun+ -j ACCEPT
$IPT -A OUTPUT -o tun+ -j ACCEPT
```

Then restart firestarter with:
```
sudo /etc/firestarter/firestarter.sh stop
sudo /etc/firestarter/firestarter.sh start
```

---

### Post by spynappels on 2012-03-16
> **undecidable said:**
> For simple humans (like me) who want to keep firestarter but who will understand iptables about 3 weeks after hell grows cold:

"Firestarter 1.0 does not support VPN configurations without some tweaking. VPN capability in Firestarter is currently planned for version 1.1."
11.04 has Firestarter 1.0.3


Firestarter is no longer maintained, so you may understand iptables about 3 weeks before version 1.1 is released.

---

### Post by undecidable on 2012-03-19
ahhhhhhhhhhhhhh.  My head is full.
though in fact it may be easier to learn iptables than to keep learning new firewalls  (10.10 we had guarddog).

---

### Post by Biblioclasta on 2012-12-22
Thanks!
This fixed for me

> **pi3ch said:**
> The other piece of cake solution is to 

[LIST=1]
[*]Import your VPN config file in NetworkManager
[*]Edit the VPN connection
[*]Go to IP Settings tab (IP4Settings)
[*]Click on Routes
[*]Check "Use this connection only for resources on its network"
[*]Restart the connection.
[/LIST]
This will no allow the VPN connection to mess up your routing table.

---

### Post by svaens on 2013-03-14
I had exactly the same problem.... 
I had been playing around with firewalls for other reasons ([http://ubuntuforums.org/showthread.php?t=345251](http://ubuntuforums.org/showthread.php?t=345251)) and had at some point installed firestarter. 
I played with it; it didn't help me; so I deleted all rules and left it alone. I had not thought it being installed would cause me grief. 
However, as soon as I uninstalled it, no longer have I this problem of not being able to connect via VPN (when using the Network Manager). 

```
PING 173.194.35.134 (173.194.35.134) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
```

Mind you, I didn't have this problem when using openvpn via the command line. What is the difference? Simply a bad combination of rules applied by both firestarter and the network manager? Except .... firestarter does not simply add rules to ufw.... it is its own firewall....

---

### Post by undecidable on 2013-07-03
> The other piece of cake solution is to
 1.   Import your VPN config file in NetworkManager
 2.   Edit the VPN connection
 3.   Go to IP Settings tab (IP4Settings)
 4.   Click on Routes
 5.   Check "Use this connection only for resources on its network"
 6.   Restart the connection.
This will no allow the VPN connection to mess up your routing table.

I am not completely sure of this, but I think that procedure defeats 2 of the 3 purposes of a VPN.

If you are using the VPN just to access a company or private network - then that method is fine.

If you are using a VPN to protect your internet access when you are in a hotel / coffee shop / airport or other untrusted location, that method will defeat the VPN.  It means you are not using the VPN for general browsing / email access etc.  

If you are using a VPN  to access geo-restricted sites in another country, that method will defeat the VPN also for the same reason.

---

### Post by undecidable on 2013-07-03
> **svaens said:**
>  
Mind you, I didn't have this problem when using openvpn via the command line. What is the difference? Simply a bad combination of rules applied by both firestarter and the network manager? Except .... firestarter does not simply add rules to ufw.... it is its own firewall....

A few thoughts:
a. Firewall  is not its own firewall - it is another gui interface to iptables.  
b. I tried briefly to get kvpnc to work - but couldn't get it to work - can't remember why.  So I use openvpn via the command line. 
c. I tried briefly to integrate my openvpn into Network Manager - but couldn't get it to work either - can't remember why.  So stuck with the cli.  
d.  Even using the cli I did need to do the procedure I outlined in the post above to get through firestarter. 
[http://ubuntuforums.org/showthread.php?t=1660520&p=11770091#post11770091]("http://ubuntuforums.org/showthread.php?t=1660520&p=11770091#post11770091")
 to get through the firewall

For those new to Linux who may be unsure about using the command line, the command is just:
```
sudo /etc/init.d/openvpn start <configfile>.conf
sudo /etc/init.d/openvpn stop <configfile>.conf
```

to reduce typing I create aliases for these:
```
alias vstart='sudo /etc/init.d/openvpn start'
alias vstop='sudo /etc/init.d/openvpn stop'
```

so I just need to type each time:
```
vstart <configfile>.conf
vstop <configfile>.conf
```

---

### Post by umor on 2014-03-08
The following solution solved the problem of no data trasfer after successfull connection to vpn-server for me (ubuntu 13.10). Thank you pi3ch!

> **pi3ch said:**
> The other piece of cake solution is to 

[LIST=1]
[*]Import your VPN config file in NetworkManager
[*]Edit the VPN connection
[*]Go to IP Settings tab (IP4Settings)
[*]Click on Routes
[*]Check "Use this connection only for resources on its network"
[*]Restart the connection.
[/LIST]
This will no allow the VPN connection to mess up your routing table.

---

### Post by matija5 on 2014-10-23
This solutin also worked for me (Ubuntu 14.04 LTS)!!!

> **pi3ch said:**
> The other piece of cake solution is to 

[LIST=1]
[*]Import your VPN config file in NetworkManager 
[*]Edit the VPN connection 
[*]Go to IP Settings tab (IP4Settings) 
[*]Click on Routes 
[*]Check "Use this connection only for resources on its network" 
[*]Restart the connection. 
[/LIST]
This will no allow the VPN connection to mess up your routing table.

---

### Post by peterkuykendall-f on 2015-05-18
This "solution" defeats many aspects the VPN!  By having it route only traffic on it's network, any traffic that is destined for the Internet outside of the VPN server (99.999999% of the Internet) is in the clear.  This is very likely NOT what you want.

Fire up Wireshark or tcpdump to see for yourself.  You will see clear traffic going out, with little or nothing going down the VPN.

---

### Post by david300 on 2015-11-13
I know that this thread has been marked SOLVED but I found the following useful [http://arashmilani.com/post?id=53](http://arashmilani.com/post?id=53).Hope it helps/is relevant.

---

### Post by kent-3 on 2016-01-29
> **peterkuykendall-f said:**
> This "solution" defeats many aspects the VPN!  By having it route only traffic on it's network, any traffic that is destined for the Internet outside of the VPN server (99.999999% of the Internet) is in the clear.  This is very likely NOT what you want.

Fire up Wireshark or tcpdump to see for yourself.  You will see clear traffic going out, with little or nothing going down the VPN.

I was having this same problem on Linux Mint (connecting by VPN, internet worked for about a minute then stopped with "dns probe finished no internet" errors). I discovered what *may* be an easy, alternative solution, but I'm not sure if it might suffer from the same problem quoted.

I edited the connection, went to the IPV4, clicked Routes, and put a check next to "Ignore automatically obtained routes". 

Upon trying the connection again it stayed connected without DNS probe errors and "what's my IP" location test sites show the correct, remote IP and location. This suggests to me that my internet traffic is being routed through the remote location, but the quoted comment above made me question whether my connection will be secure if I'm using a public Wi-Fi hotspot when traveling. Anyone care to comment on that?

---

### Post by oldos2er on 2016-01-30
Linux Mint forums are [here]("http://forums.linuxmint.com/"). Since this thread references an old unsupported version of Ubuntu, I'm closing it.

---

