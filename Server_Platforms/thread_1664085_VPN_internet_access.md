---
title: "VPN internet access"
date: 2011-01-10
forum: Server Platforms
---

### Post by pspkicks316 on 2011-01-10
I've got VPN setup and working on my server. I can VPN into the server and access my local network from anywhere. It uses pptpd for it. My problem is that I can't access the internet once I'm connected to my VPN. Is it possible to allow internet access through VPN?
 
I mainly would just like to be able to connect, access my local network, and still browse the internet. Is there anything specific I need to change?

---

### Post by Dr_Deadmeat on 2011-01-11
You might try to edit the file /etc/sysctl.conf and uncomment the line which says net.ipv4.ip_forward=1 and then run sysctl -p

That will enable ip forwarding on the computer, and that was what I needed to make it work on my server.

---

### Post by pspkicks316 on 2011-01-12
I already have it uncommented. Any other ideas?

---

### Post by bsntech on 2011-01-12
Check your routes by doing a 'route' command and see where the default route is.  You may have to configure a script that once you login to VPN, it sets a route for that network to use the ppp connection and the default route through your regular connection.

---

### Post by pspkicks316 on 2011-01-12
I'm not quite sure what you mean, or how I would do this. 

My server's IP is 192.168.0.192

On the server, route gives me
192.168.0.0 * 255.255.255.0 U 0 0 0 eth0
That's looks fine, I guess.

With my Android phone using VPN I get:
[IMG]http://i.imgur.com/G6DZ0.png[/IMG]

---

### Post by ephmanjmm on 2011-01-12
I am not using pptp but rather the Cisco compatible vpn client so YMMV.  On the IPv4 Settings tab there is a Routes button.  From there, there is a check box to use this connection only for resources on this network.  That solved the problem for me.

---

### Post by pspkicks316 on 2011-01-12
> **ephmanjmm said:**
> I am not using pptp but rather the Cisco compatible vpn client so YMMV.  On the IPv4 Settings tab there is a Routes button.  From there, there is a check box to use this connection only for resources on this network.  That solved the problem for me.

That's a client, this is a server. Thanks for the input though!

---

