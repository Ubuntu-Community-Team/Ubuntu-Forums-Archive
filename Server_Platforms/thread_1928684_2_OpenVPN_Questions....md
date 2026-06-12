---
title: "2 OpenVPN Questions..."
date: 2012-02-20
forum: Server Platforms
---

### Post by d4m1r on 2012-02-20
Hey guys, I just setup OpenVPN on my Ubuntu 11.04 server according to [this guide]("http://tipupdate.com/how-to-install-openvpn-on-ubuntu-vps/") and I am able to connect to it from my PC and it routes all HTTP traffic through out, but I'd like to route ALL traffic through my remote Ubuntu server (PC->Server->Internet)....Is that possible?

Also, what is "lzo compression" and should I leave it enabled or should I disable it?

---

### Post by kevdog on 2012-02-20
I used this tutorial [http://ubuntuforums.org/showthread.php?t=1762152&highlight=openvpn](http://ubuntuforums.org/showthread.php?t=1762152&highlight=openvpn).  It routes all traffic.

---

### Post by d4m1r on 2012-02-20
I already have it setup...just it seems to be routing HTTP traffic only. For example, if I launch a bittorrent client or teamspeak, it uses my regular IP :confused: Now I am reading OpenVPN can't support all network traffic as that requires PPTP or something like that....

Can someone confirm they are using a linux server to run OpenVPN and they are able to route ALL traffic (regardless of the application) through it?

---

### Post by SeijiSensei on 2012-02-21
You can route all the traffic through the tunnel except for the connection between your computer and the remote VPN host.  

To do this, you need to set up a static route that points to the VPN host's public IP address and uses the ISP's default gateway as the gateway to that host.  Then add a default route that points to the IP address assigned to the other end of VPN tunnel.  Now all traffic between your computer and the VPN host is sent over the public Internet, but all other traffic from your computer will be sent over the tunnel.

Here's a start at a bash script to do this for you:
```

#!/bin/bash

ISP_GATEWAY_IP=1.2.3.4
VPN_REMOTE_IP=5.6.7.8
VPN_TUNNEL_IP=10.1.1.1

# route traffic to the remote VPN host via ISP
ip route add $VPN_REMOTE_IP via $ISP_GATEWAY_IP

# restart OpenVPN
/etc/init.d/openvpn restart
    
# delete the standard default route
ip route del default

# create a new default route through the tunnel
ip route add default via $VPN_TUNNEL_IP
    

```

This example assumes your remote VPN host has IP 5.6.7.8, your ISP's gateway is 1.2.3.4, and the remote VPN endpoint (defined by the "ifconfig" statement in openvpn.conf) is 10.1.1.1.

---

### Post by Bachstelze on 2012-02-21
> **d4m1r said:**
> 
Can someone confirm they are using a linux server to run OpenVPN and they are able to route ALL traffic (regardless of the application) through it?

Yes, make sure

```
push "redirect-gateway def1 bypass-dhcp"
```

is uncommented in your server config. The guide you linked doesn't mention it. You will need to do some serious configuration on your server, though. In particular, you will probably have to setup NAT manually via iptables.

---

### Post by d4m1r on 2012-02-21
> **Bachstelze said:**
> Yes, make sure

```
push "redirect-gateway def1 bypass-dhcp"
```is uncommented in your server config. The guide you linked doesn't mention it. You will need to do some serious configuration on your server, though. In particular, you will probably have to setup NAT manually via iptables.

From the guide:

**"Step Ten :** In this step we are going to do necessary  amendments to tunnel all traffic through the OpenVPN server on the VPS.   We need to amend certain files . First issue the following command and edit server.conf file.
 **[COLOR=#000080]vi  [/COLOR][COLOR=#000080]*/etc/openvpn/server.conf*[/COLOR]**
 uncomment the following line
 **push “redirect-gateway def1 bypass-dhcp” ;)**


**[B]Sh**ort of having to configure a custom network connection to my VPN, I am just gonna try another VPN client instead of network-manager-openvpn. I think that may support just HTTP traffic hence my issue....The way I have OpenVPN setup server side means I should be able to route ALL traffic according to most threads..
[/B]

---

### Post by SeijiSensei on 2012-02-21
I just run "sudo /etc/init.d/openvpn start" and have it launch all the tunnels it finds configured in /etc/openvpn.  I never deal with a GUI for this, even on a machine where I'm using the GUI to launch the network connection.  Once I have the connection up, I run the script manually from a Terminal.

---

