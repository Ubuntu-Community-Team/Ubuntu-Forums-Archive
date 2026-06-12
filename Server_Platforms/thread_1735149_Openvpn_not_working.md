---
title: "Openvpn not working"
date: 2011-04-21
forum: Server Platforms
---

### Post by linuxuser123456 on 2011-04-21
I am having trouble setting up Openvpn both route or bridge. My goal is to use a bridge configuration. The clients can connect to the server, but the clients can&#8217;t ping or connect to anything on the network or the internet.
   
  I have been trying to troubleshoot Openvpn for weeks. 
  What I am doing wrong?
   
  I am on Ubuntu server 10.10
   
  Here is my setup
   
  Openvpn server(192.168.1.150)<---> router(192.168.1.1)<---> Modem(192.168.0.1)<-WLAN->Remote VPN client
   
  Here are my configuration files
   
  [COLOR=red][FONT=&quot]Server config[/FONT][/COLOR]
  
  [FONT=&quot]port 1194[/FONT]
  [FONT=&quot]proto udp[/FONT]
  [FONT=&quot]dev tap0[/FONT]
  [FONT=&quot]up "/etc/openvpn/up.sh br0"[/FONT]
  [FONT=&quot]down "/etc/openvpn/down.sh br0"[/FONT]
  [FONT=&quot]ca /etc/openvpn/ca.crt[/FONT]
  [FONT=&quot]cert /etc/openvpn/server.crt[/FONT]
  [FONT=&quot]key /etc/openvpn/server.key[/FONT]
  [FONT=&quot]dh /etc/openvpn/dh2048.pem[/FONT]
  [FONT=&quot]tls-auth /etc/openvpn/ta.key 0[/FONT]
  [FONT=&quot]ifconfig-pool-persist ipp.txt[/FONT]
  [FONT=&quot]server-bridge 192.168.4.1 255.255.255.0 192.168.4.100 192.168.4.200[/FONT]
  [FONT=&quot]push "route 192.168.1.0 255.255.255.0"[/FONT]
  [FONT=&quot]push "redirect-gateway def1"[/FONT]
  [FONT=&quot]push "dhcp-option DNS 192.168.1.1"[/FONT]
  [FONT=&quot]client-to-client[/FONT]
  [FONT=&quot]keepalive 10 120[/FONT]
  [FONT=&quot]comp-lzo[/FONT]
  [FONT=&quot]user nobody[/FONT]
  [FONT=&quot]group nogroup[/FONT]
  [FONT=&quot]persist-key[/FONT]
  [FONT=&quot]persist-tun[/FONT]
  [FONT=&quot]status openvpn-status.log[/FONT]
  [FONT=&quot]log /etc/openvpn/openvpn.log[/FONT]
  [FONT=&quot]verb 6[/FONT]
   
  [COLOR=red]Interfaces config[/COLOR]
   
  br0       Link encap:Ethernet  HWaddr *removed on purpose*
            inet addr:192.168.1.150  Bcast:192.168.1.255  Mask:255.255.255.0
            inet6 addr: fe80::222:68ff:fe7a:eec9/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:21688 errors:0 dropped:0 overruns:0 frame:0
            TX packets:10614 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:2316722 (2.3 MB)  TX bytes:1808145 (1.8 MB)
   
  eth0      Link encap:Ethernet  HWaddr *same as br0*
            inet6 addr: fe80::222:68ff:fe7a:eec9/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:24156 errors:0 dropped:0 overruns:0 frame:0
            TX packets:12396 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:3016781 (3.0 MB)  TX bytes:2057208 (2.0 MB)
            Interrupt:19 Base address:0xd800
   
  lo        Link encap:Local Loopback
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:56 errors:0 dropped:0 overruns:0 frame:0
            TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:5683 (5.6 KB)  TX bytes:5683 (5.6 KB)
   
  tap0      Link encap:Ethernet  HWaddr *removed on purpose*
            inet6 addr: fe80::d8c7:66ff:fe57:b02d/64 Scope:Link
            UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
            RX packets:6 errors:0 dropped:0 overruns:0 frame:0
            TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:100
            RX bytes:400 (400.0 B)  TX bytes:5336 (5.3 KB)
   
  [COLOR=red]Windows config from Openvpn client[/COLOR]
   
  Ethernet adapter Wireless Network Connection:
   
          Connection-specific DNS Suffix  . :
          Description . . . . . . . . . . . : 
          Physical Address. . . . . . . . . : Removed
          Dhcp Enabled. . . . . . . . . . . : Yes
          Autoconfiguration Enabled . . . . : Yes
          IP Address. . . . . . . . . . . . : 192.168.1.148
          Subnet Mask . . . . . . . . . . . : 255.255.255.0
          Default Gateway . . . . . . . . . : 192.168.1.1
          DHCP Server . . . . . . . . . . . : 192.168.1.1
          DNS Servers . . . . . . . . . . . : 192.168.1.1
          Lease Obtained. . . . . . . . . . : Removed
          Lease Expires . . . . . . . . . . : Removed
   
  Ethernet adapter Local Area Connection 2:
   
          Connection-specific DNS Suffix  . :
          Description . . . . . . . . . . . : TAP-Win32 Adapter V9
          Physical Address. . . . . . . . . : Removed
          Dhcp Enabled. . . . . . . . . . . : Yes
          Autoconfiguration Enabled . . . . : Yes
          IP Address. . . . . . . . . . . . : 192.168.4.100
          Subnet Mask . . . . . . . . . . . : 255.255.255.0
          Default Gateway . . . . . . . . . : 192.168.4.1
          DHCP Server . . . . . . . . . . . : 192.168.4.0
          DNS Servers . . . . . . . . . . . : 192.168.1.1
          Lease Obtained. . . . . . . . . . : Removed
          Lease Expires . . . . . . . . . . : Removed
   
  [COLOR=red]Openvpn client log[/COLOR]
   
  Thu Apr 21 00:28:57 2011 OpenVPN 2.1.4 i686-pc-mingw32 [SSL] [LZO2] [PKCS11] built on Nov  8 2010
  Thu Apr 21 00:28:57 2011 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
  Thu Apr 21 00:28:58 2011 Control Channel Authentication: using 'C:\keys\ta.key' as a OpenVPN static key file
  Thu Apr 21 00:28:58 2011 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
  Thu Apr 21 00:28:58 2011 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
  Thu Apr 21 00:28:58 2011 LZO compression initialized
  Thu Apr 21 00:28:58 2011 Control Channel MTU parms [ L:1574 D:166 EF:66 EB:0 ET:0 EL:0 ]
  Thu Apr 21 00:28:58 2011 Socket Buffers: R=[8192->8192] S=[8192->8192]
  Thu Apr 21 00:28:58 2011 Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ]
  Thu Apr 21 00:28:58 2011 Local Options hash (VER=V4): '13a273ba'
  Thu Apr 21 00:28:58 2011 Expected Remote Options hash (VER=V4): '360696c5'
  Thu Apr 21 00:28:58 2011 UDPv4 link local: [undef]
  Thu Apr 21 00:28:58 2011 UDPv4 link remote: 192.168.1.150:1194
  Thu Apr 21 00:28:58 2011 TLS: Initial packet from 192.168.1.150:1194, sid=03ef0cf9 8e039b40
  Thu Apr 21 00:28:58 2011 VERIFY OK: depth=1, /C=Removed/ST=Removed/L=Removed/O=Removed/CN=Removed/emailAddress=Removed
  Thu Apr 21 00:28:58 2011 VERIFY OK: nsCertType=SERVER
  Thu Apr 21 00:28:58 2011 VERIFY OK: depth=0, /C=Removed/ST=Removed/L=Removed/O=Removed/CN=Removed/emailAddress=Removed
  Thu Apr 21 00:28:58 2011 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
  Thu Apr 21 00:28:58 2011 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
  Thu Apr 21 00:28:58 2011 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
  Thu Apr 21 00:28:58 2011 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
  Thu Apr 21 00:28:58 2011 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
  Thu Apr 21 00:28:58 2011 [server] Peer Connection Initiated with 192.168.1.150:1194
  Thu Apr 21 00:29:01 2011 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
  Thu Apr 21 00:29:01 2011 PUSH: Received control message: 'PUSH_REPLY,route 192.168.1.0 255.255.255.0,redirect-gateway def1,dhcp-option DNS 192.168.1.1,route-gateway 192.168.4.1,ping 10,ping-restart 120,ifconfig 192.168.4.100 255.255.255.0'
  Thu Apr 21 00:29:01 2011 OPTIONS IMPORT: timers and/or timeouts modified
  Thu Apr 21 00:29:01 2011 OPTIONS IMPORT: --ifconfig/up options modified
  Thu Apr 21 00:29:01 2011 OPTIONS IMPORT: route options modified
  Thu Apr 21 00:29:01 2011 OPTIONS IMPORT: route-related options modified
  Thu Apr 21 00:29:01 2011 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
  Thu Apr 21 00:29:01 2011 ROUTE default_gateway=192.168.1.1
  Thu Apr 21 00:29:01 2011 TAP-WIN32 device [Local Area Connection 2] opened: \\.\Global\{1DCE96A1-B07F-46D3-AFEF-B69EA1297228}.tap
  Thu Apr 21 00:29:01 2011 TAP-Win32 Driver Version 9.7 
  Thu Apr 21 00:29:01 2011 TAP-Win32 MTU=1500
  Thu Apr 21 00:29:01 2011 Notified TAP-Win32 driver to set a DHCP IP/netmask of 192.168.4.100/255.255.255.0 on interface {1DCE96A1-B07F-46D3-AFEF-B69EA1297228} [DHCP-serv: 192.168.4.0, lease-time: 31536000]
  Thu Apr 21 00:29:01 2011 Successful ARP Flush on interface [3] {1DCE96A1-B07F-46D3-AFEF-B69EA1297228}
  Thu Apr 21 00:29:06 2011 TEST ROUTES: 2/2 succeeded len=1 ret=1 a=0 u/d=up
  Thu Apr 21 00:29:06 2011 C:\WINDOWS\system32\route.exe ADD 192.168.1.150 MASK 255.255.255.255 192.168.1.1
  Thu Apr 21 00:29:06 2011 Route addition via IPAPI succeeded [adaptive]
  Thu Apr 21 00:29:06 2011 C:\WINDOWS\system32\route.exe ADD 0.0.0.0 MASK 128.0.0.0 192.168.4.1
  Thu Apr 21 00:29:06 2011 Route addition via IPAPI succeeded [adaptive]
  Thu Apr 21 00:29:06 2011 C:\WINDOWS\system32\route.exe ADD 128.0.0.0 MASK 128.0.0.0 192.168.4.1
  Thu Apr 21 00:29:06 2011 Route addition via IPAPI succeeded [adaptive]
  Thu Apr 21 00:29:06 2011 WARNING: potential route subnet conflict between local LAN [192.168.1.0/255.255.255.0] and remote VPN [192.168.1.0/255.255.255.0]
  Thu Apr 21 00:29:06 2011 C:\WINDOWS\system32\route.exe ADD 192.168.1.0 MASK 255.255.255.0 192.168.4.1
  Thu Apr 21 00:29:06 2011 Route addition via IPAPI succeeded [adaptive]
  Thu Apr 21 00:29:06 2011 Initialization Sequence Completed

---

### Post by spynappels on 2011-04-21
> **linuxuser123456 said:**
> 
  Thu Apr 21 00:29:06 2011 WARNING: potential route subnet conflict between local LAN [192.168.1.0/255.255.255.0] and remote VPN [192.168.1.0/255.255.255.0]


This would probably be part of your problem. If your home LAN is on a 192.168.1.x/255.255.255.0 subnet and the remote computer is on a 192.168.1.x/255.255.255.0 subnet, there will definitely be routing errors. For example, you say you want to access a resource at 192.168.1.50 on your home LAN, but your remote computer does not know whether you want that address on the Remote LAN or on the Home LAN, so it does not route it anywhere.

Can you change the subnet on your home LAN to something less likely to conflict? 192.168.87.x or something?

---

### Post by linuxuser123456 on 2011-04-21
Actually 192.168.1.150 is my Openvpn server which is physically connected with CAT6 to to 192.168.1.1 my router. This may be a stupid question but, are you suggesting that I cannot test Openvpn on the LAN network itself.Do I have to test it on the WLAN side of the network?

---

### Post by spynappels on 2011-04-21
> **linuxuser123456 said:**
> Actually 192.168.1.150 is my Openvpn server which is physically connected with CAT6 to to 192.168.1.1 my router. This may be a stupid question but, are you suggesting that I cannot test Openvpn on the LAN network itself.Do I have to test it on the WLAN side of the network?

Yes, that is correct, although to be pedantic it is the WAN side (WLAN is Wireless LAN). 

But I was also saying that with the subnet you have in your LAN being such a common one, many routers come preconfigured to use this subnet, you will have problems connecting and working correctly from anywhere that uses the same subnet.

---

### Post by linuxuser123456 on 2011-04-22
Thanks, the error is gone when connecting from the WAN side.
But I am still unable to connect or ping to anything on the network. Maybe my bridge is miss configured?Can anyone check my config or send a working config file.

[COLOR=Red]interfaces config for bridge[/COLOR]

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.150
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.1.1

auto br0
iface br0 inet static
        address 192.168.1.150
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

Thanks

---

