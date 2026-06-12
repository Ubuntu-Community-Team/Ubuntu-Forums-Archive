---
title: "I know it's simple but my brain no worky"
date: 2016-02-04
forum: Server Platforms
---

### Post by n-mike-3 on 2016-02-04
Client-1/10.8.0.6 DG 10.8.0.5 via OPENVPN connected to Router-1/192.168.1.1 then I SSH to Server-1/192.168.1.12 DG 192.168.1.1 Everything work great.  But then I try to establish another OPENVPN connection from the Server-1 to a VPN provider, I loose connection from Client-1/10.8.0.6 as soon as it makes connection and can no longer ping Server-1 from Client-1.  

I tried ssh to another box on the 192.168 network and Server-1 responds just dandy.  

I'm thinking I need to add a static persistent route on Server-1 back to the 10.8.0.0 network?  How?  Doing this over cli.

Thankyou.
Putz

---

### Post by matt_symes on 2016-02-04
Thread moved to **Server Platforms**.

This may be a better sub forum for your query.

---

### Post by nerdtron on 2016-02-04
You can add temporary static routes (lost upon reboot) using the "route add" command. You can set the permanent routes by adding entries to your network interfaces file.
The syntax is explained here: [http://askubuntu.com/questions/168033/how-to-set-static-routes-in-ubuntu-server](http://askubuntu.com/questions/168033/how-to-set-static-routes-in-ubuntu-server)

---

### Post by n-mike-3 on 2016-02-05
Static routes aren't working.  As soon as open vpn is running on the other machine I loose connection.

---

### Post by volkswagner on 2016-02-06
Can you post log info? I think using Openvpn server configure "topology netmask " is more robust, yet not the default.

---

### Post by darkod on 2016-02-06
A static route from Server-1 192.168.1.12 to 10.8.0.0/24 wouldn't help you anyway (I think). You also have to be careful with private subnets used in all three networks (where client-1 is, where server-1 is, and the network where server-1 is connecting to). The general rule for VPN is for the private subnets on all locations to be different.

So if your server-1 subnet is 192.168.1.0/24 it could be an issue if the client-1 subnet is identical, or the subnet where the second OpenVPN server is (the one you are connecting server-1 to).

Going back to the static route, the usual routes added to openvpn are from one private subnet to the other, not to the VPN subnet (10.8.0.0/24). You basically tell it to reach the other subnet using the other end of the vpn tunnel, like:
From 192.168.1.0 send all traffic destined to 10.0.0.0 over 10.8.0.6

Also, you say the second vpn connection is also openvpn. Can you confirm it is not using the 10.8.0.0/24 vpn subnet also? That would definitely mess things up.

Sit down and draw carefully the subnets used and what you want to connect where. That will take you one step closer... And help us help you too.

---

