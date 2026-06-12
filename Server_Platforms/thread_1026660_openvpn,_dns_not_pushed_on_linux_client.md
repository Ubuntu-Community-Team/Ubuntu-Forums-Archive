---
title: "openvpn, dns not pushed on linux client"
date: 2008-12-31
forum: Server Platforms
---

### Post by Shwick2 on 2008-12-31
I have openvpn 2.1_rc7 running on ubuntu 8.04.  I set up a user that has all traffic and dns pushed through the vpn.

On windows the vpn client works just fine, all traffic and dns requests are pushed through the vpn.

When I boot the windows pc with a live cd of ubuntu 8.04 and connect with vpn, the dns requests aren't pushed through the vpn.

I already added those two scripts that were supposed to update resolv.conf to my client config, still didn't work.
```

up /etc/openvpn/update-resolv-conf

down /etc/openvpn/update-resolv-conf

```
In fact if you look at the client output you don't see /etc/openvpn/update-resolv-conf being called on the dns ip 10.8.0.1, but you do see it called on the ip that is pushed to the client, 
```

/etc/openvpn/update-resolv-conf tun0 1500 1544 10.8.1.1 10.8.1.2 init

```
I'm wondering if this is a permissions issue.  I start the client with "sudo openvpn anonUserPush.conf".  Am I supposed to add in something for the update-resolv-conf script?

If I manually add the dns to resolv.conf my requests are pushed through the vpn.

Client output:
```

Wed Dec 31 16:44:36 2008 OpenVPN 2.1_rc7 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on Jun 11 2008
Wed Dec 31 16:44:36 2008 WARNING: file 'keys/anonUserPush.key' is group or others accessible
Wed Dec 31 16:44:36 2008 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Wed Dec 31 16:44:36 2008 LZO compression initialized
Wed Dec 31 16:44:36 2008 Control Channel MTU parms [ L:1544 D:140 EF:40 EB:0 ET:0 EL:0 ]
Wed Dec 31 16:44:36 2008 Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Wed Dec 31 16:44:36 2008 Local Options hash (VER=V4): '69109d17'
Wed Dec 31 16:44:36 2008 Expected Remote Options hash (VER=V4): 'c0103fa8'
Wed Dec 31 16:44:36 2008 Attempting to establish TCP connection with 10.11.12.1:443 [nonblock]
Wed Dec 31 16:44:37 2008 TCP connection established with 10.11.12.1:443
Wed Dec 31 16:44:37 2008 Send to HTTP proxy: 'CONNECT 10.6.7.0:1194 HTTP/1.0'
Wed Dec 31 16:44:38 2008 HTTP proxy returned: 'HTTP/1.0 200 Connection established'
Wed Dec 31 16:44:40 2008 Socket Buffers: R=[87380->131072] S=[16384->131072]
Wed Dec 31 16:44:40 2008 TCPv4_CLIENT link local: [undef]
Wed Dec 31 16:44:40 2008 TCPv4_CLIENT link remote: 10.11.12.1:443
Wed Dec 31 16:44:40 2008 TLS: Initial packet from 10.11.12.1:443, sid=27752b22 5d16d2b1
Wed Dec 31 16:44:40 2008 VERIFY OK: depth=1, /C=CA/ST=ON/L=Ottawa/O=homeGateway/CN=homeGateway_CA/emailAddress=anon@anon.com
Wed Dec 31 16:44:40 2008 Validating certificate key usage
Wed Dec 31 16:44:40 2008 ++ Certificate has key usage  00a0, expects 00a0
Wed Dec 31 16:44:40 2008 VERIFY KU OK
Wed Dec 31 16:44:40 2008 Validating certificate extended key usage
Wed Dec 31 16:44:40 2008 ++ Certificate has EKU (str) TLS Web Server Authentication, expects TLS Web Server Authentication
Wed Dec 31 16:44:40 2008 VERIFY EKU OK
Wed Dec 31 16:44:40 2008 VERIFY OK: depth=0, /C=CA/ST=ON/L=Ottawa/O=homeGateway/CN=server/emailAddress=anon@anon.com
Wed Dec 31 16:44:40 2008 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Dec 31 16:44:40 2008 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Dec 31 16:44:40 2008 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Dec 31 16:44:40 2008 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Dec 31 16:44:40 2008 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Wed Dec 31 16:44:40 2008 [server] Peer Connection Initiated with 10.11.12.1:443
Wed Dec 31 16:44:41 2008 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Wed Dec 31 16:44:41 2008 PUSH: Received control message: 'PUSH_REPLY,route 10.6.7.0 255.255.255.255,route 10.8.0.1,topology net30,ping 10,ping-restart 120,redirect-gateway,dhcp-option DNS 10.8.0.1,ifconfig 10.8.1.1 10.8.1.2'
Wed Dec 31 16:44:41 2008 OPTIONS IMPORT: timers and/or timeouts modified
Wed Dec 31 16:44:41 2008 OPTIONS IMPORT: --ifconfig/up options modified
Wed Dec 31 16:44:41 2008 OPTIONS IMPORT: route options modified
Wed Dec 31 16:44:41 2008 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Wed Dec 31 16:44:41 2008 TUN/TAP device tun0 opened
Wed Dec 31 16:44:41 2008 TUN/TAP TX queue length set to 100
Wed Dec 31 16:44:41 2008 ifconfig tun0 10.8.1.1 pointopoint 10.8.1.2 mtu 1500
Wed Dec 31 16:44:41 2008 /etc/openvpn/update-resolv-conf tun0 1500 1544 10.8.1.1 10.8.1.2 init
Wed Dec 31 16:44:41 2008 OpenVPN ROUTE: omitted no-op route: 10.11.12.1/255.255.255.255 -> 10.11.12.1
Wed Dec 31 16:44:41 2008 route del -net 0.0.0.0 netmask 0.0.0.0
Wed Dec 31 16:44:41 2008 route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.8.1.2
Wed Dec 31 16:44:41 2008 route add -net 10.6.7.0 netmask 255.255.255.255 gw 10.8.1.2
Wed Dec 31 16:44:41 2008 route add -net 10.8.0.1 netmask 255.255.255.255 gw 10.8.1.2
Wed Dec 31 16:44:41 2008 Initialization Sequence Completed

```

---

### Post by rvjr on 2011-02-14
Hi Shwick2

have you solved this? I cant find anything on the web that helps this DNS issues, I'm on 10.04 btw.

Best
Rainer

---

### Post by andl on 2011-05-26
Try to install resolvconf package.

---

