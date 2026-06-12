---
title: "connected to openvpn server but no access"
date: 2010-06-02
forum: Server Platforms
---

### Post by linkshift on 2010-06-02
Ok, so with the help of many people and many tutorial i have setup Open VPN on Ubuntu 9.04, generated the key and have it running successfully on the server end.

I download the open vpn client for windows, copied over the key ca and cert file and connected to the server. All went well and the open vpn gui said its connected to the server (green comp icon in taskbar) and it said in a ballon it assigned me an ip of 10.8.0.6

it all looks good... BUT i have no vpn access...
The virtual adapted in windows is not able to pull an actual IP/gateway and such...

HELP! thanks in advance...

here is the log i get while connecting
```
Thu Jun 03 04:31:27 2010 OpenVPN 2.1.1 i686-pc-mingw32 [SSL] [LZO2] [PKCS11] built on Dec 11 2009
Thu Jun 03 04:31:27 2010 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Thu Jun 03 04:31:27 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Thu Jun 03 04:31:28 2010 LZO compression initialized
Thu Jun 03 04:31:28 2010 Control Channel MTU parms [ L:1576 D:140 EF:40 EB:0 ET:0 EL:0 ]
Thu Jun 03 04:31:28 2010 Data Channel MTU parms [ L:1576 D:1450 EF:44 EB:135 ET:32 EL:0 AF:3/1 ]
Thu Jun 03 04:31:28 2010 Local Options hash (VER=V4): '31fdf004'
Thu Jun 03 04:31:28 2010 Expected Remote Options hash (VER=V4): '3e6d1056'
Thu Jun 03 04:31:28 2010 Attempting to establish TCP connection with 204.93.166.75:1194
Thu Jun 03 04:31:28 2010 TCP connection established with 204.93.166.75:1194
Thu Jun 03 04:31:28 2010 Socket Buffers: R=[8192->8192] S=[8192->8192]
Thu Jun 03 04:31:28 2010 TCPv4_CLIENT link local: [undef]
Thu Jun 03 04:31:28 2010 TCPv4_CLIENT link remote: 204.93.166.75:1194
Thu Jun 03 04:31:28 2010 TLS: Initial packet from 204.93.166.75:1194, sid=73a01bc9 15ec4e1b
Thu Jun 03 04:31:33 2010 VERIFY OK: depth=1, /C=PE/ST=LI/L=Lima/O=Nombre-OpenVPN/CN=Nombre-OpenVPN_CA/emailAddress=tu-nombre@example.com
Thu Jun 03 04:31:33 2010 VERIFY OK: depth=0, /C=PE/ST=LI/L=Lima/O=Nombre-OpenVPN/CN=server/emailAddress=tu-nombre@example.com
Thu Jun 03 04:31:43 2010 WARNING: 'dev-type' is used inconsistently, local='dev-type tap', remote='dev-type tun'
Thu Jun 03 04:31:43 2010 WARNING: 'link-mtu' is used inconsistently, local='link-mtu 1576', remote='link-mtu 1543'
Thu Jun 03 04:31:43 2010 WARNING: 'tun-mtu' is used inconsistently, local='tun-mtu 1532', remote='tun-mtu 1500'
Thu Jun 03 04:31:43 2010 WARNING: 'comp-lzo' is present in local config but missing in remote config, local='comp-lzo'
Thu Jun 03 04:31:43 2010 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Thu Jun 03 04:31:43 2010 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Jun 03 04:31:43 2010 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Thu Jun 03 04:31:43 2010 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Jun 03 04:31:43 2010 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Thu Jun 03 04:31:43 2010 [server] Peer Connection Initiated with 204.93.166.75:1194
Thu Jun 03 04:31:46 2010 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Thu Jun 03 04:31:47 2010 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway def1,route 10.8.0.0 255.255.255.0,topology net30,ifconfig 10.8.0.6 10.8.0.5'
Thu Jun 03 04:31:47 2010 OPTIONS IMPORT: --ifconfig/up options modified
Thu Jun 03 04:31:47 2010 OPTIONS IMPORT: route options modified
Thu Jun 03 04:31:47 2010 WARNING: Since you are using --dev tap, the second argument to --ifconfig must be a netmask, for example something like 255.255.255.0. (silence this warning with --ifconfig-nowarn)
Thu Jun 03 04:31:47 2010 ROUTE default_gateway=192.168.1.1
Thu Jun 03 04:31:47 2010 OpenVPN ROUTE: OpenVPN needs a gateway parameter for a --route option and no default was specified by either --route-gateway or --ifconfig options
Thu Jun 03 04:31:47 2010 OpenVPN ROUTE: failed to parse/resolve route for host/network: 10.8.0.0
Thu Jun 03 04:31:47 2010 TAP-WIN32 device [Local Area Connection 3] opened: \\.\Global\{3308F60A-512A-4B69-A506-05DA4852D22F}.tap
Thu Jun 03 04:31:47 2010 TAP-Win32 Driver Version 9.6 
Thu Jun 03 04:31:47 2010 TAP-Win32 MTU=1500
Thu Jun 03 04:31:47 2010 Notified TAP-Win32 driver to set a DHCP IP/netmask of 10.8.0.6/10.8.0.5 on interface {3308F60A-512A-4B69-A506-05DA4852D22F} [DHCP-serv: 10.8.0.4, lease-time: 31536000]
Thu Jun 03 04:31:47 2010 NOTE: FlushIpNetTable failed on interface [36] {3308F60A-512A-4B69-A506-05DA4852D22F} (status=5) : Access is denied.  
Thu Jun 03 04:31:52 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:31:52 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:31:57 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:31:57 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:31:58 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:31:58 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:31:59 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:31:59 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:00 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:00 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:01 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:01 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:02 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:02 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:03 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:03 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:04 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:04 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:05 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:05 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:06 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:06 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:07 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:07 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:08 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:08 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:09 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:09 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:10 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:10 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:11 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:11 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:12 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:12 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:13 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:13 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:14 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:14 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:15 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:15 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:16 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:16 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:17 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:17 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:18 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:18 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:19 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:19 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:20 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:20 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:21 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:21 2010 Route: Waiting for TUN/TAP interface to come up...
Thu Jun 03 04:32:22 2010 TEST ROUTES: 0/0 succeeded len=0 ret=0 a=0 u/d=down
Thu Jun 03 04:32:22 2010 NOTE: unable to redirect default gateway -- VPN gateway parameter (--route-gateway or --ifconfig) is missing
SYSTEM ROUTING TABLE
0.0.0.0 0.0.0.0 192.168.1.1 p=0 i=12 t=4 pr=3 a=3946 h=0 m=25/0/0/0/0
127.0.0.0 255.0.0.0 127.0.0.1 p=0 i=1 t=3 pr=3 a=270672 h=0 m=306/0/0/0/0
127.0.0.1 255.255.255.255 127.0.0.1 p=0 i=1 t=3 pr=3 a=270672 h=0 m=306/0/0/0/0
127.255.255.255 255.255.255.255 127.0.0.1 p=0 i=1 t=3 pr=3 a=270672 h=0 m=306/0/0/0/0
169.254.0.0 255.255.0.0 169.254.178.22 p=0 i=36 t=3 pr=3 a=25 h=0 m=286/0/0/0/0
169.254.178.22 255.255.255.255 169.254.178.22 p=0 i=36 t=3 pr=3 a=25 h=0 m=286/0/0/0/0
169.254.255.255 255.255.255.255 169.254.178.22 p=0 i=36 t=3 pr=3 a=25 h=0 m=286/0/0/0/0
192.168.1.0 255.255.255.0 192.168.1.101 p=0 i=12 t=3 pr=3 a=3946 h=0 m=281/0/0/0/0
192.168.1.101 255.255.255.255 192.168.1.101 p=0 i=12 t=3 pr=3 a=3946 h=0 m=281/0/0/0/0
192.168.1.255 255.255.255.255 192.168.1.101 p=0 i=12 t=3 pr=3 a=3946 h=0 m=281/0/0/0/0
224.0.0.0 240.0.0.0 127.0.0.1 p=0 i=1 t=3 pr=3 a=270672 h=0 m=306/0/0/0/0
224.0.0.0 240.0.0.0 192.168.1.101 p=0 i=12 t=3 pr=3 a=270645 h=0 m=281/0/0/0/0
224.0.0.0 240.0.0.0 169.254.178.22 p=0 i=36 t=3 pr=3 a=1480 h=0 m=286/0/0/0/0
255.255.255.255 255.255.255.255 127.0.0.1 p=0 i=1 t=3 pr=3 a=270672 h=0 m=306/0/0/0/0
255.255.255.255 255.255.255.255 192.168.1.101 p=0 i=12 t=3 pr=3 a=270645 h=0 m=281/0/0/0/0
255.255.255.255 255.255.255.255 169.254.178.22 p=0 i=36 t=3 pr=3 a=1480 h=0 m=286/0/0/0/0
SYSTEM ADAPTER LIST
TAP-Win32 Adapter V9
  Index = 36
  GUID = {3308F60A-512A-4B69-A506-05DA4852D22F}
  IP = 169.254.178.22/255.255.0.0 
  MAC = 00:ff:33:08:f6:0a
  GATEWAY = 0.0.0.0/255.255.255.255 
  DHCP SERV = 0.0.0.0/255.255.255.255 
  DHCP LEASE OBTAINED = Thu Jun 03 04:32:22 2010
  DHCP LEASE EXPIRES  = Thu Jun 03 04:32:22 2010
  DNS SERV =  
```this is what my client config file looks like..
```
dev tap
client
proto tcp
remote 204.93.xxx.75 1194
dev tap
ca ca.crt
cert client1.crt
key client1.key
comp-lzo
verb 3
mute 20
resolv-retry infinite
nobind
client
dev tap
persist-key
persist-tun
```ipconfig (virtual adapter) reveals some random non working ip (as if its not connected to anything)
```
Ethernet adapter Local Area Connection 3:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::457c:4c53:636b:b216%36
   Autoconfiguration IPv4 Address. . : 169.254.178.22
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Default Gateway . . . . . . . . . :
```

---

### Post by noway2 on 2010-06-02
It looks like you have a routing problem from these entries:

47 2010 OpenVPN ROUTE: failed to parse/resolve route for host/network: 10.8.0.0 and
Thu Jun 03 04:31:47 2010 OpenVPN ROUTE: OpenVPN needs a gateway parameter for a --route option and no default was specified by either --route-gateway or --ifconfig options

The problem is most likely in your server config file. Do you have a default-gateway set?  It appears to be missing and it looks like there is no way for the client to figure out how to get the connection through the TAP device to the host.

---

### Post by linkshift on 2010-06-03
where can i see/change the default gateway in ubuntu?

---

### Post by linkshift on 2010-06-03
oh, do u mean default gateway in the openvpn config?
hmm... ill look into that and set that up, if its not there....
but any handy shell command to find out what my def. gateway is?

---

### Post by noway2 on 2010-06-03
You will want to look in /etc/openvpn/server.conf.

You should have a set of configurations similar to these (numbers changed for your configuration):

#this will redirect all traffic through the VPN
server-bridge 192.168.0.1 255.255.255.0 192.168.0.90 192.168.0.99
push "redirect-gateway def1"
push "route-gateway 192.168.0.1"

#DHCP Information
ifconfig-pool-persist ipp.txt
push "dhcp-option DNS 192.168.0.49"
push "dhcp-option WINS 192.168.0.49"
push "dhcp-option DOMAIN debian.lan"
push "dhcp-option NBT 2"

I would have posted them yesterday, but a thunderstorm knocked the power out and I couldn't access my server, sorry.

This will push the gateway and the DNS information so that things will hopefully route through the VPN.

---

### Post by spynappels on 2010-06-04
That is if you are setup in Bridged Mode, you may need to adjust some of these if you work in routed mode....

---

### Post by noway2 on 2010-06-04
Thats true.  I assumed that they are running bridged mode because of this message in the logs. > WARNING: Since you are using --dev tap, the second argument to --ifconfig must be a netmask, for example something like 255.255.255.0. (silence this warning with --ifconfig-nowarn)

This error also points to a configuration problem in server.conf. It also brings up another possible area of difficulty.  Is the bridge set up correctly?  I found this document to be quite helpful: [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

---

### Post by benderisgreat on 2010-06-04
> Thu Jun 03 04:31:43 2010 WARNING: 'dev-type' is used inconsistently, local='dev-type tap', remote='dev-type tun'

Your server is configured to use a tunnel type interface while your client is not.

Also in your client config you have three instances of 'dev tap' and two of 'client'. Remove the duplicates and replace 'dev tap' with 'dev tun'. I would always use tun unless you know you need tap. In any case the client and server configuration need to match.

---

