---
title: "Next cloud AIO on Ubuntu Server: question about static ip"
date: 2023-09-06
forum: Server Platforms
---

### Post by kelltech on 2023-09-06
Very new to a self hosting attempt, running into some roadblocks trying to setup Next cloud AIO ([https://github.com/nextcloud/all-in-one](https://github.com/nextcloud/all-in-one)). I hope my questions will make sense and that I'm asking in the right place.

In my router settings, I have forwarded ports 80, 443, and 3478. I can reach a Nextcloud AIO setup login page using the internal private IP. After I began this process, I set up a static IP address through my ISP. The host I use for other things is also my domain registrar and is helping with the nameservers and says,

"Before we proceed you need to ensure you have Nextcloud (or rather your  server for it) configured to use the static IP and that it's accessible from the public IP."

How can I ensure that my AIO is configured to use the static IP? Is that simply configuring Netplan?

---

### Post by TheFu on 2023-09-07
> **kelltech said:**
>  
How can I ensure that my AIO is configured to use the static IP? Is that simply configuring Netplan?

No. This has nothing to do with the Ubuntu networking.  It all happens upstream.  The ISP must allow the desired ports through. Most residential ISPs block well-know server ports like 80, 22, 443, 25, 587, 465, 8080, 8000, 993, 143, and all the other ports below 1024.  

Then you need to setup port forwarding inside the router to the static IP on the LAN.  Lots of how-tos for this exist, but they are router specific, since each model is a tiny bit different, though they are all the same ... from the big picture.  Don't be tempted to use the DMZ setting. Just don't.

I'd strongly encourage you NOT to allow access into your home network over those ports to the whole internet.  Rather setup a wireguard VPN server on a high port and host that yourself, then you can connect to your Public static IP:port ---> LAN_IP:port where the wireguard server runs and have full, secure, access to everything on your LAN that has a static IP.  There are lots of how-tos for accomplishing this.  Next to nobody will even attempt to crack a wireguard VPN. It just isn't done.  OTOH, HTTP/HTTPS and the other ports you've listed will be attempted.

Or you could setup ssh remote access on a high-port and use a SOCKS5 proxy via ssh to access your LAN web services.  I've posted how to do that in these forums a few times.  Obviously, you'll need to allow sshd to be access from the outside world, and you'd want to secure that access using ssh-keys (never passwords!!!!) and block brute force attacks using denyhosts or fail2ban.

To verify that any port is open externally, you can use any internet scanning services you like or just go visit a coffee shop nearby and try the connection using their wifi.

A Wireguard server is trivial to setup compared to openvpn servers.  Using a VPN server at home makes connections from smartphones/tablets much easier than using an ssh-proxy.  I don't trust my home wifi, so it sits outside my secured networks on a different subnet and only when my IoT devices (android tablets/phones) use the VPN client, can they access the secured parts of my network. At a prior job, I learned too many reasons why we should never trust wifi or bt or any RF connectivity, but most of the world doesn't seem to care.  Sigh.  Convenience outweighs security, again.

I see that Nextcloud-AIO is a docker deployment. Ewww. Not my favorite idea.  Docker networking is, er, different. It requires forwarding ports from the docker host into the docker container in addition to all the other stuff above.

I wouldn't leave port 80 open to the world.  If you use Let's Encrypt for your TLS certs, you'll likely want to open port 80 when getting a new cert and when upgrading existing certs, but besides those 30 seconds, every 3 months, don't leave port 80 open.

Really, for $5 month, it would be better to get a VPS and host your nextcloud instance there, if you want most access to be available when you are away from home. Lots of reasons to go this direction.

---

