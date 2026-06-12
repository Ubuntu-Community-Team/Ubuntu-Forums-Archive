---
title: "Docker, UFW, and OpenVPN - only allow certain ports from VPN network and block public"
date: 2017-05-17
forum: Security
---

### Post by diskmaster23 on 2017-05-17
I have UFW up and running in default incoming drop all with the proper ports like SSH, Mosh, HTTP, and etc ope. It's blocking things well. I have OpenVPN up and running. I have access to the Docker containers, internet, and such.

Here is my problem:
I have portainer.io (and a bunch of other services) running on Docker on port 9001. Now, UFW doesn't have port 9001 open because I don't want it exposed to the public, but I want it exposed to VPN clients, like myself. So, if I connect to my OpenVPN while UFW is enabled, I try to goto publicIP:9001, it timeouts.
If I take UFW down while connected to OpenVPN, I can actually goto dockerIp:9001.

For the life of me, I cannot figure out how to properly configure UFW to allow port 9001 from my VPN network.

If I 'UFW allow 9001', I get access to it, but so does everyone else. That's not what I want.

What do I do?

---

### Post by TheFu on 2017-05-17
You can have ufw allow access only from the LAN and/or any IP or any specific subnet. You need to know the source IPs.  There are many examples of using ufw in this way.  [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) - look in the 'Allow Access' section.

Sometimes it is very useful to draw a picture and label all the IPs and subnets.  That usually helps me to get clarity for what is really needed.

And turn up the logging, so you can see where any blocking/failures are happening.

---

