---
title: "Openvpn initializes but domain is not resolved"
date: 2018-02-18
forum: Security
---

### Post by acefalobi on 2018-02-18
I am trying to access a vpn using the openvpn in the command line. The command works and the following log is displayed

```

acefalobi@kali:~/Seedstars/git-lab$ sudo openvpn --config openvpn.ovpn
Sun Feb 18 12:21:02 2018 OpenVPN 2.4.4 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] built on Dec 10 2017
Sun Feb 18 12:21:02 2018 library versions: OpenSSL 1.1.0g  2 Nov 2017, LZO 2.08
Enter Auth Username: ace
Enter Auth Password: ********
Sun Feb 18 12:21:08 2018 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Sun Feb 18 12:21:08 2018 NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Sun Feb 18 12:21:08 2018 TCP/UDP: Preserving recently used remote address: [AF_INET]52.213.12.22:443
Sun Feb 18 12:21:08 2018 Socket Buffers: R=[87380->87380] S=[16384->16384]
Sun Feb 18 12:21:08 2018 Attempting to establish TCP connection with [AF_INET]52.213.12.22:443 [nonblock]
Sun Feb 18 12:21:09 2018 TCP connection established with [AF_INET]52.213.12.22:443
Sun Feb 18 12:21:09 2018 TCP_CLIENT link local: (not bound)
Sun Feb 18 12:21:09 2018 TCP_CLIENT link remote: [AF_INET]52.213.12.22:443
Sun Feb 18 12:21:10 2018 TLS: Initial packet from [AF_INET]52.213.12.22:443, sid=56e50002 e5ff3bb2
Sun Feb 18 12:21:10 2018 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Sun Feb 18 12:21:10 2018 VERIFY OK: depth=1, C=CH, ST=GE, L=Geneva, O=Seedstars, OU=OpenVPN Server, CN=Seedstars CA, emailAddress=lr@seedstars.com
Sun Feb 18 12:21:10 2018 VERIFY OK: depth=0, C=CH, ST=GE, L=Geneva, O=Seedstars, OU=OpenVPN Server, CN=server, emailAddress=lr@seedstars.com
Sun Feb 18 12:21:11 2018 Control Channel: TLSv1.2, cipher TLSv1.2 DHE-RSA-AES256-GCM-SHA384, 2048 bit RSA
Sun Feb 18 12:21:11 2018 [server] Peer Connection Initiated with [AF_INET]52.213.12.22:443
Sun Feb 18 12:21:12 2018 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Sun Feb 18 12:21:12 2018 PUSH: Received control message: 'PUSH_REPLY,route 172.16.0.0 255.255.0.0,dhcp-option DOMAIN int.seedstars.com,dhcp-option DOMAIN-SEARCH int.seedstars.com,dhcp-option DNS 172.16.0.2,route 172.31.0.1,topology net30,ping 10,ping-restart 120,ifconfig 172.31.27.234 172.31.27.233'
Sun Feb 18 12:21:12 2018 OPTIONS IMPORT: timers and/or timeouts modified
Sun Feb 18 12:21:12 2018 OPTIONS IMPORT: --ifconfig/up options modified
Sun Feb 18 12:21:12 2018 OPTIONS IMPORT: route options modified
Sun Feb 18 12:21:12 2018 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Sun Feb 18 12:21:12 2018 Outgoing Data Channel: Cipher 'AES-256-CBC' initialized with 256 bit key
Sun Feb 18 12:21:12 2018 Outgoing Data Channel: Using 512 bit message hash 'SHA512' for HMAC authentication
Sun Feb 18 12:21:12 2018 Incoming Data Channel: Cipher 'AES-256-CBC' initialized with 256 bit key
Sun Feb 18 12:21:12 2018 Incoming Data Channel: Using 512 bit message hash 'SHA512' for HMAC authentication
Sun Feb 18 12:21:12 2018 ROUTE_GATEWAY 192.168.43.1/255.255.255.0 IFACE=wlan0 HWADDR=b0:10:41:ed:78:21
Sun Feb 18 12:21:12 2018 TUN/TAP device tun0 opened
Sun Feb 18 12:21:12 2018 TUN/TAP TX queue length set to 100
Sun Feb 18 12:21:12 2018 do_ifconfig, tt->did_ifconfig_ipv6_setup=0
Sun Feb 18 12:21:12 2018 /sbin/ip link set dev tun0 up mtu 1500
Sun Feb 18 12:21:12 2018 /sbin/ip addr add dev tun0 local 172.31.27.234 peer 172.31.27.233
Sun Feb 18 12:21:12 2018 /etc/openvpn/update-resolv-conf tun0 1500 1604 172.31.27.234 172.31.27.233 init
Sun Feb 18 12:21:12 2018 /sbin/ip route add 172.16.0.0/16 via 172.31.27.233
Sun Feb 18 12:21:12 2018 /sbin/ip route add 172.31.0.1/32 via 172.31.27.233
Sun Feb 18 12:21:12 2018 Initialization Sequence Completed



```

But when I try to access the domain, chrome tells me that it can't resolve the name.

I used the GTK interface and created a vpn connection in the Network Settings using the same .ovpn file and connected using that. This time, it worked and I could connect to the domain. The only problem was that I couldn't connect to other websites when I connected to the VPN.

I searched online and saw that the most common solution was to just use the openvpn commandline. But this is not working for me and I am in a dilema.

Please help :(

---

### Post by oldos2er on 2018-02-18
You marked the thread 'Solved,' would you please post the solution so that others may benefit from it?

---

