---
title: "In syslog my public IP is the SRC, not the private IP."
date: 2016-03-07
forum: Server Platforms
---

### Post by Random20220612 on 2016-03-07
Hello,

I'M running openvpn server over ubuntu server.
client-to-server setup, nothing special.

Looking in the /var/log/syslog I can see the requests are from my public IP address and not from my private IP from network 10.8.0.0 over tun0.
Of course I'm connected as client from my workstation.
I think my access must be from 10.8.0.0 and not from my public IP address.

```
# openvpn client1.ovpn
Mon Mar  7 16:37:13 2016 OpenVPN 2.3.2 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Dec  1 2014
Mon Mar  7 16:37:13 2016 Socket Buffers: R=[212992->131072] S=[212992->131072]
Mon Mar  7 16:37:13 2016 NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Mon Mar  7 16:37:13 2016 UDPv4 link local: [undef]
Mon Mar  7 16:37:13 2016 UDPv4 link remote: [AF_INET]1234:1194
Mon Mar  7 16:37:14 2016 TLS: Initial packet from [AF_INET]1234:1194, sid=4f8f0542 aa41ca8f
Mon Mar  7 16:37:15 2016 VERIFY OK: depth=1, C=UY, ST=UY, L=Montevideo, O=xxxxxx, CN=xxxxxx CA, 
emailAddress=xxxxxxxxxxx
Mon Mar  7 16:37:15 2016 VERIFY OK: nsCertType=SERVER
Mon Mar  7 16:37:15 2016 VERIFY OK: depth=0, C=UY, ST=UY, L=Montevideo, O=xxxxxxxx, CN=server, 
emailAddress=xxxxxxxxx
Mon Mar  7 16:37:17 2016 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Mar  7 16:37:17 2016 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Mar  7 16:37:17 2016 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Mar  7 16:37:17 2016 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Mar  7 16:37:17 2016 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Mon Mar  7 16:37:17 2016 [server] Peer Connection Initiated with [AF_INET]104.238.131.199:1194
Mon Mar  7 16:37:19 2016 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Mon Mar  7 16:37:19 2016 PUSH: Received control message: 'PUSH_REPLY,dhcp-option DNS 208.67.222.222,dhcp-option DNS 208.67.220.220,route 10.8.0.1,topology net30,ping 10,ping-restart 120,ifconfig 10.8.0.6 10.8.0.5'
Mon Mar  7 16:37:19 2016 OPTIONS IMPORT: timers and/or timeouts modified
Mon Mar  7 16:37:19 2016 OPTIONS IMPORT: --ifconfig/up options modified
Mon Mar  7 16:37:19 2016 OPTIONS IMPORT: route options modified
Mon Mar  7 16:37:19 2016 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Mon Mar  7 16:37:19 2016 ROUTE_GATEWAY 192.168.13.1/255.255.255.0 IFACE=wlan0 HWADDR=dc:85:de:8f:9f:25
Mon Mar  7 16:37:19 2016 TUN/TAP device tun0 opened
Mon Mar  7 16:37:19 2016 TUN/TAP TX queue length set to 100
Mon Mar  7 16:37:19 2016 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Mon Mar  7 16:37:19 2016 /sbin/ip link set dev tun0 up mtu 1500
Mon Mar  7 16:37:19 2016 /sbin/ip addr add dev tun0 local 10.8.0.6 peer 10.8.0.5
Mon Mar  7 16:37:19 2016 /sbin/ip route add 10.8.0.1/32 via 10.8.0.5
Mon Mar  7 16:37:19 2016 GID set to nogroup
Mon Mar  7 16:37:19 2016 UID set to nobody
Mon Mar  7 16:37:19 2016 Initialization Sequence Completed
```

In the server log, in this case, the ip showed as SRC connection should be 10.8.0.x 

Also in the openvpn.log i can see all my access as client are from my public ip:

```
# tail -f /etc/openvpn/openvpn.log 
Mon Mar  7 15:37:25 2016 us=897132 client1/167.56.xxx.x:54191 UDPv4 READ [501] from [AF_INET]167.56.xxx.x:54191: P_DATA_V1 kid=0 DATA len=500
Mon Mar  7 15:37:25 2016 us=897197 client1/167.56.xxx.x:54191 TUN WRITE [459]
Mon Mar  7 15:37:25 2016 us=971940 client1/167.56.xxx.x:54191 TUN READ [52]
Mon Mar  7 15:37:25 2016 us=972018 client1/167.56.xxx.x:54191 UDPv4 WRITE [93] to [AF_INET]167.56.xxx.x:54191: P_DATA_V1 kid=0 DATA len=92
Mon Mar  7 15:37:25 2016 us=972055 client1/167.56.xxx.x:54191 TUN READ [56]
Mon Mar  7 15:37:25 2016 us=972072 client1/167.56.xxx.x:54191 UDPv4 WRITE [93] to [AF_INET]167.56.xxx.x:54191: P_DATA_V1 kid=0 DATA len=92
Mon Mar  7 15:37:26 2016 us=42625 client1/167.56.xxx.x:54191 UDPv4 READ [101] from [AF_INET]167.56.xxx.x:54191: P_DATA_V1 kid=0 DATA len=100
Mon Mar  7 15:37:26 2016 us=42716 client1/167.56.xxx.x:54191 TUN WRITE [64]
Mon Mar  7 15:37:26 2016 us=154626 client1/167.56.xxx.x:54191 UDPv4 READ [93] from [AF_INET]167.56.xxx.x:54191: P_DATA_V1 kid=0 DATA len=92
Mon Mar  7 15:37:26 2016 us=154726 client1/167.56.xxx.x:54191 TUN WRITE [52]
```

My server.conf:

```
# cat server.conf 
local 1234
port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key  
dh dh2048.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 208.67.222.222"
push "dhcp-option DNS 208.67.220.220"
keepalive 10 120
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 6
log         openvpn.log


```

In the ufw i setup the postrouting: (before.rules)

```
# START OPENVPN RULES
# NAT table rules
*nat
:POSTROUTING ACCEPT [0:0]
# Allow traffic from OpenVPN client to eth0
-A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE

COMMIT
# END OPENVPN RULES

```

***Any idea?***

---

### Post by darkod on 2016-03-07
That's normal. The log entries are from establishing the tunnel connection, and of course the public IP of the client shows up. Both in /var/log/syslog and /etc/openvpn/openvpn.log.

Also there will be entries from time to time, like when the key gets refreshed (by default it's 1 hour).

Don't worry about it. Is there a problem?

---

### Post by papibe on 2016-03-07
Hi marceloramone.

If I am understanding the logs correctly, you have a PC/client in a LAN with this details:
[LIST]
[*]network: 192.168.13.0
[*]gateway: 192.168.13.1
[*]publicIP: 167.56.xxx.x
[/LIST]
Your OpenVPN server is:
[LIST]
[*]on the Internet, and
[*]its IP is104.238.x.x
[/LIST]
Your private VPN addresses would be 10.8.0.0/24

Is that correct?

If that's the main setup, note that your OpenVPN server knows who you are. First, it receives a connection from your public IP, and then, once connected, it may route traffic over the private addresses. There's no anonymity between the server and the client.

Does that help?
Regards.

---

### Post by Random20220612 on 2016-03-07
Thanks darkod,

I'M trying to close server resources outside openvpn, for example, only allow webserver for openvpn clients, and close for the rest o the world. 
I have ufw running with the following setup:

```
ufw allow 1194/udp

```

in /etc/default/ufw conf:

```
DEFAULT_FORWARD_POLICY="ACCEPT"

```

in /etc/ufw/before.rules conf:

```
# START OPENVPN RULES
# NAT table rules
*nat
:POSTROUTING ACCEPT [0:0] 
# Allow traffic from OpenVPN client to eth0
-A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
COMMIT
# END OPENVPN RULES
```

And this rule to open traffic from 10.8.0.0/24 network:

```
ufw allow from 10.8.0.0/24 to any port 80 proto tcp

```


So the rules are:

```
22                         ALLOW IN    Anywhere
1194/udp                   ALLOW IN    Anywhere
80/tcp                     ALLOW IN    10.8.0.0/24
```

But I'm no able to access the webserver, connected or not connected to the vpn, the ufw is blocking all access.

```
Mar  2 09:03:24 lamp kernel: [61503.549249] [UFW BLOCK] IN=eth0 OUT= MAC=56:00:00:1f:64:e6:fe:00:00:1f:64:e6:08:00 SRC=58.218.xxx.xxx DST=104.238.xx.xxx LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=256 PROTO=TCP SPT=43861 DPT=8888 WINDOW=512 RES=0x00 SYN URGP=0 

```

---

### Post by Random20220612 on 2016-03-07
OMG! My terrible mistake!
   
I was trying to access the webapp from server_public_ip/webapp!!! 
Now I'M accessing form 10.8.0.1/weapp and works!!!

---

### Post by darkod on 2016-03-07
There you go... You solved it. :)

The 10.8.0.0/24 is present only on the vpn tunnel. If you are trying to access with public IP then you are accessing the external interface and your firewall was rejecting it because that's what you told it to do. To access through the vpn you have to use the vpn subnet addresses...

---

