---
title: "OpenVPN Help needed, please..."
date: 2010-08-01
forum: Server Platforms
---

### Post by iamgeniusrnti on 2010-08-01
So I'm supposed to fly to texas and I wanted to have VPN access to my house in case my experiment cuts off my family from the internet.  So I added another server called Amahi.  You  might be wondering why I am posting here and I will tell you that rarely does anyone ever answer questions over there LOL!

So I got the VPN running on Amahi and TCP/UDP ports forwarded thru Smoothwall.  I can connect but I can't see any network beyond that.  I can't surf the web thru VPN or even surf any of the servers on my network.

Here is the log that my Ubuntu Client spits out:
Jul 31 23:53:25 k-laptop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'...
Jul 31 23:53:25 k-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 19623
Jul 31 23:53:25 k-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections
Jul 31 23:53:25 k-laptop NetworkManager: <info>  VPN plugin state changed: 3
Jul 31 23:53:25 k-laptop NetworkManager: <info>  VPN connection 'hda' (Connect) reply received.
Jul 31 23:53:25 k-laptop nm-openvpn[19628]: OpenVPN 2.1_rc19 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 13 2009
Jul 31 23:53:25 k-laptop nm-openvpn[19628]: WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Jul 31 23:53:25 k-laptop nm-openvpn[19628]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Jul 31 23:53:25 k-laptop nm-openvpn[19628]: /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Jul 31 23:53:26 k-laptop nm-openvpn[19628]: LZO compression initialized
Jul 31 23:53:27 k-laptop nm-openvpn[19628]: Attempting to establish TCP connection with xxx.xxx.xxx.xxx:1194 [nonblock]
Jul 31 23:53:28 k-laptop nm-openvpn[19628]: TCP connection established with xxx.xxx.xxx.xxx:1194
Jul 31 23:53:28 k-laptop nm-openvpn[19628]: TCPv4_CLIENT link local: [undef]
Jul 31 23:53:28 k-laptop nm-openvpn[19628]: TCPv4_CLIENT link remote: xxx.xxx.xxx.xxx:1194
Jul 31 23:53:33 k-laptop nm-openvpn[19628]: [server] Peer Connection Initiated with xxx.xxx.xxx.xxx:1194
Jul 31 23:53:35 k-laptop nm-openvpn[19628]: TUN/TAP device tap0 opened
Jul 31 23:53:35 k-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tap0, iface: tap0)
Jul 31 23:53:35 k-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tap0, iface: tap0): no ifupdown configuration found.
Jul 31 23:53:35 k-laptop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/tap0: couldn't determine device driver; ignoring...
Jul 31 23:53:35 k-laptop nm-openvpn[19628]: /sbin/ifconfig tap0 192.168.1.205 netmask 255.255.255.0 mtu 1500 broadcast 192.168.1.255
Jul 31 23:53:35 k-laptop avahi-daemon[981]: Joining mDNS multicast group on interface tap0.IPv4 with address 192.168.1.205.
Jul 31 23:53:35 k-laptop avahi-daemon[981]: IP_ADD_MEMBERSHIP failed: No buffer space available
Jul 31 23:53:35 k-laptop avahi-daemon[981]: Registering new address record for 192.168.1.205 on tap0.IPv4.
Jul 31 23:53:35 k-laptop vmnetBridge: Adding interface tap0 index:49
Jul 31 23:53:35 k-laptop nm-openvpn[19628]: /usr/lib/network-manager-openvpn/nm-openvpn-service-openvpn-helper tap0 1500 1576 192.168.1.205 255.255.255.0 init
Jul 31 23:53:35 k-laptop NetworkManager: <info>  VPN connection 'hda' (IP Config Get) reply received.
Jul 31 23:53:35 k-laptop NetworkManager: <info>  VPN Gateway: xxx.xxx.xxx.xxx
Jul 31 23:53:35 k-laptop NetworkManager: <info>  Internal Gateway: 192.168.1.10
Jul 31 23:53:35 k-laptop NetworkManager: <info>  Tunnel Device: tap0
Jul 31 23:53:35 k-laptop NetworkManager: <info>  Internal IP4 Address: 192.168.1.205
Jul 31 23:53:35 k-laptop NetworkManager: <info>  Internal IP4 Prefix: 24
Jul 31 23:53:35 k-laptop NetworkManager: <info>  Internal IP4 Point-to-Point Address: 0.0.0.0
Jul 31 23:53:35 k-laptop NetworkManager: <info>  Maximum Segment Size (MSS): 0
Jul 31 23:53:35 k-laptop NetworkManager: <info>  Static Route: 192.168.1.0/24   Next Hop: 192.168.1.0
Jul 31 23:53:35 k-laptop NetworkManager: <info>  Internal IP4 DNS: 192.168.1.10
Jul 31 23:53:35 k-laptop NetworkManager: <info>  DNS Domain: 'home'
Jul 31 23:53:35 k-laptop NetworkManager: <info>  Login Banner:
Jul 31 23:53:35 k-laptop NetworkManager: <info>  -----------------------------------------
Jul 31 23:53:35 k-laptop NetworkManager: <info>  (null)
Jul 31 23:53:35 k-laptop NetworkManager: <info>  -----------------------------------------
Jul 31 23:53:35 k-laptop nm-openvpn[19628]: Initialization Sequence Completed
Jul 31 23:53:36 k-laptop NetworkManager: <info>  VPN connection 'hda' (IP Config Get) complete.
Jul 31 23:53:36 k-laptop kernel: [196105.012069] bridge-wlan0: disabling the bridge
Jul 31 23:53:36 k-laptop NetworkManager: <info>  Policy set 'hda' (tap0) as default for routing and DNS.
Jul 31 23:53:36 k-laptop NetworkManager: <info>  VPN plugin state changed: 4
Jul 31 23:53:36 k-laptop vmnetBridge: RTM_NEWROUTE: index:49
Jul 31 23:53:36 k-laptop vmnetBridge: Stopped bridge wlan0 to virtual network 0.
Jul 31 23:53:36 k-laptop kernel: [196105.036222] bridge-wlan0: down
Jul 31 23:53:36 k-laptop kernel: [196105.036243] bridge-wlan0: detached
Jul 31 23:53:36 k-laptop vmnetBridge: Started bridge tap0 to virtual network 0.
Jul 31 23:53:36 k-laptop kernel: [196105.036370] /dev/vmnet: open called by PID 1482 (vmnet-bridge)
Jul 31 23:53:36 k-laptop kernel: [196105.036395] /dev/vmnet: hub 0 does not exist, allocating memory.
Jul 31 23:53:36 k-laptop kernel: [196105.036480] /dev/vmnet: port on hub 0 successfully opened
Jul 31 23:53:36 k-laptop kernel: [196105.036513] bridge-tap0: up
Jul 31 23:53:36 k-laptop kernel: [196105.036526] bridge-tap0: attached
Jul 31 23:53:36 k-laptop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Jul 31 23:53:37 k-laptop dnsmasq[1384]: reading /etc/resolv.conf
Jul 31 23:53:37 k-laptop avahi-daemon[981]: Registering new address record for fe80::b0fe:62ff:fe82:3c48 on tap0.*.
Jul 31 23:53:37 k-laptop dnsmasq[1384]: using nameserver 192.168.2.254#53
Jul 31 23:53:46 k-laptop kernel: [196114.684069] tap0: no IPv6 routers present
Jul 31 23:53:48 k-laptop kernel: [196116.762153] Unknown OutputIN= OUT=tap0 SRC=192.168.1.205 DST=63.245.217.21 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=48534 DF PROTO=TCP SPT=46686 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 31 23:53:51 k-laptop kernel: [196119.760134] Unknown OutputIN= OUT=tap0 SRC=192.168.1.205 DST=63.245.217.21 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=48535 DF PROTO=TCP SPT=46686 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 31 23:53:57 k-laptop kernel: [196125.710283] Unknown OutputIN= OUT=tap0 SRC=192.168.1.205 DST=192.168.1.1 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=34458 DF PROTO=TCP SPT=59056 DPT=441 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 31 23:53:57 k-laptop wpa_supplicant[1159]: CTRL-EVENT-SCAN-RESULTS 
Jul 31 23:53:57 k-laptop avahi-daemon[981]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.103.
Jul 31 23:53:57 k-laptop avahi-daemon[981]: IP_ADD_MEMBERSHIP failed: No buffer space available
Jul 31 23:53:57 k-laptop kernel: [196126.604244] Unknown InputIN=tap0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:58:27:67:43:08:00 SRC=192.168.1.5 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=8151 PROTO=UDP SPT=137 DPT=137 LEN=76 
Jul 31 23:53:59 k-laptop kernel: [196128.104787] Unknown InputIN=tap0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:58:27:67:43:08:00 SRC=192.168.1.5 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=8152 PROTO=UDP SPT=137 DPT=137 LEN=76 
Jul 31 23:53:59 k-laptop kernel: [196128.105113] Unknown InputIN=tap0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:58:27:67:43:08:00 SRC=192.168.1.2 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=8153 PROTO=UDP SPT=137 DPT=137 LEN=76 
Jul 31 23:53:59 k-laptop kernel: [196128.105347] Unknown InputIN=tap0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:58:27:67:43:08:00 SRC=192.168.1.2 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=8154 PROTO=UDP SPT=137 DPT=137 LEN=76 
Jul 31 23:53:59 k-laptop kernel: [196128.105746] Unknown InputIN=tap0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:d9:0a:6b:46:08:00 SRC=192.168.1.8 DST=192.168.1.255 LEN=177 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=2190 DPT=2190 LEN=157 
Jul 31 23:54:00 k-laptop kernel: [196128.708128] Unknown OutputIN= OUT=tap0 SRC=192.168.1.205 DST=192.168.1.1 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=34459 DF PROTO=TCP SPT=59056 DPT=441 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 31 23:54:06 k-laptop kernel: [196134.708131] Unknown OutputIN= OUT=tap0 SRC=192.168.1.205 DST=192.168.1.1 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=34460 DF PROTO=TCP SPT=59056 DPT=441 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 31 23:54:13 k-laptop kernel: [196142.561352] Unknown OutputIN= OUT=tap0 SRC=192.168.1.205 DST=173.194.33.104 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=58733 DF PROTO=TCP SPT=35379 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 31 23:54:16 k-laptop kernel: [196145.561118] Unknown OutputIN= OUT=tap0 SRC=192.168.1.205 DST=173.194.33.104 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=58734 DF PROTO=TCP SPT=35379 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 31 23:54:18 k-laptop kernel: [196146.708153] Unknown OutputIN= OUT=tap0 SRC=192.168.1.205 DST=192.168.1.1 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=34461 DF PROTO=TCP SPT=59056 DPT=441 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 31 23:54:22 k-laptop kernel: [196151.561088] Unknown OutputIN= OUT=tap0 SRC=192.168.1.205 DST=173.194.33.104 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=58735 DF PROTO=TCP SPT=35379 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 31 23:54:34 k-laptop kernel: [196163.561157] Unknown OutputIN= OUT=tap0 SRC=192.168.1.205 DST=173.194.33.104 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=58736 DF PROTO=TCP SPT=35379 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 31 23:54:42 k-laptop kernel: [196170.708132] Unknown OutputIN= OUT=tap0 SRC=192.168.1.205 DST=192.168.1.1 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=34462 DF PROTO=TCP SPT=59056 DPT=441 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 31 23:54:58 k-laptop kernel: [196187.560663] Unknown OutputIN= OUT=tap0 SRC=192.168.1.205 DST=173.194.33.104 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=58737 DF PROTO=TCP SPT=35379 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 

At the end, the Unknown errors will go one at the rate of about once every two seconds.  192.168.1.205 is the IP that the VPN server dishes out.  192.168.1.1 is teh Smoothwall and 192.168.1.10 is the VPN server.

The server's logs look like this:

 31 23:54:17 localhost openvpn[1312]: MULTI: multi_create_instance called
Jul 31 23:54:17 localhost openvpn[1312]: Re-using SSL/TLS context
Jul 31 23:54:17 localhost openvpn[1312]: LZO compression initialized
Jul 31 23:54:17 localhost openvpn[1312]: Control Channel MTU parms [ L:1576 D:140 EF:40 EB:0 ET:0 EL:0 ]
Jul 31 23:54:17 localhost openvpn[1312]: Data Channel MTU parms [ L:1576 D:1450 EF:44 EB:135 ET:32 EL:0 AF:3/1 ]
Jul 31 23:54:17 localhost openvpn[1312]: Local Options hash (VER=V4): '3e6d1056'
Jul 31 23:54:17 localhost openvpn[1312]: Expected Remote Options hash (VER=V4): '31fdf004'
Jul 31 23:54:17 localhost openvpn[1312]: TCP connection established with 97.242.112.229:42897
Jul 31 23:54:17 localhost openvpn[1312]: Socket Buffers: R=[131072->131072] S=[131072->131072]
Jul 31 23:54:17 localhost openvpn[1312]: TCPv4_SERVER link local: [undef]
Jul 31 23:54:17 localhost openvpn[1312]: TCPv4_SERVER link remote: 97.242.112.229:42897
Jul 31 23:54:18 localhost openvpn[1312]: 97.242.112.229:42897 TLS: Initial packet from 97.242.112.229:42897, sid=8da8656e 2eefdbfd
Jul 31 23:54:22 localhost openvpn[1312]: 97.242.112.229:42897 VERIFY OK: depth=1, /C=US/ST=CA/L=SanJose/O=HomeHDA/OU=VPN/CN=yourhda.com/emailAddress=info@homehda.com
Jul 31 23:54:22 localhost openvpn[1312]: 97.242.112.229:42897 VERIFY OK: depth=0, /C=US/ST=CA/L=SanJose/O=HomeHDA/OU=VPN/CN=client-tcheng/emailAddress=info@homehda.com
Jul 31 23:54:23 localhost openvpn[1312]: 97.242.112.229:42897 PLUGIN_CALL: POST /usr/lib/openvpn/plugin/lib/openvpn-auth-pam.so/PLUGIN_AUTH_USER_PASS_VERIFY status=0
Jul 31 23:54:23 localhost openvpn[1312]: 97.242.112.229:42897 TLS: Username/Password authentication succeeded for username 'admin' 
Jul 31 23:54:23 localhost openvpn[1312]: 97.242.112.229:42897 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Jul 31 23:54:23 localhost openvpn[1312]: 97.242.112.229:42897 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Jul 31 23:54:23 localhost openvpn[1312]: 97.242.112.229:42897 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Jul 31 23:54:23 localhost openvpn[1312]: 97.242.112.229:42897 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Jul 31 23:54:24 localhost openvpn[1312]: 97.242.112.229:42897 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Jul 31 23:54:24 localhost openvpn[1312]: 97.242.112.229:42897 [client-tcheng] Peer Connection Initiated with 97.242.112.229:42897
Jul 31 23:54:24 localhost openvpn[1312]: client-tcheng/97.242.112.229:42897 PUSH: Received control message: 'PUSH_REQUEST'
Jul 31 23:54:24 localhost openvpn[1312]: client-tcheng/97.242.112.229:42897 SENT CONTROL [client-tcheng]: 'PUSH_REPLY,route-gateway 192.168.1.1,route 192.168.1.0 255.255.255.0,dhcp-option DNS 192.168.1.10,dhcp-option DOMAIN home,route-gateway 192.168.1.10,ping 10,ping-restart 220,ifconfig 192.168.1.205 255.255.255.0' (status=1)
Jul 31 23:54:25 localhost openvpn[1312]: client-tcheng/97.242.112.229:42897 MULTI: Learn: b2:fe:62:82:3c:48 -> client-tcheng/97.242.112.229:42897
Jul 31 23:57:29 localhost openvpn[1312]: client-tcheng/97.242.112.229:42897 Connection reset, restarting [0]
Jul 31 23:57:29 localhost openvpn[1312]: client-tcheng/97.242.112.229:42897 SIGUSR1[soft,connection-reset] received, client-instance restarting
Jul 31 23:57:29 localhost openvpn[1312]: TCP/UDP: Closing socket

And the server's config file looks like this:

port 1194
proto tcp
dev tap
#dev tun
mode server
tls-server
dev tap0
ca /etc/openvpn/amahi/ca.crt
cert /etc/openvpn/amahi/server.crt
# This file should be kept secret
key /etc/openvpn/amahi/server.key
dh /etc/openvpn/amahi/dh1024.pem
#server 10.8.0.0 255.255.255.0
#ifconfig-pool-persist /var/run/openvpn-ipp.cache
server-bridge 192.168.1.10 255.255.255.0 192.168.1.205 192.168.1.210
push "route-gateway 192.168.1.1"
push "route 192.168.1.0 255.255.255.0"
push "dhcp-option DNS 192.168.1.10"
#push "dhcp-option WINS 192.168.1.10"
push "dhcp-option DOMAIN home"
keepalive 10 220
comp-lzo
persist-key
persist-tun
status /var/log/openvpn-status.log
verb 3
;mute 20
plugin /usr/lib/openvpn/plugin/lib/openvpn-auth-pam.so "login login USERNAME password PASSWORD"

I've been wracking my brain for two days--please help???

---

### Post by iamgeniusrnti on 2010-08-01
So uhh... yea... I just want to appologize for completely wasting everybody's time (including to myself for blowing the last two days) for as soon as I posted this, I instantly knew what my problem was.

THE DAMN FIREWALL!  After I posted the log, I noticed among teh gibberish was a link to a tutorial.  I clicked said link and it popped me to the middle of a page with a statement that said VPNs usually don't work if you have a firewall turned on... as soon as I ran up firestarter and stalled the FW, I had instant internet!

So yea... sorry for posting suck a stupid question:s

---

