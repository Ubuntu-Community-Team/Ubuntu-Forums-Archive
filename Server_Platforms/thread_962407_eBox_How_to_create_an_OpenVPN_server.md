---
title: "eBox: How to create an OpenVPN server"
date: 2008-10-29
forum: Server Platforms
---

### Post by Boy1dr on 2008-10-29
Hi,

I'm trying to get eBox to work.
Everything installs fine.

But when setting up the OpenVPN module, the eBox-system says the OpenVPN server is running, however it is NOT.

I have followed the instructions as described within the eBox application and the online User Guide.

I've used knmap to scan the eBox's IP-adr and found no OpenVPN-daemon listening (I've set the port to 1194 - standard)

What am I doing wrong ? ... Has anyone got the eBox OpenVPN module up and running ?

Thanx

(I had difficulties in finding any support on eBox with google, so I'm hoping this thread will be the first of many, to help those who wants to use eBox :-)

---

### Post by Boy1dr on 2008-10-29
no worries, solved it.

There were 2 major issues...

1) knmap does not scan port 1194 by default, it is considered to be an "unknown service".  Setting an actual port range (1-1200) will include 1194 in the scan, and reveal whether or not the OpenVPN-service is runnning or not.

2) A setting in the Gnome Network Manager's OpenVPN module is not checked by default and is used in the standard ebox-openvpn configuration ... if this setting is on, then it will work fine with ebox. ( "X.509: Allow server certificate without server extensions" )

bye bye :popcorn:

---

### Post by Boy1dr on 2008-10-30
A new problem came up...

When setting up the server side of the ebox-OpenVPN module, you have to provide at VPN-network ( "VPN network address" and "VPN network netmask" ) 

(That's ok ... I just wonder: Where is the option within ebox to setup a bridged-connection)

After setting up a VPN-network, a section at the bottom of the config-page appears called "*This section manages which networks will be made accessible to connecting clients*". I don't get it .. "accessible" .. if the system is reffering to the networks the VPN-connection will route to, then I guess its not working for me as I can't access any other IP-adr other than the one given to the ebox-server.

Let me describe the setup... (example IP adr.)

**Internal network:** (server side: where the ebox-server is installed)
                  Network    : 192.168.10.0
                  Subnet mask: 255.255.255.0
                  (Gateway: 192.168.10.1)

**VPN Network:**      (The virtual-network within the ebox-server)
                  Network    : 192.168.20.0
                  Subnet mask: 255.255.255.0
[B]
ebox internal IP-adr.:[/B] 192.168.10.50
(ebox VPN-adress...automatically given by the ebox: 192.168.20.1)

a **PC turned on** and accepting pings is on the network with IP: 192.168.10.75

a **firewall** with a public IP adr. is NAT'ing the traffic on port 1194 to the IP 192.168.10.50 on the same port.

**Client network**   : (Another network across the great internet)
                   Network    : 192.168.30.0
                   Subnet mask: 255.255.255.0
                   (Gateway: 192.168.30.1)

**Client-PC** is on the network with IP: 192.168.30.60 ... and the openvpn is installed with a client-setup.


**This is what I want...**
Have the Client-PC connect to the ebox-server, so that it can ping 192.168.10.75 and get a reply

**This is what I've got so far...**
The Client-PC connect to the ebox-server .. but I have no access to 192.168.10.75 ... only 192.168.10.50 (ebox) ... and any other client connecting to the 192.168.20.0/24-network.

What am I missing ? ...any help with be greatly appreciated

/Boy1dr

---

### Post by senor_smile on 2009-08-22
Did you ever figure this out?  I would like to implement ebox in the future, but am having trouble figuring out how to even do a simple openvpn setup.

---

### Post by Boy1dr on 2009-08-26
Yes senor_smile, I did fix it, so that I could use the ebox.

But what I did was not inside the ebox-administration webpage.
I didn't find the routing and IP-masquerading option within ebox, so I had to do it directly inside Ubuntu using a Terminal.

I've created a simple bash-script to activate ip-forwarding (ip_forward) and to be sure, that nothing from the ebox was interfering with it, I reset all IPTABLES-rules.

Here is the script (must be run as root ...use **sudo**)
```

#!/bin/bash

echo 0 > /proc/sys/net/ipv4/ip_forward

echo "Flushing all IPTABLES rules"
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

iptables -t nat -A POSTROUTING -s  192.168.20.0/24 -o eth0 -j MASQUERADE
iptables -t nat -A POSTROUTING -s  192.168.20.0/24 -o eth1 -j MASQUERADE

echo 1 > /proc/sys/net/ipv4/ip_forward

iptables -t nat -L

```

Even though it works, I still can't use bridged connection.  This is still a routed virtual network.  Eventhough I might succeed in writing a bridge-script, to bridge the two netcards together, I would still prefer it, as an option within ebox.

Please feel free to post any new info on the subject

/Boy1dr

---

### Post by imrehg on 2009-09-05
> **Boy1dr said:**
> 
I've created a simple bash-script to activate ip-forwarding (ip_forward) and to be sure, that nothing from the ebox was interfering with it, I reset all IPTABLES-rules.


The ip_forward can be set without scripting, in /etc/sysctl.conf find and uncomment the line:
```
net.ipv4.ip_forward=1
```For bridged connection you can check the manual at [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN) Everything is there except the ip_forwarding. Works pretty well for me even at this moment. ;)

Not sure how it would work from ebox - the thing fails to install...

Hope that helps...

---

