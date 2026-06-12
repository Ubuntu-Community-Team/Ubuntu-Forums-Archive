---
title: "No Public IP Address"
date: 2013-09-15
forum: Server Platforms
---

### Post by qwertimis on 2013-09-15
Hi All,
I am currently running a home server which has Desktop Ubuntu 12.04 on it (I prefer the option of the GUI).

When I try to find the public IP address so that I can access it from elsewhere using ipconfig or the various other commands it just shows its local address (10.0.0.xx).

It is able to access the internet.

I initially did go on an installation spree when I first got it so it may be something conflicting there. Besides that, could anyone suggest what the problem is?

Thanks

---

### Post by sanderj on 2013-09-15
What is your question?

---

### Post by qwertimis on 2013-09-15
Well basically: Why don't I have a public IP and how can I access my server over the internet?

---

### Post by Bucky Ball on 2013-09-15
*Thread moved to **Server Platforms**.*

Slightly off topic, but you do have the option of installing the server edition and installing a lightweight desktop environment (not GUI really). Better. You don't need to install a full blown Ubuntu flavour for a desktop environment and if you just want to run it as a server not the best option.

---

### Post by lisati on 2013-09-15
If your machine is able to access the internet, then it has a public IP address. From a browser, you can find out the public IP address by visiting [http://whatismyipaddress.com](http://whatismyipaddress.com)

If you want public and/or external access to your server, you'll need to set up port forwarding with your router; the specifics vary from router to router. You'll want to give some thought to security, and take care to make sure you only open up ports that are needed.

---

### Post by sanderj on 2013-09-15
> **qwertimis said:**
> Well basically: Why don't I have a public IP and how can I access my server over the internet?

Probably because you're behind a NAT-device (a router). Easy to check: "mtr -nrc2 8.8.8.8": see the first two or three hops: probably first a 10.x.y.z (or 192.168) address, then a public IP address

Access your server from Internet: set up port forwarding in your NAT device. See [http://portforward.com/](http://portforward.com/)

---

### Post by qwertimis on 2013-09-15
> **Bucky Ball said:**
> *Thread moved to **Server Platforms**.*

Slightly off topic, but you do have the option of installing the server edition and installing a lightweight desktop environment (not GUI really). Better. You don't need to install a full blown Ubuntu flavour for a desktop environment and if you just want to run it as a server not the best option.
Sorry for posting in the wrong spot.
I hadn't actually thought of that - I'm not used to this whole being able to install GUI's etc, thanks.

> **lisati said:**
> If your machine is able to access the internet, then it has a public IP address. From a browser, you can find out the public IP address by visiting [http://whatismyipaddress.com](http://whatismyipaddress.com)

If you want public and/or external access to your server, you'll need to set up port forwarding with your router; the specifics vary from router to router. You'll want to give some thought to security, and take care to make sure you only open up ports that are needed.
This IP address is the one for my router though.

> **sanderj said:**
> Probably because you're behind a NAT-device (a router). Easy to check: "mtr -nrc2 8.8.8.8": see the first two or three hops: probably first a 10.x.y.z (or 192.168) address, then a public IP address

Access your server from Internet: set up port forwarding in your NAT device. See [http://portforward.com/](http://portforward.com/)
I did that and got 1 local then 9 public IPs. The first one does appear to be for my server however I have enabled port forwarding and it's still not allowing me access (getting "connection refused")

---

### Post by sanderj on 2013-09-15
"connection refused": from Internet, or from your LAN?

Anyway: you give too little details to help you. Now it is guessing for me.

Type of NAT-device, screendump of your port forwarding settings, proof that you can access your server from your LAN, and possibly public address + port

---

### Post by qwertimis on 2013-09-15
I'm attempting to ssh into it from my mac's Terminal by "ssh _user_@_ip_" and the message I get is "connection refused".

I'm sorry if I'm not giving enough details - I'm unsure of what details I need to actually give :S

It's a Telstra modem, I can get a screenshot in a second and I can access the server by using the DCHP address over the LAN.

---

### Post by The Cog on 2013-09-15
If your server only has an IP address of 10.something, then your router is doing Network Address Translation (NAT) as it passes your connections out to the internet. 

Now the problem for the router is that although it can NAT outgoing connections by converting the address of the internal PC to its own address, if it gets a connection request coming in from the internet, it doesn't know which internal PC to pass the connection on to. You have to configure the router and explicitly tell it that you want incoming connection for port 22 (SSH servers live on port 22) to be forwarded to your home server, 10.whatever. This is known as port forwarding. Also, for this to work, your server needs to have  fixed IP address so you may need to configure your DHCP server to always allocate the same address to your server.

I think you need to search for how to configure port forwarding on a telstra modem.

---

### Post by scbingham on 2013-09-15
I guess you're trying to test that your server is accessible from the outside world?

I test mine by tethering my phone to my laptop. Then use the phone's data network to access my server via my public ip. Make sure your phone isn't connected to your router's wifi, or it will try to use that instead & fail.

Maybe there is a way to do this via an external server but I don't know how.

---

### Post by qwertimis on 2013-09-15
Yeah, I had figured out most of that. I have been looking into doing port forwarding on my modem and I've followed the instructions but it still isn't working. At this stage I think it's predominantly a problem with the modem, I will probably install Ubuntu server instead because I have a couple of other problems that I think I caused by haphazardly installing stuff that I thought I needed initially.

Thanks for the help - I may be back though :D

---

### Post by The Cog on 2013-09-15
I would advise against Ubuntu server for now. Server is basically Ubuntu Desktop but without the GUI interface (just a white text on black background command console). I would think that you will want the GUI for a while, until you are comfortable with the command line.

---

### Post by qwertimis on 2013-09-15
To be honest, for some reason my GUI stopped working about a month in so I've been using command line through SSH only.

What I'm going to do is maybe have a lightweight GUI that I'll turn on when absolutely necessary.

---

### Post by trundlenut on 2013-09-15
Having a look through the log files should help shed some light on what's happening.  I think auth.log will be the one you want to look at.  Try connecting from outside your network and note down the time then go and look at the log file - everything will be time stamped.

Have you only forwarded port 22?  - or whatever port you chose for SSH?  Actually if you chose a port other than 22 then you need to specify the port number when you try and connect or it won't work.  If you have used port 22 expect to get regularly hammered with log on attempts from people in China.

---

