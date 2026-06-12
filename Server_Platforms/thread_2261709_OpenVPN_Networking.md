---
title: "OpenVPN Networking"
date: 2015-01-20
forum: Server Platforms
---

### Post by HomeGamer on 2015-01-20
I have, after reading some tutorials and the OpenVPN pages, sucessfuly created an OpenVPN server in my ubuntu 14.04.
I can with any client OS and ip, using a client config file, connect to my server network and "talk" to my other PCs. I created this setup to use my smb server (192.168.1.10).
The clients ip would be in the range 10.8.0.0/24 (given by the ubuntu server) and my main network would be 192.168.1.X
From what I could tell, my clients could "talk" to my main lan but the other way around was not possible.
How can I get the main lan 192.168.1.X to "talk" to 10.8.0.X in my openvpn server?
From what I could read I would need some routing tables, but my router, at least in the webgui, isnt capable of that, if this is the answer can I do the routing tables with ubuntu?

---

### Post by volkswagner on 2015-01-21
Ideally you'd want to accomplish this at the router.

What OS are the clients on your LAN running?

You'd have to manually add the route to each client.

Here's some info on [Windows Route command]("http://www.itgeared.com/articles/1129-using-windows-route-command/")

If you're LAN clients are laptops and travel, you may have issues with the static routes. For roaming machines, you may want to script
the route ADD, then Route Delete actions.

---

### Post by HomeGamer on 2015-01-22
I tried that
route ADD 10.8.0.0 MASK 255.255.255.0 192.168.0.11
but with no sucess, I can ping 192.168.1.X from my client 10.8.0.X but not the other way around
maybe ubuntu needs some configuration in order to this work
If this worked it would solve my problem
Any ideia?

---

### Post by SeijiSensei on 2015-01-22
Normally I would guess that you haven't enable IP forwarding in /etc/sysctl.conf, but the fact that your problem is asymmetric leads me to think it has to do with routing.

What is the default route on the boxes in 192.168.0.0/24?  If you point them at the Linux box rather than the router, your problem might be solved.  You might still need to enable IP forwarding, though.  Edit sysctl.conf and remove the hash mark from "net.ipv4.ip_forward" then reboot.

If you make the Linux box the default gateway, it will know how to talk to 10.8/16 since it has both interfaces.  It will also forward along any unmatched traffic to its default router, which is probably your border router connecting to the Internet.

Try doing this manually on one of the clients to see if it works.  If it does, modify your router's DHCP server so it hands out the address of the Linux box as the clients' default gateway.

---

### Post by HomeGamer on 2015-01-22
> **SeijiSensei said:**
> Normally I would guess that you haven't enable IP forwarding in /etc/sysctl.conf, but the fact that your problem is asymmetric leads me to think it has to do with routing.

What is the default route on the boxes in 192.168.0.0/24?  If you point them at the Linux box rather than the router, your problem might be solved.  You might still need to enable IP forwarding, though.  Edit sysctl.conf and remove the hash mark from "net.ipv4.ip_forward" then reboot.

If you make the Linux box the default gateway, it will know how to talk to 10.8/16 since it has both interfaces.  It will also forward along any unmatched traffic to its default router, which is probably your border router connecting to the Internet.

Try doing this manually on one of the clients to see if it works.  If it does, modify your router's DHCP server so it hands out the address of the Linux box as the clients' default gateway.

Thank you for your response, I did enable IP forwarding on my ubuntu server.
Rigth now I am using as default gateway my router 192.168.1.254
I added a route in my windows machine (route add 10.8.0.0 mask 255.255.255.0 192.168.1.11) (192.168.1.11 is my ubuntu server), but still I cant ping 10.8.0.X from windows but from 10.8.0.X I can ping all 192.168.1.X
What am I missing? The tutorial I followed is this [http://readwrite.com/2014/04/10/raspberry-pi-vpn-tutorial-server-secure-web-browsing](http://readwrite.com/2014/04/10/raspberry-pi-vpn-tutorial-server-secure-web-browsing) maybe it can help shred some ligth into the problem
Now I am thinking I will try and find some router that supports routing tables and connect it to my main router, then connect my windows machine and my server to it and add a route to it to see if I can ping from 192.168.1.X my server subnet 10.8.0.0

---

### Post by darkod on 2015-01-23
Why are you trying to ping 10.8.0.x? If your purpose is lan-to-lan vpn it usually works private range vs the other private range. Forget about the vpn range.
In your case the other range seems to be 192.168.0.x right? In that case you should be making routes to that subnet and try pings between 192.168.0.x and 192.168.1.x.

If you insist using the vpn clients ips I think there was an option for that in server.conf but I can't search for it now.

---

### Post by SeijiSensei on 2015-01-23
> **HomeGamer said:**
> Now I am thinking I will try and find some router that supports routing tables and connect it to my main router, then connect my windows machine and my server to it and add a route to it to see if I can ping from 192.168.1.X my server subnet 10.8.0.0

I took this approach here actually.  I added a route in my border router that forwards traffic for my external VPN network through the VPN node here.

If your router doesn't support static routes, and you want to buy one that does, I recommend buying something that supports dd-wrt and/or Tomato.  These are full-featured router operating systems based on Linux.

Have you tried telling a client to use the Ubuntu box as its default gateway?  That really should be all you need.

---

### Post by HomeGamer on 2015-01-24
> **darkod said:**
> Why are you trying to ping 10.8.0.x? If your  purpose is lan-to-lan vpn it usually works private range vs the other  private range. Forget about the vpn range.
In your case the other range seems to be 192.168.0.x right? In that case  you should be making routes to that subnet and try pings between  192.168.0.x and 192.168.1.x.

If you insist using the vpn clients ips I think there was an option for  that in server.conf but I can't search for it now.

What you are saying is that I should give 192.168.0.X ips for my clients instead of 10.8.0.X?

> **SeijiSensei said:**
> I took this approach here actually.  I added a route in my border router that forwards traffic for my external VPN network through the VPN node here.

If your router doesn't support static routes, and you want to buy one that does, I recommend buying something that supports dd-wrt and/or Tomato.  These are full-featured router operating systems based on Linux.

Have you tried telling a client to use the Ubuntu box as its default gateway?  That really should be all you need.

So do you have a somewhat setup like this?
I tried changing the gateway from my windows box to the ubuntu server still I could not ping my 10.8.0.X
Could it be the netmask? In the tutorial it changes it to 255.255.255.252
Could this not be working because i have my setup on virtual machines? (both the server and the windows box)
Got my hands on a cisco router from a friend and will try the routing

---

### Post by darkod on 2015-01-24
No, do not give 192.168.0.x to clients. There was mentioning of that range in previous posts but it might have been a typo, so I thought you might be connecting two networks by VPN, one with local range 192.168.0.x and the other with 192.168.1.x.

Testing one vpn setup I have, pinging towards the client was not working either. I think this is by design, and not sure if it can be changed (maybe it would need some iptables rules too, not just routing rules).

When you have client-server vpn like you do, the idea is the client to talk to the server and get the service it needs. According to your first post, you are able to do that. So your setup works. Even when you have several different servers, still the clients would talk to the servers, not the other way around.

It seems what you are trying to do is for the server to initiate talking to the client, which is not how client-server relationship works. The client initiates request and gets the server reply, which is working for you. Why would a server want to initiate talking to the client?

I see this first as a concept question, not as a "how do I configure" question.

Going back to another network with 192.168.0.x or any other subnet... Your server LAN is 192.168.1.x. The clients that connect over vpn are outside of that network, otherwise they would be on 192.168.1.x and they can use that for direct communication. So what local IPs do these clients have? They can't have 10.8.0.x as local because that is IP issued to a client by the openvpn, not its local LAN IP. Will all clients be connecting from different locations? Because if they are on same location, they will have local LAN on that location, for example 192.168.0.x, and in that case we are talking about LAN-to-LAN connecting which is done in a different way (with two OpenVPN servers, one on each subnet, connected between themselves and acting as routers between the two subnets).

---

### Post by HomeGamer on 2015-01-26
> **darkod said:**
> No, do not give 192.168.0.x to clients. There was mentioning of that range in previous posts but it might have been a typo, so I thought you might be connecting two networks by VPN, one with local range 192.168.0.x and the other with 192.168.1.x.

Testing one vpn setup I have, pinging towards the client was not working either. I think this is by design, and not sure if it can be changed (maybe it would need some iptables rules too, not just routing rules).

When you have client-server vpn like you do, the idea is the client to talk to the server and get the service it needs. According to your first post, you are able to do that. So your setup works. Even when you have several different servers, still the clients would talk to the servers, not the other way around.

It seems what you are trying to do is for the server to initiate talking to the client, which is not how client-server relationship works. The client initiates request and gets the server reply, which is working for you. Why would a server want to initiate talking to the client?

I see this first as a concept question, not as a "how do I configure" question.

Going back to another network with 192.168.0.x or any other subnet... Your server LAN is 192.168.1.x. The clients that connect over vpn are outside of that network, otherwise they would be on 192.168.1.x and they can use that for direct communication. So what local IPs do these clients have? They can't have 10.8.0.x as local because that is IP issued to a client by the openvpn, not its local LAN IP. Will all clients be connecting from different locations? Because if they are on same location, they will have local LAN on that location, for example 192.168.0.x, and in that case we are talking about LAN-to-LAN connecting which is done in a different way (with two OpenVPN servers, one on each subnet, connected between themselves and acting as routers between the two subnets).

I really dont need, for the moment, to connect two networks by vpn
Adding a routing table to my gateaway (router 192.168.1.254) solved my problem, I can ping from 192.168.1.X to my vpn 10.8.0.X
Thank you for your support and if anyone needs some clarity on what I did just ask

---

