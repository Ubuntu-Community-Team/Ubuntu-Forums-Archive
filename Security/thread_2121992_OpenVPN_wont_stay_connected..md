---
title: "OpenVPN wont stay connected."
date: 2013-03-03
forum: Security
---

### Post by squid636 on 2013-03-03
I am using a VPN service called PrivatVPN which has you install openvpn.  I followed the directions and yet my connection keeps dropping after about a minute.  I am only losing my connection to the internet when it disconnects.  It will let not let me reconnect the VPN either.  I have ran multiple commands from the terminal without enabling the VPN, with the VPN enabled, and after the VPN loses it connection.  I see that my eth0 connection disappears from the routing table after I lose the VPN connection but I am not sure if that is the problem or how to fix it.  Thanks for any help you all can give.

**Before enabling the VPN service:**
```
netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.10.12.1      128.0.0.0       UG        0 0          0 tap0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
5.5.0.0         0.0.0.0         255.255.254.0   U         0 0          0 as0t0
5.5.2.0         0.0.0.0         255.255.254.0   U         0 0          0 as0t1
5.5.4.0         0.0.0.0         255.255.254.0   U         0 0          0 as0t2
5.5.6.0         0.0.0.0         255.255.254.0   U         0 0          0 as0t3
5.5.8.0         0.0.0.0         255.255.254.0   U         0 0          0 as0t4
5.5.10.0        0.0.0.0         255.255.254.0   U         0 0          0 as0t5
5.5.12.0        0.0.0.0         255.255.254.0   U         0 0          0 as0t6
5.5.14.0        0.0.0.0         255.255.254.0   U         0 0          0 as0t7
10.10.12.0      0.0.0.0         255.255.255.0   U         0 0          0 tap0
31.7.62.130     192.168.1.1     255.255.255.255 UGH       0 0          0 eth0
128.0.0.0       10.10.12.1      128.0.0.0       UG        0 0          0 tap0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
--------------------------------------------------------------------------------------------
ifconfig tap0
tap0      Link encap:Ethernet  HWaddr 42:65:15:cb:9b:09  
          inet addr:10.10.12.175  Bcast:10.10.12.255  Mask:255.255.255.0
          inet6 addr: fe80::4065:15ff:fecb:9b09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11327 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:6388791 (6.3 MB)  TX bytes:2239904 (2.2 MB)
--------------------------------------------------------------------------------------------
ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:14:d1:1a:d3:eb  
          inet addr:192.168.1.129  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:d1ff:fe1a:d3eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11588 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9697 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6845668 (6.8 MB)  TX bytes:3007289 (3.0 MB)
--------------------------------------------------------------------------------------------
ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:0d:08:4c:06:16  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
--------------------------------------------------------------------------------------------
ifconfig
as0t0     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.0.1  P-t-P:5.5.0.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t1     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.2.1  P-t-P:5.5.2.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t2     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.4.1  P-t-P:5.5.4.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t3     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.6.1  P-t-P:5.5.6.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t4     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.8.1  P-t-P:5.5.8.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t5     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.10.1  P-t-P:5.5.10.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t6     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.12.1  P-t-P:5.5.12.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t7     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.14.1  P-t-P:5.5.14.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:14:d1:1a:d3:eb  
          inet addr:192.168.1.129  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:d1ff:fe1a:d3eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9710 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6855439 (6.8 MB)  TX bytes:3012124 (3.0 MB)

eth1      Link encap:Ethernet  HWaddr 00:24:21:5b:4e:fb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:710 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:131257 (131.2 KB)  TX bytes:131257 (131.2 KB)

tap0      Link encap:Ethernet  HWaddr 42:65:15:cb:9b:09  
          inet addr:10.10.12.175  Bcast:10.10.12.255  Mask:255.255.255.0
          inet6 addr: fe80::4065:15ff:fecb:9b09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11449 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9447 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:6394977 (6.3 MB)  TX bytes:2246164 (2.2 MB)
--------------------------------------------------------------------------------------------
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.10.12.1      128.0.0.0       UG    0      0        0 tap0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
5.5.0.0         0.0.0.0         255.255.254.0   U     0      0        0 as0t0
5.5.2.0         0.0.0.0         255.255.254.0   U     0      0        0 as0t1
5.5.4.0         0.0.0.0         255.255.254.0   U     0      0        0 as0t2
5.5.6.0         0.0.0.0         255.255.254.0   U     0      0        0 as0t3
5.5.8.0         0.0.0.0         255.255.254.0   U     0      0        0 as0t4
5.5.10.0        0.0.0.0         255.255.254.0   U     0      0        0 as0t5
5.5.12.0        0.0.0.0         255.255.254.0   U     0      0        0 as0t6
5.5.14.0        0.0.0.0         255.255.254.0   U     0      0        0 as0t7
10.10.12.0      0.0.0.0         255.255.255.0   U     0      0        0 tap0
31.7.62.130     192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
128.0.0.0       10.10.12.1      128.0.0.0       UG    0      0        0 tap0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
--------------------------------------------------------------------------------------------
cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search hr.cox.net
--------------------------------------------------------------------------------------------
ping -c3 91.189.94.186
PING 91.189.94.186 (91.189.94.186) 56(84) bytes of data.
64 bytes from 91.189.94.186: icmp_req=1 ttl=51 time=142 ms
64 bytes from 91.189.94.186: icmp_req=2 ttl=51 time=144 ms
64 bytes from 91.189.94.186: icmp_req=3 ttl=51 time=146 ms

--- 91.189.94.186 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 142.665/144.460/146.603/1.655 ms
--------------------------------------------------------------------------------------------
ping -c3 ubuntuforums.com
PING ubuntuforums.com (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=1 ttl=51 time=142 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=2 ttl=51 time=145 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=3 ttl=51 time=142 ms

--- ubuntuforums.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 142.510/143.631/145.666/1.441 ms
--------------------------------------------------------------------------------------------
sudo iptables-save -c
# Generated by iptables-save v1.4.12 on Sun Mar  3 17:37:21 2013
*nat
:PREROUTING ACCEPT [29:3527]
:INPUT ACCEPT [29:3527]
:OUTPUT ACCEPT [1138:72434]
:POSTROUTING ACCEPT [1138:72434]
:AS0_DPFWD_TCP - [0:0]
:AS0_DPFWD_UDP - [0:0]
:AS0_NAT - [0:0]
:AS0_NAT_POST_REL_EST - [0:0]
:AS0_NAT_PRE - [0:0]
:AS0_NAT_PRE_REL_EST - [0:0]
:AS0_NAT_TEST - [0:0]
[0:0] -A PREROUTING -m state --state RELATED,ESTABLISHED -j AS0_NAT_PRE_REL_EST
[0:0] -A PREROUTING -d 192.168.1.129/32 -p udp -m udp --dport 1194 -m state --state NEW -j AS0_DPFWD_UDP
[0:0] -A PREROUTING -d 192.168.1.129/32 -p tcp -m tcp --dport 443 -m state --state NEW -j AS0_DPFWD_TCP
[0:0] -A POSTROUTING -m state --state RELATED,ESTABLISHED -j AS0_NAT_POST_REL_EST
[0:0] -A POSTROUTING -m mark --mark 0x2000000/0x2000000 -j AS0_NAT_PRE
[0:0] -A AS0_DPFWD_TCP -p tcp -j DNAT --to-destination 192.168.1.129:914
[0:0] -A AS0_DPFWD_TCP -j ACCEPT
[0:0] -A AS0_DPFWD_UDP -p udp -j DNAT --to-destination 192.168.1.129:918
[0:0] -A AS0_DPFWD_UDP -j ACCEPT
[0:0] -A AS0_NAT -o eth0 -j SNAT --to-source 192.168.1.129
[0:0] -A AS0_NAT -o tap0 -j SNAT --to-source 10.10.12.175
[0:0] -A AS0_NAT -j ACCEPT
[0:0] -A AS0_NAT_POST_REL_EST -j ACCEPT
[0:0] -A AS0_NAT_PRE -d 5.5.0.0/20 -j AS0_NAT_TEST
[0:0] -A AS0_NAT_PRE -d 192.168.0.0/16 -j AS0_NAT_TEST
[0:0] -A AS0_NAT_PRE -d 172.16.0.0/12 -j AS0_NAT_TEST
[0:0] -A AS0_NAT_PRE -d 10.0.0.0/8 -j AS0_NAT_TEST
[0:0] -A AS0_NAT_PRE -j AS0_NAT
[0:0] -A AS0_NAT_PRE_REL_EST -j ACCEPT
[0:0] -A AS0_NAT_TEST -o as0t+ -j ACCEPT
[0:0] -A AS0_NAT_TEST -d 5.5.0.0/20 -j ACCEPT
[0:0] -A AS0_NAT_TEST -j AS0_NAT
COMMIT
# Completed on Sun Mar  3 17:37:21 2013
# Generated by iptables-save v1.4.12 on Sun Mar  3 17:37:21 2013
*mangle
:PREROUTING ACCEPT [417:28815]
:INPUT ACCEPT [22123:13010935]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [19632:5118500]
:POSTROUTING ACCEPT [19651:5119272]
:AS0_MANGLE_PRE_REL_EST - [0:0]
:AS0_MANGLE_TUN - [0:0]
[21706:12982120] -A PREROUTING -m state --state RELATED,ESTABLISHED -j AS0_MANGLE_PRE_REL_EST
[0:0] -A PREROUTING -i as0t+ -j AS0_MANGLE_TUN
[21706:12982120] -A AS0_MANGLE_PRE_REL_EST -j ACCEPT
[0:0] -A AS0_MANGLE_TUN -j MARK --set-xmark 0x2000000/0xffffffff
[0:0] -A AS0_MANGLE_TUN -j ACCEPT
COMMIT
# Completed on Sun Mar  3 17:37:21 2013
# Generated by iptables-save v1.4.12 on Sun Mar  3 17:37:21 2013
*filter
:INPUT ACCEPT [74:5736]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [19634:5118681]
:AS0_ACCEPT - [0:0]
:AS0_IN - [0:0]
:AS0_IN_POST - [0:0]
:AS0_IN_PRE - [0:0]
:AS0_OUT - [0:0]
:AS0_OUT_LOCAL - [0:0]
:AS0_OUT_S2C - [0:0]
:AS0_WEBACCEPT - [0:0]
[21709:12982797] -A INPUT -m state --state RELATED,ESTABLISHED -j AS0_ACCEPT
[340:22402] -A INPUT -i lo -j AS0_ACCEPT
[0:0] -A INPUT -m mark --mark 0x2000000/0x2000000 -j AS0_IN_PRE
[0:0] -A INPUT -d 192.168.1.129/32 -p tcp -m state --state NEW -m tcp --dport 915 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p tcp -m state --state NEW -m tcp --dport 914 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p tcp -m state --state NEW -m tcp --dport 917 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p tcp -m state --state NEW -m tcp --dport 916 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p udp -m state --state NEW -m udp --dport 919 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p udp -m state --state NEW -m udp --dport 918 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p udp -m state --state NEW -m udp --dport 921 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p udp -m state --state NEW -m udp --dport 920 -j AS0_ACCEPT
[0:0] -A INPUT -m state --state RELATED,ESTABLISHED -j AS0_WEBACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p tcp -m state --state NEW -m tcp --dport 943 -j AS0_WEBACCEPT
[0:0] -A FORWARD -m state --state RELATED,ESTABLISHED -j AS0_ACCEPT
[0:0] -A FORWARD -m mark --mark 0x2000000/0x2000000 -j AS0_IN_PRE
[0:0] -A FORWARD -o as0t+ -j AS0_OUT_S2C
[0:0] -A OUTPUT -o as0t+ -j AS0_OUT_LOCAL
[22049:13005199] -A AS0_ACCEPT -j ACCEPT
[0:0] -A AS0_IN -d 5.5.0.1/32 -j ACCEPT
[0:0] -A AS0_IN -d 10.10.12.0/24 -j ACCEPT
[0:0] -A AS0_IN -d 192.168.1.0/24 -j ACCEPT
[0:0] -A AS0_IN -j AS0_IN_POST
[0:0] -A AS0_IN_POST -o as0t+ -j AS0_OUT
[0:0] -A AS0_IN_POST -j DROP
[0:0] -A AS0_IN_PRE -d 5.5.0.0/20 -j AS0_IN
[0:0] -A AS0_IN_PRE -d 192.168.0.0/16 -j AS0_IN
[0:0] -A AS0_IN_PRE -d 172.16.0.0/12 -j AS0_IN
[0:0] -A AS0_IN_PRE -d 10.0.0.0/8 -j AS0_IN
[0:0] -A AS0_IN_PRE -j ACCEPT
[0:0] -A AS0_OUT -j DROP
[0:0] -A AS0_OUT_LOCAL -p icmp -m icmp --icmp-type 5 -j DROP
[0:0] -A AS0_OUT_LOCAL -j ACCEPT
[0:0] -A AS0_OUT_S2C -j AS0_OUT
[0:0] -A AS0_WEBACCEPT -j ACCEPT
COMMIT
# Completed on Sun Mar  3 17:37:21 2013
```

**After enabling the VPN service:**
```
netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.10.12.1      128.0.0.0       UG        0 0          0 tap0
0.0.0.0         91.240.65.1     0.0.0.0         UG        0 0          0 tap1
5.5.0.0         0.0.0.0         255.255.254.0   U         0 0          0 as0t0
5.5.2.0         0.0.0.0         255.255.254.0   U         0 0          0 as0t1
5.5.4.0         0.0.0.0         255.255.254.0   U         0 0          0 as0t2
5.5.6.0         0.0.0.0         255.255.254.0   U         0 0          0 as0t3
5.5.8.0         0.0.0.0         255.255.254.0   U         0 0          0 as0t4
5.5.10.0        0.0.0.0         255.255.254.0   U         0 0          0 as0t5
5.5.12.0        0.0.0.0         255.255.254.0   U         0 0          0 as0t6
5.5.14.0        0.0.0.0         255.255.254.0   U         0 0          0 as0t7
10.10.12.0      0.0.0.0         255.255.255.0   U         0 0          0 tap0
31.7.62.130     192.168.1.1     255.255.255.255 UGH       0 0          0 eth0
91.240.64.18    192.168.1.1     255.255.255.255 UGH       0 0          0 eth0
91.240.65.0     0.0.0.0         255.255.255.224 U         0 0          0 tap1
128.0.0.0       10.10.12.1      128.0.0.0       UG        0 0          0 tap0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
--------------------------------------------------------------------------------------------
ifconfig tap0
tap0      Link encap:Ethernet  HWaddr 42:65:15:cb:9b:09  
          inet addr:10.10.12.175  Bcast:10.10.12.255  Mask:255.255.255.0
          inet6 addr: fe80::4065:15ff:fecb:9b09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11923 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:6442911 (6.4 MB)  TX bytes:2295156 (2.2 MB)
--------------------------------------------------------------------------------------------
ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:14:d1:1a:d3:eb  
          inet addr:192.168.1.129  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:d1ff:fe1a:d3eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12197 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10021 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6952961 (6.9 MB)  TX bytes:3094641 (3.0 MB)
--------------------------------------------------------------------------------------------
ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:0d:08:4c:06:16  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
--------------------------------------------------------------------------------------------
ifconfig
as0t0     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.0.1  P-t-P:5.5.0.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t1     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.2.1  P-t-P:5.5.2.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t2     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.4.1  P-t-P:5.5.4.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t3     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.6.1  P-t-P:5.5.6.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t4     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.8.1  P-t-P:5.5.8.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t5     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.10.1  P-t-P:5.5.10.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t6     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.12.1  P-t-P:5.5.12.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t7     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.14.1  P-t-P:5.5.14.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:14:d1:1a:d3:eb  
          inet addr:192.168.1.129  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:d1ff:fe1a:d3eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12255 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10033 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6963063 (6.9 MB)  TX bytes:3099205 (3.0 MB)

eth1      Link encap:Ethernet  HWaddr 00:24:21:5b:4e:fb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:799 errors:0 dropped:0 overruns:0 frame:0
          TX packets:799 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140214 (140.2 KB)  TX bytes:140214 (140.2 KB)

tap0      Link encap:Ethernet  HWaddr 42:65:15:cb:9b:09  
          inet addr:10.10.12.175  Bcast:10.10.12.255  Mask:255.255.255.0
          inet6 addr: fe80::4065:15ff:fecb:9b09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12029 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:6456166 (6.4 MB)  TX bytes:2302564 (2.3 MB)

tap1      Link encap:Ethernet  HWaddr 16:f9:90:d8:ad:28  
          inet addr:91.240.65.14  Bcast:91.240.65.31  Mask:255.255.255.224
          inet6 addr: fe80::14f9:90ff:fed8:ad28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:42 (42.0 B)  TX bytes:7586 (7.5 KB)
--------------------------------------------------------------------------------------------
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.10.12.1      128.0.0.0       UG    0      0        0 tap0
0.0.0.0         91.240.65.1     0.0.0.0         UG    0      0        0 tap1
5.5.0.0         0.0.0.0         255.255.254.0   U     0      0        0 as0t0
5.5.2.0         0.0.0.0         255.255.254.0   U     0      0        0 as0t1
5.5.4.0         0.0.0.0         255.255.254.0   U     0      0        0 as0t2
5.5.6.0         0.0.0.0         255.255.254.0   U     0      0        0 as0t3
5.5.8.0         0.0.0.0         255.255.254.0   U     0      0        0 as0t4
5.5.10.0        0.0.0.0         255.255.254.0   U     0      0        0 as0t5
5.5.12.0        0.0.0.0         255.255.254.0   U     0      0        0 as0t6
5.5.14.0        0.0.0.0         255.255.254.0   U     0      0        0 as0t7
10.10.12.0      0.0.0.0         255.255.255.0   U     0      0        0 tap0
31.7.62.130     192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
91.240.64.18    192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
91.240.65.0     0.0.0.0         255.255.255.224 U     0      0        0 tap1
128.0.0.0       10.10.12.1      128.0.0.0       UG    0      0        0 tap0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
--------------------------------------------------------------------------------------------
cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search hr.cox.net
--------------------------------------------------------------------------------------------
ping -c3 91.189.94.186
PING 91.189.94.186 (91.189.94.186) 56(84) bytes of data.
64 bytes from 91.189.94.186: icmp_req=1 ttl=51 time=142 ms
64 bytes from 91.189.94.186: icmp_req=2 ttl=51 time=142 ms
64 bytes from 91.189.94.186: icmp_req=3 ttl=51 time=141 ms

--- 91.189.94.186 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 141.142/142.086/142.863/0.776 ms
--------------------------------------------------------------------------------------------
ping -c3 ubuntuforums.com
PING ubuntuforums.com (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=1 ttl=51 time=145 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=2 ttl=51 time=151 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=3 ttl=51 time=142 ms

--- ubuntuforums.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 142.028/146.338/151.435/3.892 ms
--------------------------------------------------------------------------------------------
sudo iptables-save -c
# Generated by iptables-save v1.4.12 on Sun Mar  3 17:39:27 2013
*nat
:PREROUTING ACCEPT [31:3683]
:INPUT ACCEPT [31:3683]
:OUTPUT ACCEPT [1235:78784]
:POSTROUTING ACCEPT [1235:78784]
:AS0_DPFWD_TCP - [0:0]
:AS0_DPFWD_UDP - [0:0]
:AS0_NAT - [0:0]
:AS0_NAT_POST_REL_EST - [0:0]
:AS0_NAT_PRE - [0:0]
:AS0_NAT_PRE_REL_EST - [0:0]
:AS0_NAT_TEST - [0:0]
[0:0] -A PREROUTING -m state --state RELATED,ESTABLISHED -j AS0_NAT_PRE_REL_EST
[0:0] -A PREROUTING -d 192.168.1.129/32 -p udp -m udp --dport 1194 -m state --state NEW -j AS0_DPFWD_UDP
[0:0] -A PREROUTING -d 192.168.1.129/32 -p tcp -m tcp --dport 443 -m state --state NEW -j AS0_DPFWD_TCP
[0:0] -A POSTROUTING -m state --state RELATED,ESTABLISHED -j AS0_NAT_POST_REL_EST
[0:0] -A POSTROUTING -m mark --mark 0x2000000/0x2000000 -j AS0_NAT_PRE
[0:0] -A AS0_DPFWD_TCP -p tcp -j DNAT --to-destination 192.168.1.129:914
[0:0] -A AS0_DPFWD_TCP -j ACCEPT
[0:0] -A AS0_DPFWD_UDP -p udp -j DNAT --to-destination 192.168.1.129:918
[0:0] -A AS0_DPFWD_UDP -j ACCEPT
[0:0] -A AS0_NAT -o eth0 -j SNAT --to-source 192.168.1.129
[0:0] -A AS0_NAT -o tap0 -j SNAT --to-source 10.10.12.175
[0:0] -A AS0_NAT -j ACCEPT
[0:0] -A AS0_NAT_POST_REL_EST -j ACCEPT
[0:0] -A AS0_NAT_PRE -d 5.5.0.0/20 -j AS0_NAT_TEST
[0:0] -A AS0_NAT_PRE -d 192.168.0.0/16 -j AS0_NAT_TEST
[0:0] -A AS0_NAT_PRE -d 172.16.0.0/12 -j AS0_NAT_TEST
[0:0] -A AS0_NAT_PRE -d 10.0.0.0/8 -j AS0_NAT_TEST
[0:0] -A AS0_NAT_PRE -j AS0_NAT
[0:0] -A AS0_NAT_PRE_REL_EST -j ACCEPT
[0:0] -A AS0_NAT_TEST -o as0t+ -j ACCEPT
[0:0] -A AS0_NAT_TEST -d 5.5.0.0/20 -j ACCEPT
[0:0] -A AS0_NAT_TEST -j AS0_NAT
COMMIT
# Completed on Sun Mar  3 17:39:27 2013
# Generated by iptables-save v1.4.12 on Sun Mar  3 17:39:27 2013
*mangle
:PREROUTING ACCEPT [480:35282]
:INPUT ACCEPT [23024:13167414]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [20291:5245293]
:POSTROUTING ACCEPT [20326:5249647]
:AS0_MANGLE_PRE_REL_EST - [0:0]
:AS0_MANGLE_TUN - [0:0]
[22698:13148302] -A PREROUTING -m state --state RELATED,ESTABLISHED -j AS0_MANGLE_PRE_REL_EST
[0:0] -A PREROUTING -i as0t+ -j AS0_MANGLE_TUN
[22698:13148302] -A AS0_MANGLE_PRE_REL_EST -j ACCEPT
[0:0] -A AS0_MANGLE_TUN -j MARK --set-xmark 0x2000000/0xffffffff
[0:0] -A AS0_MANGLE_TUN -j ACCEPT
COMMIT
# Completed on Sun Mar  3 17:39:27 2013
# Generated by iptables-save v1.4.12 on Sun Mar  3 17:39:27 2013
*filter
:INPUT ACCEPT [94:9534]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [20293:5245474]
:AS0_ACCEPT - [0:0]
:AS0_IN - [0:0]
:AS0_IN_POST - [0:0]
:AS0_IN_PRE - [0:0]
:AS0_OUT - [0:0]
:AS0_OUT_LOCAL - [0:0]
:AS0_OUT_S2C - [0:0]
:AS0_WEBACCEPT - [0:0]
[22547:13132809] -A INPUT -m state --state RELATED,ESTABLISHED -j AS0_ACCEPT
[383:25071] -A INPUT -i lo -j AS0_ACCEPT
[0:0] -A INPUT -m mark --mark 0x2000000/0x2000000 -j AS0_IN_PRE
[0:0] -A INPUT -d 192.168.1.129/32 -p tcp -m state --state NEW -m tcp --dport 915 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p tcp -m state --state NEW -m tcp --dport 914 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p tcp -m state --state NEW -m tcp --dport 917 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p tcp -m state --state NEW -m tcp --dport 916 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p udp -m state --state NEW -m udp --dport 919 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p udp -m state --state NEW -m udp --dport 918 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p udp -m state --state NEW -m udp --dport 921 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p udp -m state --state NEW -m udp --dport 920 -j AS0_ACCEPT
[0:0] -A INPUT -m state --state RELATED,ESTABLISHED -j AS0_WEBACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p tcp -m state --state NEW -m tcp --dport 943 -j AS0_WEBACCEPT
[0:0] -A FORWARD -m state --state RELATED,ESTABLISHED -j AS0_ACCEPT
[0:0] -A FORWARD -m mark --mark 0x2000000/0x2000000 -j AS0_IN_PRE
[0:0] -A FORWARD -o as0t+ -j AS0_OUT_S2C
[0:0] -A OUTPUT -o as0t+ -j AS0_OUT_LOCAL
[22930:13157880] -A AS0_ACCEPT -j ACCEPT
[0:0] -A AS0_IN -d 5.5.0.1/32 -j ACCEPT
[0:0] -A AS0_IN -d 10.10.12.0/24 -j ACCEPT
[0:0] -A AS0_IN -d 192.168.1.0/24 -j ACCEPT
[0:0] -A AS0_IN -j AS0_IN_POST
[0:0] -A AS0_IN_POST -o as0t+ -j AS0_OUT
[0:0] -A AS0_IN_POST -j DROP
[0:0] -A AS0_IN_PRE -d 5.5.0.0/20 -j AS0_IN
[0:0] -A AS0_IN_PRE -d 192.168.0.0/16 -j AS0_IN
[0:0] -A AS0_IN_PRE -d 172.16.0.0/12 -j AS0_IN
[0:0] -A AS0_IN_PRE -d 10.0.0.0/8 -j AS0_IN
[0:0] -A AS0_IN_PRE -j ACCEPT
[0:0] -A AS0_OUT -j DROP
[0:0] -A AS0_OUT_LOCAL -p icmp -m icmp --icmp-type 5 -j DROP
[0:0] -A AS0_OUT_LOCAL -j ACCEPT
[0:0] -A AS0_OUT_S2C -j AS0_OUT
[0:0] -A AS0_WEBACCEPT -j ACCEPT
COMMIT
# Completed on Sun Mar  3 17:39:27 2013
```

**After losing the VPN service and not being able to reconnect:**
```
netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.10.12.1      128.0.0.0       UG        0 0          0 tap0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
5.5.0.0         0.0.0.0         255.255.254.0   U         0 0          0 as0t0
5.5.2.0         0.0.0.0         255.255.254.0   U         0 0          0 as0t1
5.5.4.0         0.0.0.0         255.255.254.0   U         0 0          0 as0t2
5.5.6.0         0.0.0.0         255.255.254.0   U         0 0          0 as0t3
5.5.8.0         0.0.0.0         255.255.254.0   U         0 0          0 as0t4
5.5.10.0        0.0.0.0         255.255.254.0   U         0 0          0 as0t5
5.5.12.0        0.0.0.0         255.255.254.0   U         0 0          0 as0t6
5.5.14.0        0.0.0.0         255.255.254.0   U         0 0          0 as0t7
10.10.12.0      0.0.0.0         255.255.255.0   U         0 0          0 tap0
128.0.0.0       10.10.12.1      128.0.0.0       UG        0 0          0 tap0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
--------------------------------------------------------------------------------------------
ifconfig tap0
tap0      Link encap:Ethernet  HWaddr 42:65:15:cb:9b:09  
          inet addr:10.10.12.175  Bcast:10.10.12.255  Mask:255.255.255.0
          inet6 addr: fe80::4065:15ff:fecb:9b09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12359 errors:0 dropped:0 overruns:0 frame:0
          TX packets:286220 errors:0 dropped:272206 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:6492348 (6.4 MB)  TX bytes:416418013 (416.4 MB)
--------------------------------------------------------------------------------------------
ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:14:d1:1a:d3:eb  
          inet addr:192.168.1.129  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:d1ff:fe1a:d3eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7133802 (7.1 MB)  TX bytes:3127404 (3.1 MB)
--------------------------------------------------------------------------------------------
ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:0d:08:4c:06:16  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
--------------------------------------------------------------------------------------------
ifconfig
as0t0     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.0.1  P-t-P:5.5.0.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t1     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.2.1  P-t-P:5.5.2.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t2     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.4.1  P-t-P:5.5.4.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t3     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.6.1  P-t-P:5.5.6.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t4     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.8.1  P-t-P:5.5.8.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t5     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.10.1  P-t-P:5.5.10.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t6     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.12.1  P-t-P:5.5.12.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as0t7     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.5.14.1  P-t-P:5.5.14.1  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:14:d1:1a:d3:eb  
          inet addr:192.168.1.129  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:d1ff:fe1a:d3eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7133802 (7.1 MB)  TX bytes:3127404 (3.1 MB)

eth1      Link encap:Ethernet  HWaddr 00:24:21:5b:4e:fb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9401 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:906903 (906.9 KB)  TX bytes:906903 (906.9 KB)

tap0      Link encap:Ethernet  HWaddr 42:65:15:cb:9b:09  
          inet addr:10.10.12.175  Bcast:10.10.12.255  Mask:255.255.255.0
          inet6 addr: fe80::4065:15ff:fecb:9b09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12359 errors:0 dropped:0 overruns:0 frame:0
          TX packets:286238 errors:0 dropped:272206 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:6492348 (6.4 MB)  TX bytes:416418769 (416.4 MB)
--------------------------------------------------------------------------------------------
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.10.12.1      128.0.0.0       UG    0      0        0 tap0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
5.5.0.0         0.0.0.0         255.255.254.0   U     0      0        0 as0t0
5.5.2.0         0.0.0.0         255.255.254.0   U     0      0        0 as0t1
5.5.4.0         0.0.0.0         255.255.254.0   U     0      0        0 as0t2
5.5.6.0         0.0.0.0         255.255.254.0   U     0      0        0 as0t3
5.5.8.0         0.0.0.0         255.255.254.0   U     0      0        0 as0t4
5.5.10.0        0.0.0.0         255.255.254.0   U     0      0        0 as0t5
5.5.12.0        0.0.0.0         255.255.254.0   U     0      0        0 as0t6
5.5.14.0        0.0.0.0         255.255.254.0   U     0      0        0 as0t7
10.10.12.0      0.0.0.0         255.255.255.0   U     0      0        0 tap0
128.0.0.0       10.10.12.1      128.0.0.0       UG    0      0        0 tap0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
--------------------------------------------------------------------------------------------
cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search hr.cox.net
--------------------------------------------------------------------------------------------
ping -c3 91.189.94.186
PING 91.189.94.186 (91.189.94.186) 56(84) bytes of data.
From 10.10.12.175 icmp_seq=1 Destination Host Unreachable
From 10.10.12.175 icmp_seq=2 Destination Host Unreachable
From 10.10.12.175 icmp_seq=3 Destination Host Unreachable

--- 91.189.94.186 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2015ms
pipe 3
--------------------------------------------------------------------------------------------
ping -c3 ubuntuforums.com
ping: unknown host ubuntuforums.com
--------------------------------------------------------------------------------------------
sudo iptables-save -c
# Generated by iptables-save v1.4.12 on Sun Mar  3 18:23:16 2013
*nat
:PREROUTING ACCEPT [64:7819]
:INPUT ACCEPT [64:7819]
:OUTPUT ACCEPT [5532:368787]
:POSTROUTING ACCEPT [5532:368787]
:AS0_DPFWD_TCP - [0:0]
:AS0_DPFWD_UDP - [0:0]
:AS0_NAT - [0:0]
:AS0_NAT_POST_REL_EST - [0:0]
:AS0_NAT_PRE - [0:0]
:AS0_NAT_PRE_REL_EST - [0:0]
:AS0_NAT_TEST - [0:0]
[0:0] -A PREROUTING -m state --state RELATED,ESTABLISHED -j AS0_NAT_PRE_REL_EST
[0:0] -A PREROUTING -d 192.168.1.129/32 -p udp -m udp --dport 1194 -m state --state NEW -j AS0_DPFWD_UDP
[0:0] -A PREROUTING -d 192.168.1.129/32 -p tcp -m tcp --dport 443 -m state --state NEW -j AS0_DPFWD_TCP
[0:0] -A POSTROUTING -m state --state RELATED,ESTABLISHED -j AS0_NAT_POST_REL_EST
[0:0] -A POSTROUTING -m mark --mark 0x2000000/0x2000000 -j AS0_NAT_PRE
[0:0] -A AS0_DPFWD_TCP -p tcp -j DNAT --to-destination 192.168.1.129:914
[0:0] -A AS0_DPFWD_TCP -j ACCEPT
[0:0] -A AS0_DPFWD_UDP -p udp -j DNAT --to-destination 192.168.1.129:918
[0:0] -A AS0_DPFWD_UDP -j ACCEPT
[0:0] -A AS0_NAT -o eth0 -j SNAT --to-source 192.168.1.129
[0:0] -A AS0_NAT -o tap0 -j SNAT --to-source 10.10.12.175
[0:0] -A AS0_NAT -j ACCEPT
[0:0] -A AS0_NAT_POST_REL_EST -j ACCEPT
[0:0] -A AS0_NAT_PRE -d 5.5.0.0/20 -j AS0_NAT_TEST
[0:0] -A AS0_NAT_PRE -d 192.168.0.0/16 -j AS0_NAT_TEST
[0:0] -A AS0_NAT_PRE -d 172.16.0.0/12 -j AS0_NAT_TEST
[0:0] -A AS0_NAT_PRE -d 10.0.0.0/8 -j AS0_NAT_TEST
[0:0] -A AS0_NAT_PRE -j AS0_NAT
[0:0] -A AS0_NAT_PRE_REL_EST -j ACCEPT
[0:0] -A AS0_NAT_TEST -o as0t+ -j ACCEPT
[0:0] -A AS0_NAT_TEST -d 5.5.0.0/20 -j ACCEPT
[0:0] -A AS0_NAT_TEST -j AS0_NAT
COMMIT
# Completed on Sun Mar  3 18:23:16 2013
# Generated by iptables-save v1.4.12 on Sun Mar  3 18:23:16 2013
*mangle
:PREROUTING ACCEPT [2677:187427]
:INPUT ACCEPT [32056:13988501]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [310470:437826329]
:POSTROUTING ACCEPT [310523:437834105]
:AS0_MANGLE_PRE_REL_EST - [0:0]
:AS0_MANGLE_TUN - [0:0]
[30213:13911820] -A PREROUTING -m state --state RELATED,ESTABLISHED -j AS0_MANGLE_PRE_REL_EST
[0:0] -A PREROUTING -i as0t+ -j AS0_MANGLE_TUN
[30213:13911820] -A AS0_MANGLE_PRE_REL_EST -j ACCEPT
[0:0] -A AS0_MANGLE_TUN -j MARK --set-xmark 0x2000000/0xffffffff
[0:0] -A AS0_MANGLE_TUN -j ACCEPT
COMMIT
# Completed on Sun Mar  3 18:23:16 2013
# Generated by iptables-save v1.4.12 on Sun Mar  3 18:23:16 2013
*filter
:INPUT ACCEPT [178:18688]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [310472:437826510]
:AS0_ACCEPT - [0:0]
:AS0_IN - [0:0]
:AS0_IN_POST - [0:0]
:AS0_IN_PRE - [0:0]
:AS0_OUT - [0:0]
:AS0_OUT_LOCAL - [0:0]
:AS0_OUT_S2C - [0:0]
:AS0_WEBACCEPT - [0:0]
[29382:13801751] -A INPUT -m state --state RELATED,ESTABLISHED -j AS0_ACCEPT
[2496:168062] -A INPUT -i lo -j AS0_ACCEPT
[0:0] -A INPUT -m mark --mark 0x2000000/0x2000000 -j AS0_IN_PRE
[0:0] -A INPUT -d 192.168.1.129/32 -p tcp -m state --state NEW -m tcp --dport 915 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p tcp -m state --state NEW -m tcp --dport 914 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p tcp -m state --state NEW -m tcp --dport 917 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p tcp -m state --state NEW -m tcp --dport 916 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p udp -m state --state NEW -m udp --dport 919 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p udp -m state --state NEW -m udp --dport 918 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p udp -m state --state NEW -m udp --dport 921 -j AS0_ACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p udp -m state --state NEW -m udp --dport 920 -j AS0_ACCEPT
[0:0] -A INPUT -m state --state RELATED,ESTABLISHED -j AS0_WEBACCEPT
[0:0] -A INPUT -d 192.168.1.129/32 -p tcp -m state --state NEW -m tcp --dport 943 -j AS0_WEBACCEPT
[0:0] -A FORWARD -m state --state RELATED,ESTABLISHED -j AS0_ACCEPT
[0:0] -A FORWARD -m mark --mark 0x2000000/0x2000000 -j AS0_IN_PRE
[0:0] -A FORWARD -o as0t+ -j AS0_OUT_S2C
[0:0] -A OUTPUT -o as0t+ -j AS0_OUT_LOCAL
[31878:13969813] -A AS0_ACCEPT -j ACCEPT
[0:0] -A AS0_IN -d 5.5.0.1/32 -j ACCEPT
[0:0] -A AS0_IN -d 10.10.12.0/24 -j ACCEPT
[0:0] -A AS0_IN -d 192.168.1.0/24 -j ACCEPT
[0:0] -A AS0_IN -j AS0_IN_POST
[0:0] -A AS0_IN_POST -o as0t+ -j AS0_OUT
[0:0] -A AS0_IN_POST -j DROP
[0:0] -A AS0_IN_PRE -d 5.5.0.0/20 -j AS0_IN
[0:0] -A AS0_IN_PRE -d 192.168.0.0/16 -j AS0_IN
[0:0] -A AS0_IN_PRE -d 172.16.0.0/12 -j AS0_IN
[0:0] -A AS0_IN_PRE -d 10.0.0.0/8 -j AS0_IN
[0:0] -A AS0_IN_PRE -j ACCEPT
[0:0] -A AS0_OUT -j DROP
[0:0] -A AS0_OUT_LOCAL -p icmp -m icmp --icmp-type 5 -j DROP
[0:0] -A AS0_OUT_LOCAL -j ACCEPT
[0:0] -A AS0_OUT_S2C -j AS0_OUT
[0:0] -A AS0_WEBACCEPT -j ACCEPT
COMMIT
# Completed on Sun Mar  3 18:23:16 2013
```

---

### Post by jdthood on 2013-03-04
Try disabling avahi.

---

### Post by squid636 on 2013-03-04
I found the issue.  Upon boot openvpn was starting on its own and connecting to my vpn without any interaction from me.  Since I want to have the ability to turn it on and off that didnt work for me.  By renaming this file 

```
/etc/init.d/openvpn
```

 and restarting everything is working as it use to.

---

