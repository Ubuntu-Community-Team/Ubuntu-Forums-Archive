---
title: "OpenVPN internet access problem"
date: 2013-01-11
forum: Server Platforms
---

### Post by peterhkd on 2013-01-11
Hello Ubuntu Forum members ):P ! im a Debian user. And this forum is so active, i decided to ask help here. 

So i want an openvpn server on my rig. And i followed many howto's started by howtoforge's "openvpn gaming trough firewalls" my openvpn server connects and i can ping the servers ip address .
The Dns is alrgiht i can tacert (win7 traceroute) any domain and the cmd will say the ip of the host. But no data came trouge just the servers local apache website's. i will now post here the config
and what i can. please help me find the bug in my conf so i can connect trough my server. thank you!


#ifconfig
```
root@plehr:/home/plehr# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:84:99:b7
          inet addr:193.169.16.200  Bcast:193.169.16.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe84:99b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25810961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43424400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10426532739 (9.7 GiB)  TX bytes:19545906078 (18.2 GiB)
          Interrupt:25 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:328268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:198829075 (189.6 MiB)  TX bytes:198829075 (189.6 MiB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.0.0.1  P-t-P:10.0.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:36888 (36.0 KiB)  TX bytes:25304 (24.7 KiB)
```

#route -n
```
root@plehr:/home/plehr# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.2        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
10.0.0.0        10.0.0.2        255.255.255.0   UG    0      0        0 tun0
193.169.16.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         193.169.16.1    0.0.0.0         UG    0      0        0 eth0
```

#iptables -L -t nat
```
root@plehr:/home/plehr# iptables -L -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  all  --  10.0.0.0/24          anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

net.ipv4.ip_forward = 1
```
root@plehr:/home/plehr# cat /proc/sys/net/ipv4/ip_forward
1
```

Server OpenVpn conf
```
dev tun
proto tcp
port 31336


ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/server.crt
key /etc/openvpn/easy-rsa/keys/server.key
dh /etc/openvpn/easy-rsa/keys/dh1024.pem


server 10.0.0.0 255.255.255.0


persist-key
persist-tun


status /var/log/openvpn-status.log
verb 3

push "redirect-gateway def1"
#set the dns servers
push "dhcp-option DNS 10.0.0.1"


log-append /var/log/openvpn
comp-lzo
```

Windows 7 Client conf
```
client
dev tun
proto tcp
remote 193.169.16.200 31336
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert acerlaptop.crt
key acerlaptop.key
ns-cert-type server
comp-lzo
verb 3
redirect-gateway
route-method exe
route-delay 2
```

Windows Client Connection Log
```
Fri Jan 11 17:37:42 2013 OpenVPN 2.2.2 Win32-MSVC++ [SSL] [LZO2] [PKCS11] built on Dec 15 2011
Fri Jan 11 17:37:42 2013 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Fri Jan 11 17:37:42 2013 LZO compression initialized
Fri Jan 11 17:37:42 2013 Control Channel MTU parms [ L:1544 D:140 EF:40 EB:0 ET:0 EL:0 ]
Fri Jan 11 17:37:42 2013 Socket Buffers: R=[8192->8192] S=[8192->8192]
Fri Jan 11 17:37:42 2013 Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Fri Jan 11 17:37:42 2013 Local Options hash (VER=V4): '69109d17'
Fri Jan 11 17:37:42 2013 Expected Remote Options hash (VER=V4): 'c0103fa8'
Fri Jan 11 17:37:42 2013 Attempting to establish TCP connection with 193.169.16.200:31336
Fri Jan 11 17:37:43 2013 TCP connection established with 193.169.16.200:31336
Fri Jan 11 17:37:43 2013 TCPv4_CLIENT link local: [undef]
Fri Jan 11 17:37:43 2013 TCPv4_CLIENT link remote: 193.169.16.200:31336
Fri Jan 11 17:37:43 2013 TLS: Initial packet from 193.169.16.200:31336, sid=0435e304 df929c3d
Fri Jan 11 17:37:48 2013 VERIFY OK: 
Fri Jan 11 17:37:48 2013 VERIFY OK: nsCertType=SERVER
Fri Jan 11 17:37:48 2013 VERIFY OK: 
Fri Jan 11 17:37:59 2013 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Fri Jan 11 17:37:59 2013 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Jan 11 17:37:59 2013 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Fri Jan 11 17:37:59 2013 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Jan 11 17:37:59 2013 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Fri Jan 11 17:37:59 2013 [server] Peer Connection Initiated with 193.169.16.200:31336
Fri Jan 11 17:38:02 2013 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Fri Jan 11 17:38:02 2013 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway def1,dhcp-option DNS 10.0.0.1,route 10.0.0.1,topology net30,ifconfig 10.0.0.6 10.0.0.5'
Fri Jan 11 17:38:02 2013 OPTIONS IMPORT: --ifconfig/up options modified
Fri Jan 11 17:38:02 2013 OPTIONS IMPORT: route options modified
Fri Jan 11 17:38:02 2013 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Fri Jan 11 17:38:02 2013 ROUTE default_gateway=10.29.200.1
Fri Jan 11 17:38:02 2013 TAP-WIN32 device [plehrVPN] opened: \\.\Global\{0D914662-8A9B-4E34-9BF4-80A9C4CEBCE8}.tap
Fri Jan 11 17:38:02 2013 TAP-Win32 Driver Version 9.9 
Fri Jan 11 17:38:02 2013 TAP-Win32 MTU=1500
Fri Jan 11 17:38:02 2013 Notified TAP-Win32 driver to set a DHCP IP/netmask of 10.0.0.6/255.255.255.252 on interface {0D914662-8A9B-4E34-9BF4-80A9C4CEBCE8} [DHCP-serv: 10.0.0.5, lease-time: 31536000]
Fri Jan 11 17:38:02 2013 Successful ARP Flush on interface [18] {0D914662-8A9B-4E34-9BF4-80A9C4CEBCE8}
Fri Jan 11 17:38:04 2013 TEST ROUTES: 2/2 succeeded len=1 ret=1 a=0 u/d=up
Fri Jan 11 17:38:04 2013 C:\WINDOWS\system32\route.exe ADD 193.169.16.200 MASK 255.255.255.255 10.29.200.1
 OK!
Fri Jan 11 17:38:05 2013 C:\WINDOWS\system32\route.exe ADD 0.0.0.0 MASK 128.0.0.0 10.0.0.5
 OK!
Fri Jan 11 17:38:05 2013 C:\WINDOWS\system32\route.exe ADD 128.0.0.0 MASK 128.0.0.0 10.0.0.5
 OK!
Fri Jan 11 17:38:05 2013 C:\WINDOWS\system32\route.exe ADD 10.0.0.1 MASK 255.255.255.255 10.0.0.5
 OK!
Fri Jan 11 17:38:05 2013 Initialization Sequence Completed

```


Tracert from windows while connected to vpn
```
C: \ Users \ rena> tracert ubuntuforums.org

Tracing route: ubuntuforums.org [91.189.94.12]
a maximum of 30 hops:

** 1734 ms 756 ms 351 ms 10.0.0.1
** 2 *** Request not received a response within the time limit.

** 3 *** Request not received a response within the time limit.

** 4 *** Request not received a response within the time limit.
```

So that's all what i can Think of. what  info to provide. 
Need help  ;)  
Thank you!

---

### Post by SeijiSensei on 2013-01-11
I'm not sure I entirely understand the problem, but I'm guessing that connections to the outside from the VPN client do not go through the tunnel?  That's because the default route is specified to use your Internet router.  If you really want to push everything through the tunnel, it's a bit tricky to set up.  You'll need to make the other end of the tunnel the default gateway while still enabling a connection over the Internet between the two machines.  On Linux I'd run something like this:

```

sudo ip route add 193.169.16.200 via 193.169.16.1
sudo ip route del default
sudo ip route add default via 10.0.0.2

```

The first line tells the client to use the Internet router at .1 to reach the VPN server at .200.  The next two lines then replace the default route with one that uses the remote end of the tunnel as the gateway.

There must be an equivalent set of commands using route.exe in Windows.

---

### Post by peterhkd on 2013-01-11
Oww
As soon as i entered those lines.
```
sudo ip route add 193.169.16.200 via 193.169.16.1
sudo ip route del default
sudo ip route add default via 10.0.0.2
```

the server went offline!?

Yep offline plehr.hu i no more :(

Requested ipconsole. The system was Frozen , requested reboot and running. the server is online.

Now i try'd the OpenVPN and still "118 (net::ERR_CONNECTION_TIMED_OUT)" on any webpage.

---

### Post by SeijiSensei on 2013-01-12
Did you read my post carefully?   I said that those were the commands I would use *on a Linux workstation* and suggested you try the Windows equivalent.  I didn't expect you would enter the commands willy-nilly without thinking about what they might do.  

You need to change the routing on the client, not on the server.  The client needs to be configured to use the other end of the tunnel on the server as its default gateway.  That means the client needs a route to the server via the Internet and a default route via the tunnel.

---

