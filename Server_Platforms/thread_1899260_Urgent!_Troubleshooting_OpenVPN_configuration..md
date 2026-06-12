---
title: "Urgent! Troubleshooting OpenVPN configuration."
date: 2011-12-23
forum: Server Platforms
---

### Post by artheus on 2011-12-23
Hello.

I've got a OpenVPN configuration I cant get to work.

In the config the only change I've made is the domain, and in the connection logs (verb 6) I've changed the ips to *.*.*.* as this is a server I don't want to expose publicly on the internet.

Hope someone can help me with this fast.

Thank you very much for any help!

Cheers,
Artheus

**server.conf:**
```
local sub.domain.com

port 1194

proto tcp

dev tun0

ca ca.crt
cert server.crt
key server.key

dh dh1024.pem

server 10.0.100.0 255.255.255.0

ifconfig-pool-persist ipp.txt

keepalive 10 120

comp-lzo

max-clients 5

user nobody
group nogroup

persist-key
persist-tun

status openvpn-status.log

verb 3

```

**client.conf:**
```
client

dev tun

proto tcp

remote sub.domain.com 1194

resolv-retry infinite
nobind

persist-key
persist-tun

ca ca.crt
cert artheus.cert
key artheus.key

comp-lzo

verb 3
```

**Client connection Log:**
```
Dec 23 11:03:42: Viscosity 1.3.5 (1051)
Dec 23 11:03:42: Checking reachability status of connection...
Dec 23 11:03:42: Connection is reachable. Starting connection attempt.
Dec 23 11:03:45: OpenVPN 2.2.1 x86_64-apple-darwin10.8.0 [SSL] [LZO2] [PKCS11] [eurephia] built on Aug  1 2011
Dec 23 11:03:44: MANAGEMENT: CMD 'state on'
Dec 23 11:03:44: MANAGEMENT: CMD 'hold release'
Dec 23 11:03:44: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Dec 23 11:03:44: NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Dec 23 11:03:44: Control Channel Authentication: using 'ta.key' as a OpenVPN static key file
Dec 23 11:03:44: Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Dec 23 11:03:44: Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Dec 23 11:03:44: LZO compression initialized
Dec 23 11:03:44: Control Channel MTU parms [ L:1544 D:168 EF:68 EB:0 ET:0 EL:0 ]
Dec 23 11:03:44: Socket Buffers: R=[262140->65536] S=[131070->65536]
Dec 23 11:03:44: MANAGEMENT: >STATE:1324634624,RESOLVE,,,
Dec 23 11:03:44: Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Dec 23 11:03:44: Local Options String: 'V4,dev-type tun,link-mtu 1544,tun-mtu 1500,proto TCPv4_CLIENT,comp-lzo,keydir 1,cipher BF-CBC,auth SHA1,keysize 128,tls-auth,key-method 2,tls-client'
Dec 23 11:03:44: Expected Remote Options String: 'V4,dev-type tun,link-mtu 1544,tun-mtu 1500,proto TCPv4_SERVER,comp-lzo,keydir 0,cipher BF-CBC,auth SHA1,keysize 128,tls-auth,key-method 2,tls-server'
Dec 23 11:03:44: Local Options hash (VER=V4): 'ee93268d'
Dec 23 11:03:44: Expected Remote Options hash (VER=V4): 'bd577cd1'
Dec 23 11:03:44: Attempting to establish TCP connection with *.*.*.*:1194 [nonblock]
Dec 23 11:03:44: MANAGEMENT: >STATE:1324634624,TCP_CONNECT,,,
Dec 23 11:03:45: MANAGEMENT: CMD 'hold release'
Dec 23 11:03:45: MANAGEMENT: CMD 'state on'
Dec 23 11:03:46: MANAGEMENT: CMD 'hold release'
Dec 23 11:03:46: MANAGEMENT: CMD 'pid'
Dec 23 11:03:46: MANAGEMENT: CMD 'pid'
Dec 23 11:03:46: MANAGEMENT: CMD 'hold release'
Dec 23 11:03:46: MANAGEMENT: CMD 'pid'
Dec 23 11:03:46: MANAGEMENT: CMD 'pid'
Dec 23 11:03:47: TCP connection established with *.*.*.*:1194
Dec 23 11:03:47: TCPv4_CLIENT link local: [undef]
Dec 23 11:03:47: TCPv4_CLIENT link remote: *.*.*.*:1194
Dec 23 11:03:47: MANAGEMENT: >STATE:1324634627,WAIT,,,
Dec 23 11:03:47: TCPv4_CLIENT WRITE [42] to *.*.*.*:1194: P_CONTROL_HARD_RESET_CLIENT_V2 kid=0 pid=[ #1 ] [ ] pid=0 DATA len=0
Dec 23 11:03:47: Connection reset, restarting [0]
Dec 23 11:03:47: TCP/UDP: Closing socket
Dec 23 11:03:47: SIGUSR1[soft,connection-reset] received, process restarting
Dec 23 11:03:47: MANAGEMENT: >STATE:1324634627,RECONNECTING,connection-reset,,
Dec 23 11:03:48: MANAGEMENT: CMD 'hold release'
Dec 23 11:03:48: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Dec 23 11:03:48: NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
```

**Server Log:**
```

OpenVPN CLIENT LIST
Updated,Fri Dec 23 11:14:27 2011
Common Name,Real Address,Bytes Received,Bytes Sent,Connected Since
ROUTING TABLE
Virtual Address,Common Name,Real Address,Last Ref
GLOBAL STATS
Max bcast/mcast queue length,0
END

```

---

### Post by artheus on 2011-12-23
Sorry. Forgot to mention. Ports are open and accessible. I've been able to connect with the standard Ubuntu Community OpenVPN configuration. But that is not really the config I want.

I am also using the same certificates from the earlier Ubuntu Community Configuration.

Cheers,
Artheus

Ubuntu Community Config : [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

---

