---
title: "UFW VPS Help"
date: 2016-05-12
forum: Security
---

### Post by ray46 on 2016-05-12
Im trying to learn port forwarding with Ubuntu and OpenVPN


This is what Im hoping to accomplish. 


[[IMG]http://i170.photobucket.com/albums/u251/ExplicitConcepts/example_1.jpg[/IMG]]("http://s170.photobucket.com/user/ExplicitConcepts/media/example_1.jpg.html")


I want to run services on remote servers but have that access only through the VPSs public IP addresses. 
Example. Webserver 


**Internet >>> VPS >>> Openvpn >>> LAN >>> Web Server:80 **

Public IP >>> 10.0.10.0/24 >>> 172.16.50.0/24 >>> 172.16.50.2:80
                      VPN Net             Server Side LAN       Webserver port 80


 VPS tun0 10.0.10.2/24  ======Tunnel==== 10.0.10.1/24 pfSense VPN server IP


**The server is running on the pfSense box. The client in this scenario is the VPS.**


**Issue 1  Full connectivity**


*    Using the default settings of the VPN. I haven't created any additional routes or anything. 
*    Can ping all the 172.16.50.0 addresses from the VPS over the VPN to the LAN. 


* **Can't ping the 10.0.10.2 address of the tun0 interface of the VPS from a server on the Server side LAN. 172.16.50.2**


*    Can ping the server side VPN address 10.0.10.1 from 172.16.50.2 


*    Firewall rules are set to allow traffic from the 172. network to the 10. network on pfSense. 
 
I need to add a route somewhere to let the LAN computers know how to reach the VPS tun0 interface. 


Where do I need to add this route? on the client or the server?  is this to be done in Client Specific Overrides? This is the part I&#8217;m confused about. 


Also in order to send services traffic from the server over the VPN to the public IP would the gateway of the server need to be pointed to the VPN? Or can it still just use the local 172. subnets gateway? 


**Issue 2  Routing/NAT/Port forwarding.**


The VPS has virtual interfaces. Not the standard eth0. I&#8217;ve been using UFW to configure the firewall. I have all the in and out rules applied for the ports I want to access from the public IP. 


DEFAULT_FORWARD_POLICY="ACCEPT"


net.ipv4.ip_forward=1


/etc/ufw/before.rules


First, since we trust OpenVPN completely, I would accept all traffic to/from my OpenVPN. I added this lines at the beginning of the filter section .
> -A ufw-before-input -i tun+ -j ACCEPT
-A ufw-before-output -i tun+ -j ACCEPT
Additionally, I must forward traffic to/from my OpenVPN. These lines was also added after the above lines.
> -A ufw-before-forward -s 10.0.10.0/24 -j ACCEPT
-A ufw-before-forward -d 10.0.10.0/24 -j ACCEPT
Here is my before.rules file. Im not sure what Im getting wrong here. 


```

#
# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#
 
# NAT table rules
*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
 
# Port Forwarding
-A PREROUTING -i PUBLIC IP -p tcp --dport 80 -j DNAT --to-destination 172.16.50.2
 
# Forward traffic through Public IP to OpenVPN
-A POSTROUTING -s PUBLIC IP -o 10.0.10.0/24 -j MASQUERADE
 
# don't delete the 'COMMIT' line or these nat table rules won't
# be processed
COMMIT
 
# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines
 
# allow on tun0
-A ufw-before-input -i tun+ -j ACCEPT
-A ufw-before-output -i tun+ -j ACCEPT
-A ufw-before-forward -s 10.0.10.0/24 -j ACCEPT
-A ufw-before-forward -d 10.0.10.0/24 -j ACCEPT

```


Thanks for any help I could get on this. Ill dance at your wedding!  ;D

---

### Post by ray46 on 2016-05-13
I drew a diagram out so you can get the big picture.

---

