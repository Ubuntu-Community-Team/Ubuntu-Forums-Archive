---
title: "URGENT - VPN Server Does not assign correct SubnetMask/Default gateway"
date: 2012-04-01
forum: Server Platforms
---

### Post by mhariri on 2012-04-01
Hi
 
I am new to ubuntu. I used the link [here ]("http://home.inestdia.com/localserver/setupapptpvpnserverubuntuathome")to set up the ubuntu VPN server. The clients can connect and they get an IP address but the default Gateway show up as 255.255.255.255 and default gateway as 0.0.0.0. So after the clients connect, they are not able to access the internet. I want to make sure that all traffic is directed through the VPN connection. 
 
Any ideas is greatly appreciated. 
 
 
 
 
Here is my configuration:
 
server is Ubuntu 11. eth0 is configured as
 
IP Address: 66.22.11.11
Subnet Mask: 255.255.255.248
Default Gateway:66.22.11.8
DNS1: 123.23.123.122
DNS1: 123.23.123.123
 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
66.22.11.8     *               255.255.255.248 U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         ool-60381609.st 0.0.0.0         UG    0      0        0 eth0
 
 
VPN Files
/etc/pptpd.conf
localip 66.22.11.11
remoteip 192.168.2.2-235
 
/etc/ppp/options
 ms-dns 123.23.123.122
 ms-dns 123.23.123.123

---

### Post by elico on 2012-04-03
two things:
the localip shouldn't be an ip such 66.22.11.11 that is a vaild internet ipv4 address.
the 255.255.255.255 is how pptp vpn works.
if you want another option you can try openvpn but most of your clients wont really have the head for that.
you need to make some iptables setup after you will change the localip.
the localip is an ip that will be used only for the tunnel between the client and the server in the vpn with no relation to the actual external ip address of the server.
you should also masquerade your users to the internet when they are using the vpn.

give us the output of your iptables

---

### Post by mhariri on 2012-04-03
Thank you for the reply. the 66.22.11.11 is what I used for this post instead of the actual IP address which is a real IP address. I have changed the local IP to 

VPN Files
/etc/pptpd.conf
localip 192.168.2.2
remoteip 192.168.2.3-235

and everything appears to be working!! 

Thank you

---

