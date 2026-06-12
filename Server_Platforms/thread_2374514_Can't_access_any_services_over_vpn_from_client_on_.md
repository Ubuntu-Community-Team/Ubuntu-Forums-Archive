---
title: "Can't access any services over vpn from client on Ubuntu server"
date: 2017-10-16
forum: Server Platforms
---

### Post by christianhau on 2017-10-16
Hi!

I have an Ubuntu server running 17.04 that I am using to host a Smashing dashboard. I want this dashboard to connect to a Confluence instance which is behind a vpn connection. I have set up the vpn connection on both my Ubuntu server and my windows 10 machine using the client.ovpn and both connect. From my windows machine I can then ping the confluence instance, but from the ubuntu server with the openvpn client on I cannot ping anything that is on the network that I have connected the vpn session for.

I have set up the openvpn client on the ubuntu server with the following guide [https://openvpn.net/index.php/access-server/docs/admin-guides/182-how-to-connect-to-access-server-with-linux-clients.html](https://openvpn.net/index.php/access-server/docs/admin-guides/182-how-to-connect-to-access-server-with-linux-clients.html)

The address that I am trying to reach is confluence.domain.org and on the ubuntu server I get the following message "confluence.domain.org: Name or service not known". I am guessing this has something to do with DNS, but as both are connected to the same vpn server I don't understand why one can reach internal addresses and the other cant?

The output I get when starting the vpn session on the ubuntu machine is as follows:

```
sudo openvpn --config client.ovpn[sudo] password for username:
Mon Oct 16 22:48:37 2017 OpenVPN 2.4.0 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO][LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] built on Jun 22 2017
Mon Oct 16 22:48:37 2017 library versions: OpenSSL 1.0.2g  1 Mar 2016, LZO 2.08
Enter Auth Username: username
Enter Auth Password: ************
Mon Oct 16 22:48:55 2017 Outgoing Control Channel Authentication: Using 160 bitmessage hash 'SHA1' for HMAC authentication
Mon Oct 16 22:48:55 2017 Incoming Control Channel Authentication: Using 160 bitmessage hash 'SHA1' for HMAC authentication
Mon Oct 16 22:48:55 2017 TCP/UDP: Preserving recently used remote address: [AF_INET]52.16.48.250:1194
Mon Oct 16 22:48:55 2017 Socket Buffers: R=[212992->200000] S=[212992->200000]
Mon Oct 16 22:48:55 2017 UDP link local: (not bound)
Mon Oct 16 22:48:55 2017 UDP link remote: [AF_INET]52.16.48.250:1194
Mon Oct 16 22:48:55 2017 TLS: Initial packet from [AF_INET]52.16.48.250:1194, sid=8d01703d c89d6383
Mon Oct 16 22:48:55 2017 VERIFY OK: depth=1, CN=OpenVPN CA
Mon Oct 16 22:48:55 2017 VERIFY OK: nsCertType=SERVER
Mon Oct 16 22:48:55 2017 VERIFY OK: depth=0, CN=OpenVPN Server
Mon Oct 16 22:48:55 2017 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Mon Oct 16 22:48:55 2017 [OpenVPN Server] Peer Connection Initiated with [AF_INET]52.16.48.250:1194
Mon Oct 16 22:48:56 2017 SENT CONTROL [OpenVPN Server]: 'PUSH_REQUEST' (status=1)
Mon Oct 16 22:48:56 2017 PUSH: Received control message: 'PUSH_REPLY,explicit-exase,route-metric 101,ping 12,ping-restart 50,auth-tokenSESS_ID,comp-lzo yes,redirect-private def1,redirect-private bypass-dhcp,
redirect-private autolocal,route-gateway 172.27.236.1,route 10.107.1.0 255.255.255.0,route 10.107.8.0 255.255.248.0,route 172.27.224.0 255.255.240.0,dhcp-option DNS 10.107.1.2,register-dns,block-ipv6,ifconfig 172.27.236.142 255.255.252.0'
Mon Oct 16 22:48:56 2017 Option 'explicit-exit-notify' in [PUSH-OPTIONS]:1 is ig       nored by previous <connection> blocks
Mon Oct 16 22:48:56 2017 Unrecognized option or missing or extra parameter(s) in[PUSH-OPTIONS]:4: dhcp-pre-release (2.4.0)
Mon Oct 16 22:48:56 2017 Unrecognized option or missing or extra parameter(s) in[PUSH-OPTIONS]:5: dhcp-renew (2.4.0)
Mon Oct 16 22:48:56 2017 Unrecognized option or missing or extra parameter(s) in[PUSH-OPTIONS]:6: dhcp-release (2.4.0)
Mon Oct 16 22:48:56 2017 Unrecognized option or missing or extra parameter(s) in[PUSH-OPTIONS]:20: register-dns (2.4.0)
Mon Oct 16 22:48:56 2017 Unrecognized option or missing or extra parameter(s) in[PUSH-OPTIONS]:21: block-ipv6 (2.4.0)
Mon Oct 16 22:48:56 2017 OPTIONS IMPORT: timers and/or timeouts modified
Mon Oct 16 22:48:56 2017 OPTIONS IMPORT: explicit notify parm(s) modified
Mon Oct 16 22:48:56 2017 OPTIONS IMPORT: compression parms modified
Mon Oct 16 22:48:56 2017 OPTIONS IMPORT: --ifconfig/up options modified
Mon Oct 16 22:48:56 2017 OPTIONS IMPORT: route options modified
Mon Oct 16 22:48:56 2017 OPTIONS IMPORT: route-related options modified
Mon Oct 16 22:48:56 2017 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Mon Oct 16 22:48:56 2017 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Oct 16 22:48:56 2017 Data Channel Encrypt: Using 160 bit message hash 'SHA1'for HMAC authentication
Mon Oct 16 22:48:56 2017 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Oct 16 22:48:56 2017 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Oct 16 22:48:56 2017 ROUTE_GATEWAY 10.10.10.254/255.255.255.0 IFACE=ens160 HWADDR=00:0c:29:32:9c:9b
Mon Oct 16 22:48:56 2017 TUN/TAP device tun1 opened
Mon Oct 16 22:48:56 2017 TUN/TAP TX queue length set to 100
Mon Oct 16 22:48:56 2017 do_ifconfig, tt->did_ifconfig_ipv6_setup=0
Mon Oct 16 22:48:56 2017 /sbin/ip link set dev tun1 up mtu 1500
Mon Oct 16 22:48:56 2017 /sbin/ip addr add dev tun1 172.27.236.142/22 broadcast 172.27.239.255
Mon Oct 16 22:49:01 2017 ROUTE remote_host is NOT LOCAL
Mon Oct 16 22:49:01 2017 /sbin/ip route add 52.16.48.250/32 via 10.10.10.254
RTNETLINK answers: File exists
Mon Oct 16 22:49:01 2017 ERROR: Linux route add command failed: external program exited with error status: 2
Mon Oct 16 22:49:01 2017 /sbin/ip route add 10.107.1.0/24 metric 101 via 172.27.236.1
RTNETLINK answers: File exists
Mon Oct 16 22:49:01 2017 ERROR: Linux route add command failed: external program exited with error status: 2
Mon Oct 16 22:49:01 2017 /sbin/ip route add 10.107.8.0/21 metric 101 via 172.27.236.1
RTNETLINK answers: File exists
Mon Oct 16 22:49:01 2017 ERROR: Linux route add command failed: external program exited with error status: 2
Mon Oct 16 22:49:01 2017 /sbin/ip route add 172.27.224.0/20 metric 101 via 172.27.236.1
RTNETLINK answers: File exists
Mon Oct 16 22:49:01 2017 ERROR: Linux route add command failed: external program exited with error status: 2
Mon Oct 16 22:49:01 2017 Initialization Sequence Completed



```

Any help on figuring out why I cant access anything from the Ubuntu server while everything works on the windows 10 machine is much appreciated!

---

### Post by wildmanne39 on 2017-10-16
*Thread moved to **Server Platforms for a better fit**.*

---

### Post by darkod on 2017-10-17
Well, you should start step by step...

First, I see few errors in that vpn client log. Seems like some settings are not applied, maybe because the command has no sudo rights. How are you starting the client, manually? If manually you need to use sudo.

Then, once the vpn is connected, try to ping confluence.domain.org and check the IP it returns (doesn't matter if ping works or is blocked, the important part is to see which IP it is trying to reach). Is the IP what you expect it to be?

If the IP is correct, check that you have a route telling the client to route traffic to that IP over the vpn tunnel.

Also, the client by default can access only the vpn server and only by its vpn IP. If you want to reach other resources on the server side you need further setup.

Since it works from the windows client, and looking at those error messages in the log, my best guess is that you are trying to connect the tunnel without sudo rights so it can't create the necessary routes which will allow to send traffic destined for the vpn over the tunnel.

---

### Post by christianhau on 2017-10-17
Thanks for the response! I connect to the tunnel using sudo as you can see from the first line of the log, if I try to connect without it fails completely. 
When I try to ping the host I am trying to reach I get the following (with domain added instad of actual domain):
ping confluence.domain.org
ping: confluence.domain.org: Name or service not known

From windows I can ping it and it shows the ip address.

You mention that I require further setup, what setup is that? i figured that as long as it worked on my windows client with the same ovpn client file it should work on the linux server, but one thing I saw from the installation page of openvpn was the following:
[h=3]Caveats:[/h][COLOR=#003366][FONT=Arial]When a Linux/Unix client is used with Access Server, the Access Server is unable to alter the DNS settings on the client in question.[/FONT][/COLOR]

---

### Post by christianhau on 2017-10-17
When I connected this morning many of the errors that were there yesterday are gone, but still cant ping the host I am trying to reach:
Tue Oct 17 10:44:52 2017 TUN/TAP device tun0 opened
Tue Oct 17 10:44:52 2017 TUN/TAP TX queue length set to 100
Tue Oct 17 10:44:52 2017 do_ifconfig, tt->did_ifconfig_ipv6_setup=0
Tue Oct 17 10:44:52 2017 /sbin/ip link set dev tun0 up mtu 1500
Tue Oct 17 10:44:52 2017 /sbin/ip addr add dev tun0 172.27.238.152/22 broadcast 172.27.239.255
Tue Oct 17 10:44:57 2017 ROUTE remote_host is NOT LOCAL
Tue Oct 17 10:44:57 2017 /sbin/ip route add 52.16.48.250/32 via 10.10.10.254
Tue Oct 17 10:44:57 2017 /sbin/ip route add 10.107.1.0/24 metric 101 via 172.27.236.1
Tue Oct 17 10:44:57 2017 /sbin/ip route add 10.107.8.0/21 metric 101 via 172.27.236.1
Tue Oct 17 10:44:57 2017 /sbin/ip route add 172.27.224.0/20 metric 101 via 172.27.236.1

---

### Post by darkod on 2017-10-17
Fastest way to try if it's DNS issue is to modify the /etc/hosts on your ubuntu client. Put manually the record for confluence.domain.org:
```
x.x.x.x   confluence.domain.org
```

Save and close the file. Then try the ping again to check if it returns the IP. Then check opening it through the vpn.

---

