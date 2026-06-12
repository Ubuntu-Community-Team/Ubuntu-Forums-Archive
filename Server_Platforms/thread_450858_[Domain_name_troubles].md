---
title: "[Domain name troubles]"
date: 2007-05-21
forum: Server Platforms
---

### Post by killerdragon on 2007-05-21
Here is my situation:

I have a ubuntu server setup as a DMZ host on my router. I have several domain (and sub domains) with A records with my external IP address. Everyone outside my network can access my server no problem using the domain names. However, the problem comes in when I try to access them in the internal network.

I know its not something with my network configuration, because I have a separate windows XP pro machine with RDP and I am able to successfully connect to that using any of the domain names.

When I try to access the domain on the local network I get:
"The connection has timed out"
from firefox.
However I will goto a machine on a different network/ISP and I can access my server just fine (this is affecting everything on the server SSH/HTTPD/ect...)

What is going on, and how can I fix this?

---

### Post by SishGupta on 2007-05-21
I understand you question, but do not know the answer.

I would recommend however that you do NOT use DMZ and forward ports instead. Running in DMZ is potentially dangerous and using NAT instead may end up solving your problem.

If you are in a situation where you feel that you may want to open a port on the fly, have ssh forwarded to the server, ssh to the server with dynamic forwarding (socks emulation) and you should be able to access the internal router from any external computer.

you can use:
ssh -X -D 8080 yourdomain.com

and then in your browser use yourdomain.com:8080 as a proxy then you can access sites on the intranet (your routers config) or surf the internet with your server as a proxy (useful for getting past corporate web filters)

---

### Post by killerdragon on 2007-05-21
> **SishGupta said:**
> I understand you question, but do not know the answer.

I would recommend however that you do NOT use DMZ and forward ports instead. Running in DMZ is potentially dangerous and using NAT instead may end up solving your problem.

If you are in a situation where you feel that you may want to open a port on the fly, have ssh forwarded to the server, ssh to the server with dynamic forwarding (socks emulation) and you should be able to access the internal router from any external computer.

you can use:
ssh -X -D 8080 yourdomain.com

and then in your browser use yourdomain.com:8080 as a proxy then you can access sites on the intranet (your routers config) or surf the internet with your server as a proxy (useful for getting past corporate web filters)


This is a dedicated server and I know EXACTLY what is running on it.
DMZ is only dangerous if the person who is using it, I also run a hosting company. I can't simply tell my users they have to use SSH to use FTP.

I monitor the server very closely, I even have deny hosts (great program!) running.

I also use that at work A LOT :P.
I even use that to access my MySQL server and such from other locations.

I think to discuss how dangerous DMZ is, is for another thread.

---

### Post by Mr. C. on 2007-05-22
The problem is that your router/firewall does not support, or is not configured, to allow NAT loopback. In such a case, you cannot use your WAN IP address from the LAN to access your servers.  You must use your LAN IPs.

To allow the same hostnames, you can setup a split DNS, where internal names map to LAN addresses, and your ISPs or registrars DNS servers point to your WAN addresses.

MrC

---

### Post by killerdragon on 2007-05-22
> **Mr. C. said:**
> The problem is that your router/firewall does not support, or is not configured, to allow NAT loopback. In such a case, you cannot use your WAN IP address from the LAN to access your servers.  You must use your LAN IPs.

To allow the same hostnames, you can setup a split DNS, where internal names map to LAN addresses, and your ISPs or registrars DNS servers point to your WAN addresses.

MrC

Yes it does support NAT loopback, because I can use my domain name to connect via RDP to my windows machine (like I put in the post...)
Hell I can even access the webserver that I'm running on my windows machine using the domain name/IP address.
Its something with ubuntu/linux. I don't have a firewall anywhere on my network, so that can't be the problem....
I've tried adding entries to my /etc/hosts file with no luck....

---

### Post by MJN on 2007-05-22
Is the Windows machine also in the DMZ? I'm just wondering if the NAT loopback is perhaps not supported inside the DMZ, but only for the LAN. I can't see why this should be the case but in the absence of any particular detail...
 
Speaking of which, can you elaborate on your setup? What entries have you tried in /etc/hosts?
 
Mathew

---

### Post by killerdragon on 2007-05-22
> **MJN said:**
> Is the Windows machine also in the DMZ? I'm just wondering if the NAT loopback is perhaps not supported inside the DMZ, but only for the LAN. I can't see why this should be the case but in the absence of any particular detail...
 
Speaking of which, can you elaborate on your setup? What entries have you tried in /etc/hosts?
 
Mathew

Not I have a port forward for the windows machine.

I've tried:

my ip address domain [www.domain](www.domain)
127.0.0.1 domain [www.domain](www.domain)
192.168.128.5 domain [www.domain](www.domain)

Nothing worked.

---

### Post by MJN on 2007-05-22
So what's the output when, for example, you have the last line entered into /etc/hosts and you do **ping [www.domain](www.domain)**?

Mathew

---

### Post by killerdragon on 2007-05-22
> **MJN said:**
> So what's the output when, for example, you have the last line entered into /etc/hosts and you do **ping [www.domain](www.domain)**?

Mathew

Using either of the 2 (127 line and the 192 line I was able to visit the site locally, but not anywhere else on the network).

---

### Post by MJN on 2007-05-22
Anything in /etc/hosts is only applicable to the machine the file is on, hence that's to be expected.

As first advised it sounds like that whilst your router can support NAT loopback for LAN services it cannot do so for anything in your DMZ. Prove it either way by taking it out of the DMZ, forwarding port 80 to it, and attempting to connecting from the LAN using the WAN IP address.

Mathew

---

