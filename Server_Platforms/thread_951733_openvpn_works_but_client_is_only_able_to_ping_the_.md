---
title: "openvpn works but client is only able to ping the server"
date: 2008-10-18
forum: Server Platforms
---

### Post by samosamo on 2008-10-18
i'm looking to get a configuration working where i connect to my home LAN while at a wifi coffee shop and i'm able to see all machines on the network.  they call it a "road warrior config." currently, after connecting to the vpn, my client is able to ping the openvpn server but not able to ping any other machines on the 192.168 network.  i'm concerned that my router is to blame. many of the tutorials i see assume the openvpn server is the same device as the router, but i want to make it clear that all my router is doing right now is forwarding port 1194/udp to the actual openvpn server.  does it need additional settings?

The openvpn server is NAT'd behind a router at 192.168.3.1
VPN range: 10.8.0.0
Home range: 192.168.3.0

openvpn server: 10.8.0.1 or 192.168.3.10

> 
port 1194
proto udp
dev tun0
ca keys/samosamo.org/ca.crt
cert keys/samosamo.org/samosamo.org.crt
key keys/samosamo.org/samosamo.org.key
dh keys/samosamo.org/dh2048.pem
server 10.8.0.0 255.255.255.0
crl-verify keys/samosamo.org/crl.pem
ifconfig-pool-persist servers/samosamo.org/logs/ipp.txt
cipher AES-128-CBC
user nobody
group nogroup
status servers/samosamo.org/logs/openvpn-status.log
log-append servers/samosamo.org/logs/openvpn.log
verb 2
mute 20
max-clients 100
keepalive 10 120
client-config-dir /etc/openvpn/servers/samosamo.org/ccd
client-to-client
comp-lzo
persist-key
persist-tun
ccd-exclusive
push "route 192.168.3.0 255.255.255.0"


> 
client
proto udp
dev tun
ca ca.crt
dh dh2048.pem
cert samosamo.crt
key samosamo.key
remote samosamo.org 1194
cipher AES-128-CBC
verb 2
mute 20
keepalive 10 120
comp-lzo
persist-key
persist-tun
float
resolv-retry infinite
nobind


I'm not that good with routing so I'm not sure if I'm doing anything wrong. Some tutorials have info about iptables but since I'm not using iptables, I ignore those steps. Is that my problem?

> iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

> 
route printout on openvpn server:
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.2        *               255.255.255.255 UH    0      0        0 tun0
192.168.3.0     *               255.255.255.0   U     0      0        0 eth0
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
default         tomato          0.0.0.0         UG    100    0        0 eth0

route printout on router machine (not sure if it matters):
# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.3.0     *               255.255.255.0   U     0      0        0 br0
24.190.32.0     *               255.255.224.0   U     0      0        0 vlan1
127.0.0.0       *               255.0.0.0       U     0      0        0 lo
default         ool-18be2001.dy 0.0.0.0         UG    0      0        0 vlan1


as of right now, from my VPN connected laptop I can ping 10.8.0.1 as well as 192.168.3.10 (same machine).  I am NOT able to ping other machines, for example, the machine I'm typing on now at 192.168.3.13.  I can ping this machine from inside the network though.

---

### Post by Zeosa on 2008-10-18
Try:

echo 1 > /proc/sys/net/ipv4/ip_forward on the server


To make it permanent uncomment "net.ipv4.ip_forward=1" in /etc/sysctl.conf

---

### Post by samosamo on 2008-10-18
> **Zeosa said:**
> Try:

echo 1 > /proc/sys/net/ipv4/ip_forward on the server


To make it permanent uncomment "net.ipv4.ip_forward=1" in /etc/sysctl.conf

i forgot to mention that i have done that already

> $ cat /proc/sys/net/ipv4/ip_forward
1

---

### Post by samosamo on 2008-10-19
bump, i have edited the original post with more info

---

### Post by samosamo on 2008-10-19
I found something [http://openvpn.net/index.php/documentation/faq.html](http://openvpn.net/index.php/documentation/faq.html)

> I've successfully set up OpenVPN and can ping between both OpenVPN peers, however I cannot reach any of the other machines on the remote subnet. What's the problem?

    *

      Make sure that the firewall is not filtering the TUN/TAP interface.
    *

      Make sure you have IP forwarding enabled on the server.
    * If you are using routing (not ethernet bridging), make sure the clients (or LAN gateway) have a route back to the server for the packets coming in over the tunnel. This can be done by:
          o adding a route in your default gateway for the VPN network IP subnet pointing to the OpenVPN machine,
          o adding a route to every client, or
          o NATing all VPN traffic to the local address of the OpenVPN machine for network traffic which leaves the OpenVPN machine for the local net.
    *

      If you are still stumped, use tcpdump, wireshark, or WinDump to determine where packets are being dropped.

Problem is, I have no idea how to add the proper route to the router :(  Can anyone help ?

---

### Post by samosamo on 2008-10-20
Solved by myself, after YEARS of frustration.

The problem was I am running the openvpn server behind the NAT gateway.  I had to add a route on my gateway:

> 10.8.0.0 255.255.255.0 192.168.3.10
^- vpn                    ^-openvpn server

I assume this step is only necessary because the NAT gateway has nowhere to send packets on the 10.8 network unless you tell it where to go

---

### Post by kevdog on 2008-10-20
Could you post the entire solution and I'm assuming this change made it into the server.conf file.  Could you re-post this?  Thanks

---

### Post by samosamo on 2008-10-20
The problem: Firewalled OpenVPN establishes route to client, but client cannot access LAN behind the OpenVPN server.

The solution: In addition to configuring routes on the server/client (openvpn does this for you with the proper config) you need to add a route to the LAN gateway (may be your small wifi router usually 192.168.1.1 or similar).  Assuming your VPN is 10.8.0.0 and your OpenVPN server is running on 192.168.3.10 your route on the LAN gateway should look like this:
**10.8.0.0 192.168.3.10 255.255.255.0 **


Trust me this is NOT properly documented anywhere on the net, despite the hundreds of posts on the openvpn discussion forums.

---

### Post by kevdog on 2008-10-20
Where do you type this statement?

Also if your router is 192.168.1.1, how do you have a Local LAN that runs on 192.168.3.x?

Is this statement in the server.conf file like like:

route 10.8.0.0 255.255.255.0 192.168.3.10

And is this an equivalent statement (try this):

route 10.8.0.0 255.255.255.0 vpn_gateway

Note that vpn_gateway is a reserved key word, another is net_gateway.  These are both documented in the documentation.

---

### Post by samosamo on 2008-10-20
why are you not following me ?

192.168.1.1 = many routers (LAN gateway) that you buy at the store use this as a default IP.  it was just an example

192.168.3.1 = my actual LAN gateway's ip, in real life

the route that i added was actually not "typed in" anywhere but entered through my router's GUI web config.  but type "man route" in linux and "route help" in windows if you want to do it in cli.

thanks for the vpn_gateway trick but i don't use that 3rd parameter, as you can see in the config i posted.  i'm pretty sure its set to vpn_gateway by default anyway.

---

### Post by kevdog on 2008-10-21
What router are you using with firmware?  Could you repost your router server config file with modification please?

I'm also unaware of this syntax:
10.8.0.0 192.168.3.10 255.255.255.0 

routes are usually defined by an ipaddress and then netmask (not two consecutive ip addresses then a netmask).  Ive typed man route (although Ive done this before, and this verified the proper syntax).

---

