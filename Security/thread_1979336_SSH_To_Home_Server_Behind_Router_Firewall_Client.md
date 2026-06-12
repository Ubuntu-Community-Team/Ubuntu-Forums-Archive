---
title: "SSH To Home Server Behind Router Firewall Client?"
date: 2012-05-13
forum: Security
---

### Post by mjwoodruff on 2012-05-13
I had been using SSH and dyndns to connect to my home server while away, but due to my ISP, I've had to start using a VPN to download torrents.  Currently, my server is setup to download all torrents/etc.  And I have my router connected to a VPN as a client (through tomato VPN), with only my home server being routed through the VPN.  All other computers on the home network are not sent through the router/VPN.  

With this current configuration, I am not able to SSH to my home server from outside of my home network.  I did setup my router to also act as a VPN server, which I can connect to, then SSH to the server.  But that is two layers of security, and for the purposes, is a little much.  I would just like to simply be able to SSH to server from my laptop or phone and be able to run terminal commands.  

Is there a better way to accomplish this?

Greatly appreciate the help and suggestions!

---

### Post by darkod on 2012-05-13
You said the router is connected to a VPN as a client.

But then you also said you can configure the router as VPN Server.

I might be understanding this wrong, but if the router is conencted as a client, that means a server exists somewhere. Why don't you simply connect your laptop/phone as a client to that same server, that should allow it as if within the same network as the router and the home server. SSH should work.

---

### Post by mjwoodruff on 2012-05-15
I can connect to my server through the VPN and SSH to server that way.  I would like to skip the VPN part.  Is that possible?

---

### Post by markbl on 2012-05-15
Set up sshd on your server (sudo apt-get install openssh-server). Make sure you can log in to that on your local lan, e.g. from a laptop. Then add a port forward from your home router/modem to that server. E.g. forward port 443 on the router to port 22 on your server. Configure dyndns (or equivalent) on your router if you have a dynamic ip address (which is the usual case).

Then when you are out in the internet cloud you can just "ssh -p443 myserver.dyndns.org". The reason I recommend port 443 is that it is far less likely to be blocked outbound from whatever site you are connecting from. E.g. many work places block port 22 outbound connections but it is difficult for any router/firewall to intercept outbound port 443 connections (normally https).

I know this is a short summary, but you can ask uncle google to fill in the details.

---

