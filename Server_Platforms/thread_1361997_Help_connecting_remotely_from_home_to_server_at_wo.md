---
title: "Help connecting remotely from home to server at work?"
date: 2009-12-22
forum: Server Platforms
---

### Post by photoman355 on 2009-12-22
Hi

I've just installed a new server at my work and would like to be able to connect to it remotely from home for maintenance and file access.

I can connect to the server remotely using SSH when I am in the same environment eg using my laptop at work to connect with the server in the same room but not when I am offsite.  I think this may be to do with the fact that I'm trying to connect through an external router (work) and my IP settings are incorrect.  

My work router has its own static IP and my server has its own IP.  I'm guessing that I can't connect to it using the normal IP of the server because that is not its location on the internet.  

How would I go about setting up the connection from my laptop/desktop so that I direct the SSH through my work router IP to the server IP?  

Details:

Ubuntu Server 8.04LTS  (Work server)
SSH installed on server.
Laptop running Win XP (Connecting with Putty)
Desktop running Ubuntu 9.04 (At home)

---

### Post by doas777 on 2009-12-22
do you have authorization to do this, and admin access to your works gateway router? if you don't, then either ask, or just give up. no point in going to jail over it.

you need to forward the port on the gateway router at work, so that requests incoming from the outside to a certian port (TCP/22 by default) to your servers ssh port.

then from home you point putty to your works gateway router's Public address. the packet hits the gateway, and gets forwarded to the internal network, and your ssh server.

[http://portforward.com/](http://portforward.com/)

---

### Post by CharlesA on 2009-12-22
You would need to do some port forwarding OR be connected to your work network via VPN. If you are using the VPN, you can just SSH into the server by using it's internet IP address. If you are using port forwarding, you will be using the gateway's IP address.

Be sure to get permissions first, of course, if you aren't in control of those devices.

Personally I think if you want to connect from home and have everything setup, you probably have permission.. but better safe than sorry. :)

Also, be sure to disable password logon (use private/public keys), disallow root access over ssh and lock the firewall down if possible.

---

### Post by photoman355 on 2009-12-23
Thanks for your replies.

I have access permission to everything as I own all the eqipment.  Port 22 is open and I can connect using Putty over SSH within the office.  I can ping my routers static internet IP from home and get a reply.

When I open putty from home and use my work routers IP as the host address and port 22 I get a network connection error.  This makes sense as the connection should only get as far as the router as there is nothing to point the SSH tunnel from the router to an IP on the office network eg my server IP.  

I'll double check the settings when I'm next in but if I was to setup VPN on the server would I not run into the same problems?

---

### Post by CharlesA on 2009-12-23
From my (limited) understanding of VPNs, is that you are basically connected to your work network, and you can access the machine just as easily as if you were at the office.

If that doesn't work, look into seeing if port forwarding is enabled on the router.

---

### Post by doas777 on 2009-12-23
well it sounds like you have opened the port, but not forwarded it. the forwarding will direct all traffic coming in on the forwarded port on the router, to be passed to the internal server on a specific port. otherwise you can use your ssh connection to tunnel another ssh connection but it gets hairy after that.

so can you describe what you did to open/forward tcp/22?

---

### Post by photoman355 on 2009-12-23
Yes I think you could be right, the settings in the router config have been set as open port 22, translate to port 22.  There is also a trigger port option which i've left blank.

The translate port seems to refer to forwarding the open port to another port on my network.  I think the port I have set is correct at port 22 as thats what the server uses for SSH.  Is that correct?

---

### Post by CharlesA on 2009-12-23
> **photoman355 said:**
> Yes I think you could be right, the settings in the router config have been set as open port 22, translate to port 22.  There is also a trigger port option which i've left blank.

The translate port seems to refer to forwarding the open port to another port on my network.  I think the port I have set is correct at port 22 as thats what the server uses for SSH.  Is that correct?

Should be correct. Does the translate port option have a field for the IP address of the machine you want to forward packets to?

---

