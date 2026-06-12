---
title: "I can't ping behind openvpn server"
date: 2012-03-05
forum: Server Platforms
---

### Post by pepe308 on 2012-03-05
Hello,

i spend hours but no solution. I'm connected to my ubuntu server 10.10 with openvpn. I can ping the local ip (192.168.0.15) of the server and its vpn ip (192.168.1.1) but i can't ping other computer on the network behind the server (for exemple 192.168.0.3 or 192.168.0.5).

if config :
[COLOR="DarkRed"]eth0      Link encap:Ethernet  HWaddr 20:cf:30:af:f7:41  
          inet adr:192.168.0.15  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: 2a01:e35:2420:62e0:22cf:30ff:feaf:f741/64 Scope:Global
          adr inet6: fe80::22cf:30ff:feaf:f741/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:21057 erreurs:0 :0 overruns:0 frame:0
          TX packets:16413 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:6025793 (6.0 MB) Octets transmis:4213513 (4.2 MB)
          Interruption:45 Adresse de base:0xe000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:22708 erreurs:0 :0 overruns:0 frame:0
          TX packets:22708 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:4540642 (4.5 MB) Octets transmis:4540642 (4.5 MB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet adr:192.168.1.1  P-t-P:192.168.1.2  Masque:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          Packets reçus:1533 erreurs:0 :0 overruns:0 frame:0
          TX packets:809 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:100 
          Octets reçus:128772 (128.7 KB) Octets transmis:69202 (69.2 KB)

virbr0    Link encap:Ethernet  HWaddr 52:e0:9f:56:0a:16  
          inet adr:192.168.122.1  Bcast:192.168.122.255  Masque:255.255.255.0
          adr inet6: fe80::50e0:9fff:fe56:a16/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:0 (0.0 B) Octets transmis:55304 (55.3 KB)[/COLOR]

my server.conf :
[COLOR="DarkOrange"]
local 192.168.0.15
port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh1024.pem
server 192.168.1.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 192.168.0.0 255.255.255.0"
client-to-client
keepalive 10 120
comp-lzo
max-clients 100
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 10
mute 20[/COLOR]

my route table :
[COLOR="Indigo"]
Destination     Gateway      Genmask         Indic Metric Ref    Use Iface
192.168.1.2     *               255.255.255.255 UH    0      0        0 tun0
192.168.1.0     192.168.1.2     255.255.255.0   UG    0      0        0 tun0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
default         freebox-server. 0.0.0.0         UG    100    0        0 eth0
[/COLOR]

I red a lot of documents but no way to ping the internal network behind the vpn.

Thank you,
Mickael

---

### Post by spynappels on 2012-03-05
Do you have a static route back to the 192.168.1.0 network set up in your router? It needs to point to 192.168.0.15 as the gateway for any 192.168.1.0 traffic.

You also need to have ipv4 forwarding enabled on the OpenVPN server, not sure if you've done that yet?

---

### Post by pepe308 on 2012-03-05
ipv4 fowarding is already enabled.

Every time i had "route 192.168.0.0 255.255.255.0" in my server.conf, i can see in route :
"192.168.0.0     192.168.1.2     255.255.255.0   UG 0  0 0 tun0" 

And juste after, i lost the connexion with my server.

---

### Post by Sergius14 on 2012-03-05
Like already been said, you need to set up a route n your local router...

Every PC have a Default-Gateway. That Router/Server, has to have this route.

Another way is to add a manual route in every PC/Server.


If your local router/default gateway is this server (I think that is not this case), you should check for Firewall/IPTable issue. Wireshark might give you some clues, about if traffic is passing or not.


Regards,

---

### Post by pepe308 on 2012-03-06
> **spynappels said:**
> Do you have a static route back to the 192.168.1.0 network set up in your router? It needs to point to 192.168.0.15 as the gateway for any 192.168.1.0 traffic.

You also need to have ipv4 forwarding enabled on the OpenVPN server, not sure if you've done that yet?

Do you mean, i need to create a route with this parameters :
Destination = 192.168.1.0
Gateway = 192.168.0.15
Interface = tun0

????

I think that's what i don't understand.

Thank you a lot,

---

### Post by spynappels on 2012-03-06
Hi M.

You do not need to create that route on the server, you need to create a static route on your router/modem. 
This route should be 
network 192.168.1.0
netmask 255.255.255.0
gateway 192.168.0.15

What is happening is that your ping packet makes it to the remote host fine, but the reply is sent to the default gateway because all the remote host knows is that the originating address is not on it's own subnet. The default gateway does not know how to reach this address either, so it fires it out to it's own next hop to the internet, and the packet is lost.
This default gateway is normally a router/modem through which you get your internet connection.

What you need to do is set a static route on this gateway which tells it to forward all traffic for the 192.168.1.0 subnet to 192.168.0.15, rather than to it's own default gateway, which will be your ISP's router. 

You could also create a static route on each of the hosts in the 192.168.0.0 network, pointing to 192.168.0.15 as the gateway for all 192.168.1.0 traffic, but this is much more work.

I'd look at adding a static route on your router first.

---

### Post by pepe308 on 2012-03-06
Ok, i will test that.
I'm just analysing traffic with tshark and i have :
on tap0 :
[COLOR="DarkSlateBlue"]
0.000000  192.168.1.6 -> 192.168.0.3  ICMP Echo (ping) request
  1.000231  192.168.1.6 -> 192.168.0.3  ICMP Echo (ping) request
  2.001338  192.168.1.6 -> 192.168.0.3  ICMP Echo (ping) request
  3.043827  192.168.1.6 -> 192.168.0.3  ICMP Echo (ping) request
  4.046146  192.168.1.6 -> 192.168.0.3  ICMP Echo (ping) request
  5.046061  192.168.1.6 -> 192.168.0.3  ICMP Echo (ping) request
  6.047888  192.168.1.6 -> 192.168.0.3  ICMP Echo (ping) request
  7.048492  192.168.1.6 -> 192.168.0.3  ICMP Echo (ping) request
  8.048387  192.168.1.6 -> 192.168.0.3  ICMP Echo (ping) request
  9.049517  192.168.1.6 -> 192.168.0.3  ICMP Echo (ping) request
[/COLOR]

on eth0 :
[COLOR="DarkRed"]
0.615499 92.146.210.43 -> 192.168.0.15 TCP 50263 > ssh [ACK] Seq=1 Ack=161 Win=65535 Len=0 TSV=182148044 TSER=2184529
  1.543111 92.146.210.43 -> 192.168.0.15 UDP Source port: 52220  Destination port: openvpn
  1.543867  192.168.1.6 -> 192.168.0.3  ICMP Echo (ping) request
  1.546862 192.168.0.15 -> 92.146.210.43 SSH Encrypted response packet len=336
  1.647528 92.146.210.43 -> 192.168.0.15 TCP 50263 > ssh [ACK] Seq=1 Ack=497 Win=65535 Len=0 TSV=182149070 TSER=2184784
  2.543263 92.146.210.43 -> 192.168.0.15 UDP Source port: 52220  Destination port: openvpn
  2.543987  192.168.1.6 -> 192.168.0.3  ICMP Echo (ping) request
  2.546901 192.168.0.15 -> 92.146.210.43 SSH Encrypted response packet len=400
......
[/COLOR]

---

### Post by spynappels on 2012-03-06
That tshark trace just points out what I was saying. The OpenVPN server is forwarding the ping requests out of the eth0 interface so it is routing them correctly, but it is not seeing any replies because the replies are not being routed back to the OpenVPN server for forwarding out through the tun0 interface.

---

### Post by pepe308 on 2012-03-06
Indeed, on the 192.168.0.3 host i have:
[COLOR="DarkGreen"]
7.881416  192.168.1.6 -> 192.168.0.3  ICMP 98 Echo (ping) request  id=0xa1a7, seq=2/512, ttl=63
  7.881468  192.168.0.3 -> 192.168.1.6  ICMP 98 Echo (ping) reply    id=0xa1a7, seq=2/512, ttl=64
[/COLOR]

Where 192.168.1.6 is my computer ip on vpn network. So it's clear it can't access to 192.168.1.6

So i created the route :

[COLOR="DarkOrange"]
sudo route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.0.15
[/COLOR]

my table was :
[COLOR="Indigo"]
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.1.2     0.0.0.0         255.255.255.255 UH    0      0        0 tun0
192.168.1.0     192.168.0.15    255.255.255.0   UG    0      0        0 eth0
192.168.1.0     192.168.1.2     255.255.255.0   UG    0      0        0 tun0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.254   0.0.0.0         UG    100    0        0 eth0
[/COLOR]

So it's ok but i can't access 192.168.1.1 (the vpn ip of 192.168.0.15 server) anymore. I can't see the vpn network anymore.

Why ?

Second question, what is 192.168.1.2 because it isn't a real host and i can't ping it from 192.168.0.15 server... ???

Thanks again.

---

### Post by spynappels on 2012-03-06
This is because each vpn client creates a tunnel with the VPN server at one end with ip 192.168.1.x and the client with ip 192.168.1.x+1 at the other. OpenVPN does some clever stuff so the server is seen as being at 192.168.1.1 even though the endpoint from any client is some other ip.

Just as an aside, you may be better using less common subnets both for your LAN and for the IPs used by OpenVPN, both 192.168.0.0 and 192.168.1.0 are commonly used as defaults on SOHO routers and you might get unexpected results if you try to connect to your VPN and access hosts on your LAN from a location that uses one of these subnets.

I use 192.168.10.0/24 for my LAN and 10.0.18.0/24 for my OpenVPN deployment and have never had any problems.

---

### Post by pepe308 on 2012-03-06
Thank you for the explanation.
I had to change my home lan because it was also 192.168.0.0/24.
Before psoting ont hat forum i checked and there are no conflicts.

Do you know why the route adding cut the connexion between me (client vpn ip 192.168.1.6) and the server (both 192.168.1.1 on vpn and 192.168.0.15) ?

Before route adding :
[COLOR="DarkOrange"]
traceroute to 192.168.1.6 (192.168.1.6), 30 hops max, 60 byte packets
 1  192.168.1.6 (192.168.1.6)  74.272 ms  77.143 ms  78.304 ms
[/COLOR]

After :
[COLOR="DarkRed"]
traceroute to 192.168.1.6 (192.168.1.6), 30 hops max, 60 byte packets
 1  192.168.0.15 (192.168.0.15)  3001.407 ms !H  3001.398 ms !H  3001.388 ms !H
[/COLOR]

And with tshark, if i ping from 192.168.0.15 to 192.168.1.6, i have :
  4.505299 AsustekC_af:f7:41 -> Broadcast    ARP Who has 192.168.1.6?  Tell 192.168.0.15

---

### Post by spynappels on 2012-03-06
Are the netmasks definitely correct?

---

### Post by pepe308 on 2012-03-06
yep.

I just sucess like that :
No route adding on the server but route adding on 192.168.0.3 :

[COLOR="Navy"]
sudo route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.0.15
[/COLOR]

---

### Post by spynappels on 2012-03-06
> **pepe308 said:**
> yep.

I just sucess like that :
No route adding on the server but route adding on 192.168.0.3 :

[COLOR="Navy"]
sudo route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.0.15
[/COLOR]

Yes, of course, the route had to be added on a LAN host.:oops:

---

### Post by pepe308 on 2012-03-06
No problem, you help me a lot.

Do you know a way to create that route on all the LAN hosts through openvpn server.conf ??

Thanks

---

### Post by spynappels on 2012-03-06
No, there is no way to do that as the LAN hosts have nothing to do with the OpenVPN server. That is why creating a static route in the router/modem is a more elegant solution.

---

