---
title: "BTguard open VPN setup"
date: 2010-12-17
forum: Server Platforms
---

### Post by creatureofthedark on 2010-12-17
hey iv been trying to setup BTguard open VPN on my ubuntu server... BTguard uses a username and password setup... i have followed the following instructions found on there site


Download BTGuard certificate (CA) by typing: wget -O /etc/openvpn/btguard.ca.crt [http://btguard.com/btguard.ca.crt](http://btguard.com/btguard.ca.crt)

Download BTGuard OpenVPN configuration by typing: wget -O /etc/openvpn/btguard.conf [http://btguard.com/btguard.conf](http://btguard.com/btguard.conf)

Setup complete!

How To Connect
1. openvpn /etc/openvpn/btguard.conf
3. Enter your BTGuard username & password.

You are now connected!


but when i try i get the following output....


creature@squirtle-fileServer-dashaus:~$ openvpn /etc/openvpn/btguard.conf                                                                                    Fri Dec 17 12:05:43 2010 OpenVPN 2.1.0 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 12 2010
Enter Auth Username: <my username>
Enter Auth Password: <my password>
Fri Dec 17 12:05:53 2010 WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Fri Dec 17 12:05:53 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Fri Dec 17 12:05:53 2010 LZO compression initialized
Fri Dec 17 12:05:53 2010 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Fri Dec 17 12:05:53 2010 RESOLVE: NOTE: vpn.btguard.com resolves to 3 addresses, choosing one by random
Fri Dec 17 12:05:53 2010 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Fri Dec 17 12:05:53 2010 Local Options hash (VER=V4): '41690919'
Fri Dec 17 12:05:53 2010 Expected Remote Options hash (VER=V4): '530fdded'
Fri Dec 17 12:05:53 2010 Socket Buffers: R=[126976->131072] S=[126976->131072]
Fri Dec 17 12:05:53 2010 UDPv4 link local: [undef]
Fri Dec 17 12:05:53 2010 UDPv4 link remote: [AF_INET]85.131.129.178:1194
Fri Dec 17 12:05:53 2010 TLS: Initial packet from [AF_INET]85.131.129.178:1194, sid=efde543f 8d8ac4c3
Fri Dec 17 12:05:55 2010 VERIFY OK: depth=1, /C=DE/ST=Hesse-Nassau/L=Frankfurt/O=BTGuard/CN=BTGuard_CA/emailAddress=support@btguard.com
Fri Dec 17 12:05:55 2010 VERIFY OK: depth=0, /C=DE/ST=Hesse-Nassau/L=Frankfurt/O=BTGuard/CN=server/emailAddress=support@btguard.com
Fri Dec 17 12:05:56 2010 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Fri Dec 17 12:05:56 2010 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Dec 17 12:05:56 2010 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Fri Dec 17 12:05:56 2010 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Dec 17 12:05:56 2010 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Fri Dec 17 12:05:56 2010 [server] Peer Connection Initiated with [AF_INET]85.131.129.178:1194
Fri Dec 17 12:05:58 2010 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Fri Dec 17 12:05:58 2010 PUSH: Received control message: 'PUSH_REPLY,dhcp-option DNS 85.131.129.171,redirect-gateway,route 10.10.0.1,topology net30,ping 10,ping-restart 120,ifconfig 10.10.0.110 10.10.0.109'
Fri Dec 17 12:05:58 2010 OPTIONS IMPORT: timers and/or timeouts modified
Fri Dec 17 12:05:58 2010 OPTIONS IMPORT: --ifconfig/up options modified
Fri Dec 17 12:05:58 2010 OPTIONS IMPORT: route options modified
Fri Dec 17 12:05:58 2010 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Fri Dec 17 12:05:58 2010 ROUTE default_gateway=192.168.2.200
Fri Dec 17 12:05:58 2010 Note: Cannot ioctl TUNSETIFF tun: Operation not permitted (errno=1)
Fri Dec 17 12:05:58 2010 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Fri Dec 17 12:05:58 2010 Cannot allocate TUN/TAP dev dynamically
Fri Dec 17 12:05:58 2010 Exiting
creature@squirtle-fileServer-dashaus:~$


any ideas what it is im doing wrong???


Thank you for any help

---

### Post by Duvrazh on 2011-11-11
Can any experts shine some light on this please? I wish to VPN my server as well using this same service but have the same error message. Thank you.

---

