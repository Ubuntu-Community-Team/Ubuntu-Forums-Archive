---
title: "VirtualBox Ubuntu Server 1404 64bit OpenVPN Access Server issue"
date: 2014-10-29
forum: Server Platforms
---

### Post by Spotopolis on 2014-10-29
I have been trying to get my Access Server running the last few days reading forum post and rereading them. I can connect from my client PC to my Ubuntu 14 Openvpn Access server's web GUI to download the client.ovpn file and log in to make web GUI changes. I can also remote to my PC at home and putty to the VM and make changes.

When my client PC (windows 8.1 64) connects to my VM I get this error:

```
Wed Oct 29 12:02:50 2014 OpenVPN 2.3.4 x86_64-w64-mingw32 [SSL (OpenSSL)] [LZO] [PKCS11] [IPv6] built on Oct 21 2014Wed Oct 29 12:02:50 2014 library versions: OpenSSL 1.0.1j 15 Oct 2014, LZO 2.05
Wed Oct 29 12:02:50 2014 MANAGEMENT: TCP Socket listening on [AF_INET]127.0.0.1:25340
Wed Oct 29 12:02:50 2014 Need hold release from management interface, waiting...
Wed Oct 29 12:02:50 2014 MANAGEMENT: Client connected from [AF_INET]127.0.0.1:25340
Wed Oct 29 12:02:50 2014 MANAGEMENT: CMD 'state on'
Wed Oct 29 12:02:50 2014 MANAGEMENT: CMD 'log all on'
Wed Oct 29 12:02:50 2014 MANAGEMENT: CMD 'hold off'
Wed Oct 29 12:02:50 2014 MANAGEMENT: CMD 'hold release'
Wed Oct 29 12:02:56 2014 MANAGEMENT: CMD 'username "Auth" "Spotopolis"'
Wed Oct 29 12:02:56 2014 MANAGEMENT: CMD 'password [...]'
Wed Oct 29 12:02:57 2014 Control Channel Authentication: tls-auth using INLINE static key file
Wed Oct 29 12:02:57 2014 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Oct 29 12:02:57 2014 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Oct 29 12:02:57 2014 Socket Buffers: R=[65536->100000] S=[65536->100000]
Wed Oct 29 12:02:57 2014 UDPv4 link local: [undef]
Wed Oct 29 12:02:57 2014 UDPv4 link remote: [AF_INET]***.***.***.***:1194
Wed Oct 29 12:02:57 2014 MANAGEMENT: >STATE:1414602177,WAIT,,,
Wed Oct 29 12:02:57 2014 MANAGEMENT: >STATE:1414602177,AUTH,,,
Wed Oct 29 12:02:57 2014 TLS: Initial packet from [AF_INET]67.48.29.204:1194, sid=c6ee8551 c236f77e
Wed Oct 29 12:02:57 2014 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Wed Oct 29 12:02:57 2014 VERIFY OK: depth=1, CN=OpenVPN CA
Wed Oct 29 12:02:57 2014 VERIFY OK: nsCertType=SERVER
Wed Oct 29 12:02:57 2014 VERIFY OK: depth=0, CN=OpenVPN Server
Wed Oct 29 12:02:58 2014 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Oct 29 12:02:58 2014 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Oct 29 12:02:58 2014 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Oct 29 12:02:58 2014 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Oct 29 12:02:58 2014 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Wed Oct 29 12:02:58 2014 [OpenVPN Server] Peer Connection Initiated with [AF_INET]***.***.***.***:1194
Wed Oct 29 12:02:59 2014 MANAGEMENT: >STATE:1414602179,GET_CONFIG,,,
Wed Oct 29 12:03:01 2014 SENT CONTROL [OpenVPN Server]: 'PUSH_REQUEST' (status=1)
Wed Oct 29 12:03:01 2014 PUSH: Received control message: 'PUSH_REPLY,explicit-exit-notify,route-gateway dhcp,route-delay 5 30,dhcp-pre-release,dhcp-renew,dhcp-release,route-metric 101,ping 12,ping-restart 50,auth-token SESS_ID,comp-lzo yes,redirect-private def1,redirect-private bypass-dhcp,redirect-private autolocal,block-ipv6'
Wed Oct 29 12:03:01 2014 Unrecognized option or missing parameter(s) in [PUSH-OPTIONS]:15: block-ipv6 (2.3.4)
Wed Oct 29 12:03:01 2014 OPTIONS IMPORT: timers and/or timeouts modified
Wed Oct 29 12:03:01 2014 OPTIONS IMPORT: explicit notify parm(s) modified
Wed Oct 29 12:03:01 2014 OPTIONS IMPORT: LZO parms modified
Wed Oct 29 12:03:01 2014 OPTIONS IMPORT: route options modified
Wed Oct 29 12:03:01 2014 OPTIONS IMPORT: route-related options modified
Wed Oct 29 12:03:01 2014 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Wed Oct 29 12:03:01 2014 open_tun, tt->ipv6=0
Wed Oct 29 12:03:01 2014 TAP-WIN32 device [Ethernet 0] opened: \\.\Global\{030DE1EA-31A2-4405-814F-8B71F47CE3D0}.tap
Wed Oct 29 12:03:01 2014 TAP-Windows Driver Version 9.21 
Wed Oct 29 12:03:01 2014 Successful ARP Flush on interface [11] {030DE1EA-31A2-4405-814F-8B71F47CE3D0}
Wed Oct 29 12:03:06 2014 TEST ROUTES: 0/0 succeeded len=0 ret=1 a=0 u/d=up
Wed Oct 29 12:03:06 2014 **NOTE: unable to redirect default gateway -- VPN gateway parameter (--route-gateway or --ifconfig) is missing**
Wed Oct 29 12:03:06 2014 Initialization Sequence Completed
Wed Oct 29 12:03:06 2014 MANAGEMENT: >STATE:1414602186,CONNECTED,SUCCESS,,***.***.***.***
Wed Oct 29 12:03:52 2014 [OpenVPN Server] Inactivity timeout (--ping-restart), restarting
Wed Oct 29 12:03:52 2014 Closing TUN/TAP interface
Wed Oct 29 12:03:52 2014 NOTE: Release of DHCP-assigned IP address lease on TAP-Windows adapter failed: An address has not yet been associated with the network endpoint.   (code=1228)
```

I have tried to edit my server.conf countless times to fix this, but I am a novice with linux. 

What I am doing is this:
Modem->Asus RT-AC66U Router->Server->phpVirtualBox->VM running Ubuntu 14.04 Server 64bit->OpenVPN-AS v2.0.10 64.

I have disabled my routers built in OpenVPN because I cannot configure it as much as I would like. So this was the next best thing I thought. I am trying to run in Bridge mode with TAP. I want to be able to be on the same subnet and access all my devices at home when connected to the VPN. I followed this **[guide]("http://www.slsmk.com/getting-started-with-openvpn/installing-openvpn-on-ubuntu-server-12-04-or-14-04-using-tap/") **and tried to edit to my needs. It looks like I may be missing some steps. 

The main final goal is to be able to connect to my VPN on port 443 and to be able to use Steam In-Home-Streaming over VPN. I was able to do this through my routers built in VPN, but not on port 443. I am also doing this so I can further my knowledge of VBox and Linux as I work in I.T. 

Any help would be greatly appreciated.

---

