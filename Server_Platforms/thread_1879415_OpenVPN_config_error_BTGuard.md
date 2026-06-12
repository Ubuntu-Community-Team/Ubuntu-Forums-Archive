---
title: "OpenVPN config error? BTGuard"
date: 2011-11-11
forum: Server Platforms
---

### Post by Duvrazh on 2011-11-11
Hello, trying to install openvpn with BTGuard service. Followed all the sparse documentation on this and ended up with the CLI output of the following.
> root@Duvrazh-MS:~/openvpn-2.2.1# openvpn /etc/openvpn/btguard.conf
Fri Nov 11 19:40:32 2011 OpenVPN 2.2.1 x86_64-unknown-linux-gnu [SSL] [LZO2] [EPOLL] [eurephia] built on Nov 11 2011
Enter Auth Username:duvrazh
Enter Auth Password:
Fri Nov 11 19:40:38 2011 WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Fri Nov 11 19:40:38 2011 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Fri Nov 11 19:40:38 2011 LZO compression initialized
Fri Nov 11 19:40:38 2011 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Fri Nov 11 19:40:38 2011 Socket Buffers: R=[126976->131072] S=[126976->131072]
Fri Nov 11 19:40:38 2011 RESOLVE: NOTE: vpn.btguard.com resolves to 2 addresses
Fri Nov 11 19:40:38 2011 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Fri Nov 11 19:40:38 2011 Local Options hash (VER=V4): '41690919'
Fri Nov 11 19:40:38 2011 Expected Remote Options hash (VER=V4): '530fdded'
Fri Nov 11 19:40:38 2011 UDPv4 link local: [undef]
Fri Nov 11 19:40:38 2011 UDPv4 link remote: 95.211.139.146:1194
Fri Nov 11 19:40:38 2011 TLS: Initial packet from 95.211.139.146:1194, sid=f03bd9aa 612bbc0c
Fri Nov 11 19:40:38 2011 VERIFY OK: depth=1, /C=DE/ST=Hesse-Nassau/L=Frankfurt/O=BTGuard/CN=BTGuard_CA/emailAddress=support@btguard.com
Fri Nov 11 19:40:38 2011 VERIFY OK: depth=0, /C=DE/ST=Hesse-Nassau/L=Frankfurt/O=BTGuard/CN=server/emailAddress=support@btguard.com
Fri Nov 11 19:40:38 2011 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Fri Nov 11 19:40:38 2011 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Nov 11 19:40:38 2011 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Fri Nov 11 19:40:38 2011 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Nov 11 19:40:38 2011 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Fri Nov 11 19:40:38 2011 [server] Peer Connection Initiated with 95.211.139.146:1194
Fri Nov 11 19:40:40 2011 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Fri Nov 11 19:40:40 2011 PUSH: Received control message: 'PUSH_REPLY,dhcp-option DNS 8.8.8.8,redirect-gateway,route 10.10.0.1,topology net30,ping 10,ping-restart 120'
Fri Nov 11 19:40:40 2011 OPTIONS IMPORT: timers and/or timeouts modified
Fri Nov 11 19:40:40 2011 OPTIONS IMPORT: --ifconfig/up options modified
Fri Nov 11 19:40:40 2011 OPTIONS IMPORT: route options modified
Fri Nov 11 19:40:40 2011 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Fri Nov 11 19:40:40 2011 ROUTE default_gateway=192.168.1.1
Fri Nov 11 19:40:40 2011 OpenVPN ROUTE: OpenVPN needs a gateway parameter for a --route option and no default was specified by either --route-gateway or --ifconfig options
Fri Nov 11 19:40:40 2011 OpenVPN ROUTE: failed to parse/resolve route for host/network: 10.10.0.1
Fri Nov 11 19:40:40 2011 TUN/TAP device tun0 opened
Fri Nov 11 19:40:40 2011 TUN/TAP TX queue length set to 100
Fri Nov 11 19:40:40 2011 NOTE: unable to redirect default gateway -- VPN gateway parameter (--route-gateway or --ifconfig) is missing
Fri Nov 11 19:40:40 2011 Initialization Sequence Completed



With no routing information and no real tutorials from BTGuard, I'm at a lost. I've just emailed them, but hoping you ladies and gentlemen might be more productive over the weekend, can anyone make any recommendations for me? Thank you very much.

---

### Post by koenn on 2011-11-11
what routing did you try to set in the ovpn conf ?

---

