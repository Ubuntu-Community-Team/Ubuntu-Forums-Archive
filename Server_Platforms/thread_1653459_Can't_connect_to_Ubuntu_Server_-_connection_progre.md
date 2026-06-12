---
title: "Can't connect to Ubuntu Server - connection progressively degrades to nothing."
date: 2010-12-26
forum: Server Platforms
---

### Post by timothyjoelwright on 2010-12-26
I have two servers hosted remotely in a datacenter. Both are running Ubuntu Server 10.10 with all the latest updates.

Server A is working perfectly and is able to connect o server B via SSH, FTP, and a few other protocols. I am able to connect to server A via SSH, FTP, etc. without any problems from home.

Server B is able to connect to server A as well, and was able to connect to other servers around the internet with good speed and no issues. Server B has ufw operating but I have a high-ordered rule to explicitly allow anything to my static home IP address.

A few weeks ago some services such as FTP started to get quite slow between my home IP and server B. SSH was working fine however, so I assumed it was due to bandwidth limitations of my hosting plan (the server is throttled from 100Mbps to 10Mbps after a certain cap is reached). Five days ago, other services between my home network and server B began to slow down, however it was much slower (30-60kbps) than the bandwidth limit of the cap. Today it has slowed to a crawl. SSH for example will either time out, or connect but have a 30 second+ lag between key strokes.

Traceroute and ping to server B from my home IP are successful and not laggy. Basic TCP analysis suggests a lot of retransmission.

Due to the progressive degeneration of the connection to my home IP only, I'm inclined to think that it's something with the host or my ISP, but I wondered if there's anything I should check or confirm before starting the lengthy process of a support ticket.

**Update: All connections are now degrading.**
After running additional speed tests around the internet from server B, the connection issues are propagating to all connections (not just one or two IP's). I'm going to create a support ticket with the host.
All suggestions are appreciated!

---

### Post by IWantFroyo on 2010-12-26
First check the internet. Other people might be having the same problem, or maybe something's wrong with the fiberoptics cable in your area (cable takes longer to fix than something like cellular internet). Then thoroughly check your system. Tons of things could've gone wrong. I once fiddled with a broken computer for months before I realised that the chipset voltage was too low and causing the computer to crash randomly. Always start at the basics. =\

---

### Post by timothyjoelwright on 2010-12-26
I've confirmed that the internet works just fine from the server to other locations, and my home network has no problems accessing the internet. The issue is connections between my home IP and the server are so slow as to be practically unusable.

To paraphrase the question: Are there any possible causes for extremely sluggish network performance between an ubuntu server and a specific IP address?

(All trace-routs are successful as are pings.)

---

