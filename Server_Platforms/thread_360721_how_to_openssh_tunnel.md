---
title: "how to openssh tunnel"
date: 2007-02-13
forum: Server Platforms
---

### Post by Foxtrot-1 on 2007-02-13
How do you setup and configure an openssh tunnel, like openvpn tunnel?
I am not an expert in linux, so please explaine me it in a easy way:P

And if someone have a good and safety openssh config file to post in this thread?

Thanks:)

---

### Post by jtc on 2007-02-13
An OpenSSH- and an OpenVPN-tunnel does somewhat different things.

It might be easier to know where to start the explaining if you tell us what you want to accomplish.

---

### Post by gaten on 2007-02-14
As the above poster stated, we'll need a bit more information to help you. BUT I have just finished setting up my VNC over SSH connection, so I figured I'd share and hopefully it will help you out.

The idea behind the config is this: You want to be able to view your desktop remotly from any computer in the world (OK, not ANY computer, but most) all the while using a secure connection. I'm using the following for this setup:

On the server side (ubuntu dapper):
-OpenSSH with public-key authentication (password auth is bad!)
-Ubuntu VNC server

On the client side (windows b/c most machines out there are windows):
-PortaPUTTY ([http://socialistsushi.com/portaputty](http://socialistsushi.com/portaputty))
-XTightVNC Client stand alone .exe ([http://prdownloads.sourceforge.net/vnc-tight/tightvnc-1.2.9_x86_viewer.zip?download](http://prdownloads.sourceforge.net/vnc-tight/tightvnc-1.2.9_x86_viewer.zip?download))

This basic idea is this, we will run the VNC server on our Linux machine, but using our firewall (a Linksys WRT54G router running DD-WRT in my case, but it could easily be iptables on your server machine) we will BLOCK outside access to port 5900 (the default VNC port in Ubuntu). I'll explain why in a bit.

We will then run OpenSSH server on our linux machine on a non standard port (ie NOT 22). Pick something arbitrary, like 56548 or something. Alot of schools/corporations block lower outgoing ports (like 22), so setting your port high may allow you to bypass some firewalls. Also, it increases security. This port WILL be accessible from the outside world. 

You will SSH to your server, and using port forwarding with the putty client create a secure tunnel to view your VNC connection over. 

This article explains better than I can: [http://johnny.chadda.se/2006/10/24/access-your-linux-computer-graphically-and-securely-using-ssh-and-vnc/](http://johnny.chadda.se/2006/10/24/access-your-linux-computer-graphically-and-securely-using-ssh-and-vnc/)

But I've give you the basic idea. Let me know if you can't figure something out (at least TRY to do it).

---

### Post by Foxtrot-1 on 2007-02-15
Thank you both for the answeres, I havn't tried to VNC to server, because it is not quite what I'm locking for.

if someone would tell med the differece between a VPN tunnel and a ssh tunnel it would be nice.

Im actually locking for a guide for openssh tunnel so I can connect from a ubuntu client to ubuntu server. 

But I'm also asking for an OpenVPN server config file if someone have:)

---

### Post by jtc on 2007-02-15
> **Foxtrot-1 said:**
> if someone would tell med the differece between a VPN tunnel and a ssh tunnel it would be nice.
Basically a VPN-tunnel covers an entire network-connection while a SSH-tunnel merely handles a specific port/service.

---

