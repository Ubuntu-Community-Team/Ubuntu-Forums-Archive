---
title: "Problems with routing the VPN network"
date: 2012-08-20
forum: Server Platforms
---

### Post by CappyT on 2012-08-20
Hi everyone!
This is my first post so I hope is in the right section...

First of all, sorry for my possible mistakes in this post (i'm italian), but the italian community of ubuntu dont'know how to help me with this problem...

Ok, lets start explain my problem.

I have a small server (pentium 4) that I use to filter HTTP traffic through squid and dansguardian. This server also provide me the IP addresses (DHCP).

On this machine I have two interfaces: eth0 (WAN - Internet) and eth1 (LAN).
I used iptables (quite simple) to route from an interface to another.

Now I want to add a VPN (simple pptp, I don't know to figure out and configure OpenVPN and I don't want to get mad doing it) who is able to surf my shared docs and see the pc on LAN (eth1) Network.

When i try to connect, I can't see the client connected even from the server! (i tryed to ping it with -i ppp0 option, but i seems dead...

Now, I can post iptables/interfaces/pptp configuration if is needed...

I hope someone can help me...
To everyone will reply, Thank you... And again, sorry for my really bad english...

---

### Post by CappyT on 2012-08-21
up... is really not possible?

---

### Post by trondhuso on 2012-08-22
You are better off buying a hardware firewall with VPN on it.

Or you have to create a linux firewall and then do the vpn stuff on it. this is just from the top of my head. I have not tried to do what you are trying to achieve :)

Trond

---

### Post by poolet on 2012-08-22
> **CappyT said:**
> Hi everyone!
I have a small server (pentium 4) that I use to filter HTTP traffic through squid and dansguardian. This server also provide me the IP addresses (DHCP).

On this machine I have two interfaces: eth0 (WAN - Internet) and eth1 (LAN).
I used iptables (quite simple) to route from an interface to another.

Now I want to add a VPN (simple pptp, I don't know to figure out and configure OpenVPN and I don't want to get mad doing it) who is able to surf my shared docs and see the pc on LAN (eth1) Network.

When i try to connect, I can't see the client connected even from the server! (i tryed to ping it with -i ppp0 option, but i seems dead...

Now, I can post iptables/interfaces/pptp configuration if is needed...


please share with us your iptables.. Also keep in mind that with openVPN you must installed RPM package and configure config file correct, also since your using DHCP a good idea is check the following article "[here]("http://openvpn.net/index.php/open-source/documentation/howto.html#dhcp")".... At the end you may look up more closer the http traffic filter!!!

---

### Post by SeijiSensei on 2012-08-22
Is TCP port 1723 open all the way to the server?

If so, and you log in with a PPTP client, what do you see in the logs?  I suspect it will log to /var/log/syslog, but if you can't find the entries there, try locating the file with:

```

cd /var/log
sudo grep -i pptp *

```

I haven't set up a pptpd server in a very long time (who would want to use such an [insecure]("http://www.schneier.com/pptp-faq.html") thing?), but I believe it has a debug configuration setting.  Set it to the most verbose level possible until you get things working properly.

Setting up a shared-key OpenVPN implementation is really pretty [simple]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") and much, much more secure.

---

