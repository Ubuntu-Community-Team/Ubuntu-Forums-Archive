---
title: "Port Forwarding specific port in VPN Server"
date: 2012-04-22
forum: Server Platforms
---

### Post by gandip on 2012-04-22
Hi:
I am weird situation. 
My office has Client application that listen on port 44899 for incoming connection from a server. This application is installed at all the workstation(windows). 
My manager now is going for business tour couple of month.
He want his client application work on his notebook even when he is aboard from office. 

To fulfill his requirement I installed ubuntu server & setup vpn server in it. Now i want to forward only 44899 port of my vpn server to manager( VPN client ) IP. I only want to forward that port not all.

I heard, to port forward I need to use following command but it will forward whole traffic . But i only want to forward specific port

> net.ipv4.ip_forward=1

Any idea how to forward 44899 port number of my vpn server to vpn client IP.

---

### Post by SeijiSensei on 2012-04-22
Just to make sure I understand, you can now connect from the Windows client to the VPN server.  Can you see the machine where the application is running (presumably it's not the VPN server)?  If so, you can add a couple of iptables rules to the VPN server to block all other ports like this:

```

iptables -A INPUT -p tcp -i tun0 --dport 44899 -j ACCEPT
iptables -A INPUT -i tun0 -j REJECT

```

This assumes that (a) the VPN uses the tun0 interface, and (b) the application uses TCP not UDP.  If the VPN server uses a different interface name, replace "tun0" with the appropriate interface.  If the application uses UDP, replace "-p tcp" with "-p udp".  If it uses both protocols, add another rule identical to the first one with "-p udp" instead.

---

### Post by elico on 2012-04-22
it depends on how your vpn setup is.
what vpn server you have used? pptpd? openvpn?

---

