---
title: "[ubuntu] Personal PC Server?"
date: 2008-04-28
forum: The Cafe
---

### Post by GCoffee on 2008-04-28
Hello guys,

After many stressful attempts to find a good server to host things on i have decided that I might run my own server..

Here are my details:

I am in a small room with 1 pc in it.
250GB Hard drive, 80GB Ubuntu Partition, 80GB Windows Partiton
512mb RAM, Have enough spare ram to upgrade to 1gb if needed.
Netgear Wireless router downstairs
Netgear wG111v2 Wireless Adapter
AOL Silver Broadband Package.
Intel Pentium 4 Processor

Is this enough to run a server?

I'm having doubts due to the fact last time I left my pc on for 3 days or so so much dust got stuck in the graphics card it started making a ticking noise... I have better PC specs now though, and a new case.

I can use spare space on my hard drive to host.

I also don't want the house to set on fire, or my pc to be fried (obviously, as much as I like my house, its my Ubuntu system im worried about... ;) )

Oh yeah, i have intel active monitor installed 2. I will test it under wine.

Thanks for your time and help.

---

### Post by BDNiner on 2008-04-28
Those specs are enough to run a server. i am guessing that it is some kind of Pentium 4 processor or a sempron. I would however install the base ubuntu system on another hard disk to keep the OS and your data serparate. Also i would try and use an ethernet connection and not wireless since there could be issues with the connection dropping.

---

### Post by intense.ego on 2008-04-28
> **GCoffee said:**
> Hello guys,

After many stressful attempts to find a good server to host things on i have decided that I might run my own server..

Here are my details:

I am in a small room with 1 pc in it.
250GB Hard drive, 80GB Ubuntu Partition, 80GB Windows Partiton
512mb RAM, Have enough spare ram to upgrade to 1gb if needed.
Netgear Wireless router downstairs
Netgear wG111v2 Wireless Adapter
AOL Silver Broadband Package.

Is this enough to run a server?

I'm having doubts due to the fact last time I left my pc on for 3 days or so so much dust got stuck in the graphics card it started making a ticking noise... I have better PC specs now though, and a new case.

I can use spare space on my hard drive to host.

I also don't want the house to set on fire, or my pc to be fried (obviously, as much as I like my house, its my Ubuntu system im worried about... ;) )

Oh yeah, i have intel active monitor installed 2. I will test it under wine.

Thanks for your time and help.

You didn't mention what processor you have, but, at the moment, it looks like more than enough to run a server.

---

### Post by GCoffee on 2008-04-28
I knew i forgot something... Its a intel pentium 4.

By the way:

> **BDNiner said:**
> Also i would try and use an ethernet connection and not wireless since there could be issues with the connection dropping.

I agree with you on that, apart from there is a small problem of having to run a wire through the downstairs roof for ethernet... That annoys me, ethernet is meant to be better than wireless in speed to. And dont you needed some sort of eternet plug on the wall?

P.S, this is going to sound really stupid for running a server, but at the moment i have 8.04 desktop edition... Can you run a server from that?

---

### Post by kavon89 on 2008-04-28
Well, it depends on what kind of server you plan on hosting. I'm going to assume you want to host a web server, maybe for personal downloads or a little website.

Your internet connection is probably the major bottleneck here. I found a UK website for testing your internet speed, run it and tell us what your upload bandwidth is in Kbps. (Also note that this number is not what the download speed others will normally have, 1 Kbps = 0.125 KB/s)

[http://resources.zdnet.co.uk/speedtest/](http://resources.zdnet.co.uk/speedtest/)

For uptime issues, pick up a can of compressed air from the store and clean out all the dust. Three days is a bit short for it to have dust problems. ;) My home server, running Ubuntu server 6.10, has had over 250 days of uptime before a brownout/outage turned it off. Haven't had to dust it yet and you won't fry your hardware or anything for keeping it on that long.

As for computer specs, I have a Pentium 3 with 64MB of ram that could handle Counter-Strike 1.6 and a Teamspeak 2 server. The maps loaded slowly but other than that I had a decent amount of players for my crappy connection before people complained of internet lag. Running with no GUI helped out, but I would imagine that running whatever you have planned would take roughly the same amount of resources as an old 700Mhz cpu and 64MB of ram.

---

### Post by BDNiner on 2008-04-28
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2000130294+1155831041&name=Up+to+200Mbps](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2000130294+1155831041&name=Up+to+200Mbps)

powerline networking theoretically allows you to use your powerlines to run the ethernet signal from one part of your house to another. I have not used it so i can't recommend it, but all you need is two of them. one by your server and the other by your modem. That could be an option with some research.

---

### Post by GCoffee on 2008-04-28
49.62kilobytes per second is bandwith speed

---

### Post by GCoffee on 2008-04-28
isnt powerlines just wireless then?

---

### Post by kavon89 on 2008-04-28
> **GCoffee said:**
> 49.62kilobytes per second is bandwith speed

Upload or Download speed? Upload is the most important, and is usually the smaller one.

Also, yes you can host a website/server for anything off of the desktop version. The server version just cuts out the "fat", which includes any GUI, and includes more configurations and different packages by default.

---

### Post by thewanderer on 2008-04-28
Setting up a home server is a great way to get started in linux systems administration, whether you would like to do it for a hobby or a career.

If you are going to make it available on the net, you can use dyndns or similar dynamic dns services to give you a dns name.

From there you can start to play with web server, mail server, file server, ftp server, security tools etc. The list goes on.

Don't forget that you will be opening a hole in your router for external internet access, so keep your system secure by keeping it up to date, use strong passwords and dont run old scripts.

Good luck!

---

### Post by smoker on 2008-04-28
> **GCoffee said:**
> isnt powerlines just wireless then?

these use the electrical wiring in your home to transmit data packets between each other, you cable one from your modem to a handy electical socket, and can plug another into any other socket in the home and cable from that to your other pc.

---

### Post by stmiller on 2008-04-28
Apache takes very little CPU to run. Unless you are running something pretty intensive like plone. For the most part that box looks great for a server. 

My Debian home server is a celery 700Mhz with 256MB of ram. :)

---

### Post by GCoffee on 2008-04-29
Here's my full bandwith spec's from a london, UK server:

Download Speed: 509 kbps (63.6 KB/sec transfer rate)
Upload Speed: 241 kbps (30.1 KB/sec transfer rate)
Latency: 57 ms

Is 241kbps enough?

---

### Post by GCoffee on 2008-04-29
OK everyone,

I have heard that the box is fit for a server! I'm installing xampp now and hopefully i can get a no-ip.com alias or something like that!

I'm patching up the security holes in xampp by the way!

---

### Post by LookTJ on 2008-04-29
> **GCoffee said:**
> Here's my full bandwith spec's from a london, UK server:

Download Speed: 509 kbps (63.6 KB/sec transfer rate)
Upload Speed: 241 kbps (30.1 KB/sec transfer rate)
Latency: 57 ms

Is 241kbps enough?
That's kinda a little slow, depends on what you will use for your server, but it's alright.

---

### Post by LookTJ on 2008-04-29
> **GCoffee said:**
> OK everyone,

I have heard that the box is fit for a server! I'm installing xampp now and hopefully i can get a no-ip.com alias or something like that!

I'm patching up the security holes in xampp by the way!
I can give you an alias if you want, just pm me then I will show you what domain name's DNS I control. And I suggest using Debian as a server rather than Ubuntu.

---

### Post by Raven_Oscar on 2008-04-29
I run my own home server on almost the same hardware. Except CPU which is AMD 1600 (so it is equal to lowest Pentium 4 processor from performance point of view). I use it mostly as NAS. And it is more than enough for LAMP (homepage and torrentflux), SAMBA, NFS and proxy for home network.
So if you are going to use it as host system for something like homepage or other things like that you definitely can use your hardware.

---

### Post by freduardo on 2008-04-29
Bit of a noobish question here:

Is it reasonably safe to run both a file server and a web server on the same machine? (Or better; Can it be made reasonably safe ...?)

I've always thought that this would not be recommended because you should keep the (internal) file server, with important data on it, as far away as possible from outside access...

Your thoughts?

---

### Post by Raven_Oscar on 2008-04-29
As for me it is secure enough to use one server for both hosting and file server. But I have not got any important data there.

---

### Post by BDNiner on 2008-04-30
> **freduardo said:**
> Bit of a noobish question here:

Is it reasonably safe to run both a file server and a web server on the same machine? (Or better; Can it be made reasonably safe ...?)

I've always thought that this would not be recommended because you should keep the (internal) file server, with important data on it, as far away as possible from outside access...

Your thoughts?

That is not a good practice, apache can be hacked. With permissions you can stop someone from accessing files once they have hacked apache but i would not take that chance.

---

