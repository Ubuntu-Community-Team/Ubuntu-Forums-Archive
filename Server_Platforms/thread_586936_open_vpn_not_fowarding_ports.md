---
title: "open vpn not fowarding ports"
date: 2007-10-22
forum: Server Platforms
---

### Post by nownto on 2007-10-22
hello all. im trying to get my vpn server up and running. this is the point im at now, i can connect and what not but i cant get the traffic to be forwarded. once i connect the inet traffice just dies. below i pasted my server.conf, client.conf, route on vpn, and my iptables setup. my network is based on 192.168.1.255 with 192.168.1.1 being my router/gateway. thanks for any help.


server.conf
[http://pastebin.ca/745763](http://pastebin.ca/745763)


client.conf
[http://pastebin.ca/745766](http://pastebin.ca/745766)

routes

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.2        *               255.255.255.255 UH    0      0        0 tun0
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0




Chain INPUT (policy ACCEPT 45661 packets, 8741K bytes)
 pkts bytes target     prot opt in     out     source               destination      
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:www
 1193 96928 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ssh
    0     0 ACCEPT     0    --  tun+   any     anywhere             anywhere         
    0     0 ACCEPT     0    --  tap+   any     anywhere             anywhere         
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ftp
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ftp

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination      
    0     0 ACCEPT     0    --  tun+   any     anywhere             anywhere         
    0     0 ACCEPT     0    --  tap+   any     anywhere             anywhere         

Chain OUTPUT (policy ACCEPT 42013 packets, 2726K bytes)
 pkts bytes target     prot opt in     out     source               destination  
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

---

### Post by steve.horsley on 2007-10-22
Your firewall doesn't seem to be doing a lot - it only has accept statements, and the default policy is also accept. I notise there are no ACCEPT statements in the FORWARD chain allowing packets from eth0 to the tunnel. Still, it is worth trying with the firewall disabled just to prove that's not the problem.

Have you enabled packet forwarding? This command does it:
**echo 1 > /proc/sys/net/ipv4/ip_forward**
I recently installed an OpenVPN service on Feisty, and adding the following line to **/etc/sysctl.conf** caused forwarding to be enabled every time the server reboots:
**net.ipv4.ip_forward=1**
Note that this is different to the commented-out lines in the file. I found that uncommentng those had no effect - perhaps I should file a bug report. I don't know if the same line would work on Gutsy, but you could try it. The command:
**cat /proc/sys/net/ipv4/ip_forward**
will tell you if forwarding is enabled.

P.S.
I couldn't contact the links you posted. DNS doesn't seem to resolve.

PPS
I just tried editing /etc/sysctl.conf on Gutsy. Again, the line I give turns forwarding on, but the line given in the file doesn't work. Unbelievable.

---

### Post by nownto on 2007-10-22
ok i have the ipfowarding working but its still not doing fowarding my net. this is my new iptables looks like i have some traffic  but still not working.
Chain INPUT (policy ACCEPT 5226 packets, 991K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:www 
  260 21600 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ssh 
    0     0 ACCEPT     0    --  tun+   any     anywhere             anywhere            
    0     0 ACCEPT     0    --  tap+   any     anywhere             anywhere            
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ftp 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ftp 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   32  2295 ACCEPT     0    --  tun+   any     anywhere             anywhere            
    0     0 ACCEPT     0    --  tap+   any     anywhere             anywhere            

Chain OUTPUT (policy ACCEPT 4857 packets, 290K bytes)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by steve.horsley on 2007-10-23
I dont know what's wrong. I don't think it's your firewall - it isn't configured to block anything. You might as well turn it off, although it is useful to have it counting packets that meet certain criteria at the moment. Can you add a line to the FORWARD chain that accepts packets in on any interface and out on tun+? This will count any packets that are forwaraded from the local LAN back to the VPN. 

I wonder if your problem is that the hosts on the LAN don't know of a route back to 10.8.0.0, Your first post says that your VPN server knows the route(of course), but how about the PCs that your clients are trying to talk to? They will either have to be configured individually with a route to 10.8.0.0 via your VPN server, or you will need to add that route to your router (which is their default gateway).

---

### Post by nownto on 2007-10-23
can you give me a example of what your talking about. sorry but the 2nd paragraph lost me :(. thanks for the help.:)

---

### Post by nownto on 2007-10-23
it may be becuase i have the network at home that the vpn server is on as a 192.168.1.0/24 and this is same configuration as most of the networks im trying to vpn from. would this be the cause of the problem?

---

### Post by steve.horsley on 2007-10-24
It's the openvpn server that needs IP forwarding enabled. But that's not enough. The clients to the openvpn server appear to be connected to a separate network that joins all the openvpn clients to the server, and in our case this looks like network 10.8.0.*. When the client tries to talk to servers up on the server LAN (on 192.168.1.*), packets will come from addresses on 10.8.0.*. To be able to repy, the servers must have a route back to network 10.8.0. They could have a static route configured in them telling them that packets to 10.8.0 shoudl be forwarded to the VPN server 192.168.1.?. Alternatively, the router that is the servers default gateway (192,168.1.1) needs to know that any packets for the VPN need to be sent to the VPN server. In this second alternative, the servers will send their replies to the router, and the router will forward them to the VPN server.

---

