---
title: "OpenVPN can authenticate but not communicate"
date: 2012-02-23
forum: Server Platforms
---

### Post by RyanRahl on 2012-02-23
I have an OpenVPN server and I can connect to it just fine but I can not communicate with any other hosts on the network including the server. I can't ping from the server to an OpenVPN client, I can't ping from an OpenVPN client to the OpenVPN server, I can't ping from OpenVPN client to OpenVPN client or from OpenVPN client to normal LAN host and vise-versa. I am scratching my head on this one pretty hard because I have had no problems setting this up before and I basically copied the settings from a functioning OpenVPN server. I have even gone as far as to flush my iptables rules just to see if it will work and it still doesn't. 

Here is my config file:
```
port 1194
proto udp
dev tap0
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh1024.pem
ifconfig-pool-persist ipp.txt
server-bridge 192.168.49.1 255.255.255.0 192.168.49.150 192.168.49.200
server-bridge
client-to-client
keepalive 10 120
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 5
```

Here is my ifconfig:
```
br0       Link encap:Ethernet  HWaddr 00:30:18:a2:6e:b8  
          inet addr:192.168.49.1  Bcast:192.168.49.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fea2:6eb8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:1328 (1.3 KB)

eth0      Link encap:Ethernet  HWaddr 00:30:18:a2:6e:b7  
          inet addr:192.168.200.30  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fea2:6eb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1513 errors:0 dropped:0 overruns:0 frame:0
          TX packets:315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:154054 (154.0 KB)  TX bytes:39617 (39.6 KB)
          Interrupt:18 Memory:fe9e0000-fea00000 

eth1      Link encap:Ethernet  HWaddr 00:30:18:a2:6e:b8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:feae0000-feb00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 B)  TX bytes:600 (600.0 B)

mon.wlan0 Link encap:UNSPEC  HWaddr D4-9A-20-5A-DB-0C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7824 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:994555 (994.5 KB)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr d4:9a:20:5a:db:0c  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2592 (2.5 KB)

```

Here is my empty iptables [iptables -L -n]
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```

Here is openvpn messages from my syslog at level 6 verbosity while pinging from an OpenVPN client(tail -50 /var/log/syslog | grep ovpn):
```
Feb 23 11:24:20 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 WRITE [53] to [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:24:25 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [53] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:24:30 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 WRITE [53] to [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:24:35 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [53] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:24:40 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 WRITE [53] to [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:24:45 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [53] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:24:50 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 WRITE [53] to [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:24:55 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [53] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:25:00 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 WRITE [53] to [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:25:05 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [53] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:25:10 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 WRITE [53] to [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:25:16 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [53] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:25:20 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 WRITE [53] to [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:25:26 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [53] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:25:30 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 WRITE [53] to [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:25:36 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [53] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:25:40 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 WRITE [53] to [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:25:45 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [53] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:25:50 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 WRITE [53] to [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:25:56 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [53] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:26:00 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 WRITE [53] to [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:26:00 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [77] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=76
Feb 23 11:26:00 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 TUN WRITE [42]
Feb 23 11:26:01 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [77] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=76
Feb 23 11:26:01 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 TUN WRITE [42]
Feb 23 11:26:02 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [77] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=76
Feb 23 11:26:02 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 TUN WRITE [42]
Feb 23 11:26:03 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [77] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=76
Feb 23 11:26:03 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 TUN WRITE [42]
Feb 23 11:26:04 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [77] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=76
Feb 23 11:26:04 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 TUN WRITE [42]
Feb 23 11:26:05 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [77] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=76
Feb 23 11:26:05 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 TUN WRITE [42]
Feb 23 11:26:06 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [77] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=76
Feb 23 11:26:06 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 TUN WRITE [42]
Feb 23 11:26:07 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [77] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=76
Feb 23 11:26:07 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 TUN WRITE [42]
Feb 23 11:26:08 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [77] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=76
Feb 23 11:26:08 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 TUN WRITE [42]
Feb 23 11:26:09 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [77] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=76
Feb 23 11:26:09 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 TUN WRITE [42]
Feb 23 11:26:10 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [77] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=76
Feb 23 11:26:10 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 WRITE [53] to [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=52
Feb 23 11:26:10 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 TUN WRITE [42]
Feb 23 11:26:11 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [77] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=76
Feb 23 11:26:11 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 TUN WRITE [42]
Feb 23 11:26:12 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [77] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=76
Feb 23 11:26:12 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 TUN WRITE [42]
Feb 23 11:26:13 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 UDPv4 READ [77] from [AF_INET]192.168.200.101:60801: P_DATA_V1 kid=0 DATA len=76
Feb 23 11:26:13 chambersbaydental ovpn-server[3196]: admin-ryan/192.168.200.101:60801 TUN WRITE [42]
```

^^I thought this is a little weird because it refers to "TUN" instead of "TAP" when it is clear that I am using the "TAP" interface.

This is my client config (sorry about the xml. I copied it out of my settings in the Gnome network manager's OpenVPN module):
```
<?xml version="1.0"?>
<gconf>
	<entry name="key" mtime="1330024911" type="string">
		<stringvalue>/home/ryan/VPNKeys/cbdg/admin-ryan.key</stringvalue>
	</entry>
	<entry name="tap-dev" mtime="1330024911" type="string">
		<stringvalue>yes</stringvalue>
	</entry>
	<entry name="comp-lzo" mtime="1330024911" type="string">
		<stringvalue>yes</stringvalue>
	</entry>
	<entry name="connection-type" mtime="1330024911" type="string">
		<stringvalue>tls</stringvalue>
	</entry>
	<entry name="remote" mtime="1330024911" type="string">
		<stringvalue>192.168.200.30</stringvalue>
	</entry>
	<entry name="ca" mtime="1330024911" type="string">
		<stringvalue>/home/ryan/VPNKeys/cbdg/ca.crt</stringvalue>
	</entry>
	<entry name="cert" mtime="1330024911" type="string">
		<stringvalue>/home/ryan/VPNKeys/cbdg/admin-ryan.crt</stringvalue>
	</entry>
	<entry name="service-type" mtime="1330024911" type="string">
		<stringvalue>org.freedesktop.NetworkManager.openvpn</stringvalue>
	</entry>
</gconf>
```

here is a uname -a:
```
Linux chambersbaydental 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

If anyone has any ideas I would love to hear them. Thanks

---

### Post by RyanRahl on 2012-02-23
Ok I figured it out after proofreading my post. I had not configured my tap interface in my interfaces file to bridge to br0

You will see the difference here:
```
br0       Link encap:Ethernet  HWaddr 00:30:18:a2:6e:b8  
          inet addr:192.168.49.1  Bcast:192.168.49.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fea2:6eb8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4525 (4.5 KB)  TX bytes:748 (748.0 B)

eth0      Link encap:Ethernet  HWaddr 00:30:18:a2:6e:b7  
          inet addr:192.168.200.30  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fea2:6eb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27264 (27.2 KB)  TX bytes:19675 (19.6 KB)
          Interrupt:18 Memory:fe9e0000-fea00000 

eth1      Link encap:Ethernet  HWaddr 00:30:18:a2:6e:b8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:feae0000-feb00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1080 (1.0 KB)  TX bytes:1080 (1.0 KB)

mon.wlan0 Link encap:UNSPEC  HWaddr D4-9A-20-5A-DB-0C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44418 (44.4 KB)  TX bytes:0 (0.0 B)

tap0      Link encap:Ethernet  HWaddr aa:cd:8e:eb:00:cb  
          inet6 addr: fe80::a8cd:8eff:feeb:cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:4931 (4.9 KB)  TX bytes:1480 (1.4 KB)

wlan0     Link encap:Ethernet  HWaddr d4:9a:20:5a:db:0c  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5965 (5.9 KB)

```

now my interfaces file is:
```


# The loopback network interface
auto lo
iface lo inet loopback

# Internet Interface
auto eth0
iface eth0 inet dhcp

# LAN interface
auto eth1
iface eth1 inet manual

# Wireless interface AP mode (ssid chambersbay)
auto wlan0
iface wlan0 inet manual

# VPN interface
auto tap0
iface tap0 inet manual

# Internal Interface Bridge
auto br0
iface br0 inet static
address 	192.168.49.1
netmask 	255.255.255.0
network 	192.168.49.0
broadcast	192.168.49.255
bridge-ports	eth1 wlan0 tap0

```

Sorry for creating an erroneous thread.r

---

