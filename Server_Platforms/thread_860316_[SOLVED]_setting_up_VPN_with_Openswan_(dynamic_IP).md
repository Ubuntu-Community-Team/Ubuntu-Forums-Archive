---
title: "[SOLVED] setting up VPN with Openswan (dynamic IP)"
date: 2008-07-15
forum: Server Platforms
---

### Post by Pitt Stains on 2008-07-15
Hi, I'm a programmer who volunteers with a nonprofit organization as their all-purpose IT guy.

I need to set up a VPN in their office so that a new hire who will be working remotely will have access to the file server and other network resources.

Being a programmer, network admin isn't really my thing, so I have a few questions.  I've installed OpenSwan, which was easy enough, but:
[LIST=1]
[*]I'm familiar with the TCP and UDP protocols, but the admin at my day job says OpenSwan is going to need to use the ESP protocol.  He also tells me that routers purchased more than six months ago are unlikely to support ESP.  My question: Who needs ESP?  The router at the office, or the router used by the remote employee, or both?
[*]When I asked the above question, the admin at my day job said that the VPN server wouldn't work if it was sitting behind a router.  He said I needed to stick it right out on the internet, drop a second Ethernet card in it, and use it as a firewall/router in addition to a VPN server.  This means more work for me, so I'm looking for a second opinion on that. :)
[*]The office doesn't have a static IP address, so I'm using DynDNS to point foo.dyndns.com at the office network.  The ipsec.secrets file requires you to enter passwords in this format:

Your.IP.Address.Here %any: PSK "secret shared by two hosts"

Since I don't know my external IP address (it changes), is it OK to put my DynDNS hostname there instead? i.e.,

foo.dyndns.com %any: PSK "secret shared by two hosts"
[/LIST]

I may have more questions as things progress, but these, I think, are crucial to getting started.

Thanks so much for your help,
-Pitt

---

### Post by wepalm on 2008-07-15
> **Pitt Stains said:**
> [LIST=1]
[*]I'm familiar with the TCP and UDP protocols, but the admin at my day job says OpenSwan is going to need to use the ESP protocol.  He also tells me that routers purchased more than six months ago are unlikely to support ESP.  My question: Who needs ESP?  The router at the office, or the router used by the remote employee, or both?[/LIST]


I have never heard of ESP protocol ever.  I know there are a lot but ESP is either incredibly new or not used very often.  I would ask him why ESP and why not TCP/UDP.  Just to be safe

---

### Post by Pitt Stains on 2008-07-15
> **wepalm said:**
> I have never heard of ESP protocol ever.  I know there are a lot but ESP is either incredibly new or not used very often.  I would ask him why ESP and why not TCP/UDP.  Just to be safe

Maybe I'm getting my terminology wrong.  The official OpenSwan page points me to: [http://www.jacco2.dds.nl/networking/openswan-l2tp.html](http://www.jacco2.dds.nl/networking/openswan-l2tp.html), where it says (under section 5.1.1 -- Ports to open on the external interface: IPsec):

> For L2TP/IPsec you need to open the same protocols and ports as for pure IPsec:

    * UDP port 500 (IKE)
    * IP protocol 50 (ESP)
    * UDP port 4500 (NAT-T) - needed if some of your clients are behind a NAT router

Note that IP 50 is a protocol, not a port. As you might know, IP has protocols such as ESP, UDP and TCP. The protocols TCP and UDP on their turn have ports such as TCP 80 (HTTP), UDP 500 (IKE) etc.

---

### Post by koenn on 2008-07-15
Is OpenSwan still being worked on ? I thought it had been replaced by OpenVPN. 

As also indicated by your quote rom OpenSwan website, support for ESP is only required if you use IPsec for your VPN tunnels. OpenVPN uses SSL, so you shouldn't have to worry about ESP support.

Because OpenVPN uses SSL/TLS (a secure transport layer on top of the IP protocol), it's immune for (most IP / network-related) problems other VPN solutions suffer from, such as trouble with firewalls, routing, NAT and so on. So no need for funky network stuff with multiple NIC's and exotic router configs. Just allow traffic on the correct port (94, I think, but look it up - UDP by default but optionally TCP) 

It should also work with dynamic addresses, even on both sides (server + remote client) but that can be a bit tricky to set up. You can usually replace IP addresses with DNS hostnames provided you have access to a relevant, knowledgeable DNS server *before* the vpn tunnel is created - as is the case with dyndns

I seem to remember that OpenVPN started as a fork / continuation of (Open)Swan, so maybe swan also supports the SSL/TLS method. Or you can just switch. [http://openvpn.net/](http://openvpn.net/)
it's also in the ubuntu repos and I do remember seeing quite a few threads about it around here.

---

### Post by Pitt Stains on 2008-07-16
OK, Koenn,

I've taken your advice and installed OpenVPN instead.  I was doing pretty well until I got to the testing phase...

I've installed OpenVPN on the Ubuntu server in the office and opened the appropriate port.  To test it, I installed the OpenVPN Gui for Windows ([http://openvpn.se/](http://openvpn.se/)) on a laptop that is connecting to the Internet via EVDO (i.e., it's definitely on a different network).

Notes about my environment:
[LIST=1]
[*]The internal IP address of the gateway in the office here is 10.10.10.1. It's just a simple router.
[*]The laptop runs Windows XP SP2.  Windows firewall is turned off.
[/LIST]

I start OpenVPN with...

```
sudo openvpn --config /etc/openvpn/server.conf
```

... so I can watch all the output.  Here's what I get:

> Tue Jul 15 23:46:16 2008 OpenVPN 2.0.9 i486-pc-linux-gnu [SSL] [LZO] [EPOLL] built on Jun 11 2008
Tue Jul 15 23:46:16 2008 Diffie-Hellman initialized with 1024 bit key
Tue Jul 15 23:46:16 2008 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Tue Jul 15 23:46:16 2008 TLS-Auth MTU parms [ L:1574 D:138 EF:38 EB:0 ET:0 EL:0 ]
Tue Jul 15 23:46:16 2008 TUN/TAP device tap0 opened
Tue Jul 15 23:46:16 2008 Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ]
Tue Jul 15 23:46:16 2008 GID set to nogroup
Tue Jul 15 23:46:16 2008 UID set to nobody
Tue Jul 15 23:46:16 2008 UDPv4 link local (bound): [undef]:1194
Tue Jul 15 23:46:16 2008 UDPv4 link remote: [undef]
Tue Jul 15 23:46:16 2008 MULTI: multi_init called, r=256 v=256
Tue Jul 15 23:46:16 2008 IFCONFIG POOL: base=10.10.10.241 size=9
Tue Jul 15 23:46:16 2008 IFCONFIG POOL LIST
Tue Jul 15 23:46:16 2008 Initialization Sequence Completed

This all looks good to me, so I head over to the Windows laptop and initiate the connection.  When I do this, I get some activity on the Linux terminal, pasted below.  I've substituted 70.70.70.70 for my real external IP address.

> Tue Jul 15 23:49:37 2008 MULTI: multi_create_instance called
Tue Jul 15 23:49:37 2008 70.70.70.70:1146 Re-using SSL/TLS context
Tue Jul 15 23:49:37 2008 70.70.70.70:1146 LZO compression initialized
Tue Jul 15 23:49:37 2008 70.70.70.70:1146 Control Channel MTU parms [ L:1574 D:138 EF:38 EB:0 ET:0 EL:0 ]
Tue Jul 15 23:49:37 2008 70.70.70.70:1146 Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ]
Tue Jul 15 23:49:37 2008 70.70.70.70:1146 Local Options hash (VER=V4): 'f7df56b8'
Tue Jul 15 23:49:37 2008 70.70.70.70:1146 Expected Remote Options hash (VER=V4): 'd79ca330'
Tue Jul 15 23:49:37 2008 70.70.70.70:1146 TLS: Initial packet from 70.70.70.70:1146, sid=b67bf5c7 0617d3d8
Tue Jul 15 23:49:37 2008 70.70.70.70:1146 write UDPv4 []: Network is unreachable (code=101)
Tue Jul 15 23:50:36 2008 70.70.70.70:1146 write UDPv4 []: Network is unreachable (code=101)
Tue Jul 15 23:50:37 2008 70.70.70.70:1146 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Tue Jul 15 23:50:37 2008 70.70.70.70:1146 TLS Error: TLS handshake failed
Tue Jul 15 23:50:37 2008 70.70.70.70:1146 SIGUSR1[soft,tls-error] received, client-instance restarting

One thing that strikes me a little odd is that the port number in the output pasted above is 1146, whereas the port I've specified in my config is 1194.

The server.conf file is as follows:

```
port 1194

proto udp

dev tap0

ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/server.crt
key /etc/openvpn/easy-rsa/keys/server.key  # This file should be kept secret

dh /etc/openvpn/easy-rsa/keys/dh1024.pem

ifconfig-pool-persist ipp.txt

server-bridge 10.10.10.240 255.255.255.0 10.10.10.241 10.10.10.249

keepalive 10 120

comp-lzo

user nobody
group nogroup

persist-key
persist-tun

status openvpn-status.log

verb 3
```

The client file on the Windows laptop is as follows:

```

client

dev tap0

proto udp

remote host.dyndns.org 1194

resolv-retry infinite

nobind

persist-key
persist-tun

ca ca.crt
cert client.crt
key client.key

comp-lzo

verb 3
```

Any suggestions on where to begin diagnosing the problem?  Thanks so much!

---

### Post by koenn on 2008-07-16
Well, I've never set up openvpn myself, but I know of commercial implementations that work really well, I've read some positive comments about it on these forums. I do have a fair understanding of networks and how Openvpn works, so it felt appropriate to suggest it. 
If that's enough to help you troubleshoot it remains to be seen :)

---
If I understand correctly that your 2nd quote is terminal output *on the vpn server*, while the client tries to initiate a connection, then I'd say

- about the 1146 port number. It's normal for **clients** to use arbitrary port numbers.Servers need fixed port numbers ("service ports", eg 1194/udp for vpn server) because clients initiate the connection, so they need to know a port number to know where to connect.  Clients use arbitrary port numbers but tell the server which port the are connecting from, so that the server know what port to send a reply to. 
I don't know whether you're supposed to see 

-- it looks like the server can't send its reply (write UDPv4, probably short for "can not write to that udp socket") because "[destination] network is unreachable".

-- as a consequence, the client and the server can't talk to each other, so the first thing they have to talk about (TLS authentication, handshake, ...) also fails. So your vpn isn't working. 


Although there could be numerous reasons for the server reply not reaching the client (firewall, ... ), udp is "fire and forget", it doesn't check if packets ever reach their destination. That, and the "network unreachable", suggests there's a problem in the server network config or on the network where the server lives, or the network design of your test environment. Are the server and te client on separate networks ?

It's hard to diagnose those things from here, especially with obfuscated IP addresses. Also, if 70.70.70.70 is supposed to be your servers's public address, does that mean that same address appears in the line
" Initial** packet from **70.70.70.70:1146 "? Is the server talking to itself ? 

I hope this helps you on your way ...

---

### Post by Pitt Stains on 2008-07-17
Success!  This tutorial proved invaluable: [http://www.thebakershome.net/openvpn_tutorial](http://www.thebakershome.net/openvpn_tutorial).  If anyone wants any specific info or wants to see my configs, just post here.

---

### Post by emanaton on 2008-10-20
> **Pitt Stains said:**
> Success!  This tutorial proved invaluable: [http://www.thebakershome.net/openvpn_tutorial](http://www.thebakershome.net/openvpn_tutorial).  If anyone wants any specific info or wants to see my configs, just post here.

Greetings Pitt,

I'm having the same problem and am having difficulty solving it. I'd LOVE to see your config file or, if you recall, what the specific fix was to the issue?

Thanks,

Sean P. O. MacCath-Moran
[www.emanaton.com](www.emanaton.com)

---

