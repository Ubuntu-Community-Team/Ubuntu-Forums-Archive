---
title: "Mini PC with ubuntu server"
date: 2016-08-29
forum: Server Platforms
---

### Post by dam034 on 2016-08-29
Hi everyone,


in my office there are 10 computers and an access point wi-fi to connect mobile devices to the office LAN.

What I need is to create a DNS server because I want to create an internal DNS zone office for the resolution of the type names: "chief.internal" or "john.internal", thus creating a TLD called "internal".

It takes a Ubuntu LTS server operating system (14 or 16, but I opt for 14) with bind9 and its configuration, which I can do.

The problem is the hardware: I won't hold any computer always turned on for DNS service, but I would put a mini PC.

I would an advice, a mini PC with these features:


[LIST]
[*]small physical size (about as much as a hand)
[*]configurable BIOS (also only trivial options)
[*]USB port to start the ubuntu installation from pendrive and/or to any expansion of memory
[*]ethernet port, possibly gigabit
[*]VGA or HDMI video output for installing ubuntu server, then I no longer need
[*]suffice 512 MB of RAM
[*]if possible at least 4 GB of storage
[*]processor capable of supporting continuous DNS resolution requests (at least 1 GHz, even 1.5)
[*]mini pc with case and power cable
[/LIST]

As an example, it would be fine one like this ([link to Amazon]("https://www.amazon.it/Amlogic-Core-Mini-Android-Streaming-Streamer/dp/B01A33EVYY/ref=pd_sim_107_2?ie=UTF8&psc=1&refRID=FEGTF86MSBYCK4MVQX69&tag=tomsforum-21")), but enough that I can enter in the BIOS. I don't need the telecontrol.

I state that I don't want to spend more than 60-70 euros.

Is there anything that matches the characteristics I have written or at least is near those?



Thanks,
dam034

---

### Post by TheFu on 2016-08-29
Why not just load a tiny server into a VM on a system that is already running 24/7?
Also - how many clients are there on the LAN to be served - I suspect 1Ghz is overkill for most small offices.

---

### Post by dam034 on 2016-08-30
> **TheFu said:**
> Why not just load a tiny server into a VM on a system that is already running 24/7?
In the office none of the computers is running 24/7, but only the modem/router, for this reason i want a mini pc, only for DNS queries.

> **TheFu said:**
> Also - how many clients are there on the LAN to be served - I suspect 1Ghz is overkill for most small offices.
The maximum is 10 desktop pc and 10/15 mobile devices, however I don't want that in case of 20/25 clients simultaneously require DNS queries, all is delayed.


Can I use a raspberry pi 3? Or is not enough?



Thanks,
dam034

---

### Post by TheFu on 2016-08-30
I think r-pi's are amazing, but not for something critical for 24/7 use. Plus for the CPU performance and I/O non-performance, they are way, way, way, way overpriced.  I use an [APU2 device from PCEngines]("http://pcengines.ch/apu2b4.htm"). Sadly, they might not sell it to you in Europe, though it is shipped from there (legal issues). It is an amazing little device, silent, no fan, USB3, 10W or less, and supports virtual machines.  No video support, serial console only. It was $144 and 3 days from order to my home. I expect to use it for my edge router for a decade.  It is replacing an AMD E350 that was about $140 total including swapping out a very loud PSU for a silent picoPSU.  These systems were more about silence and low power use with just enough CPU to do a specific job.  $10/yr is a very reasonable cost for something like this, IMHO.

It is possible to build a fairly cheap, powerful system that uses about 40W continuous for $120 if you reuse an old PSU, case, RAM, HDD.  My NAS/DHCP/Plex/Calibre server is built around a Pentium G3258. It uses more power, but has much better I/O and USB3 throughput than the other 2 devices above.  It currently has about 16TB of storage connected with room for another 32+TB connected through USB3 external arrays. Never had any throughput issues with disk, USB or network, even when the machine was very busy.

For a used device, I think you can get into the $70 range, but those will be C2D CPUs in older laptops.  Swap out the spinning HDD for a small SSD and you could have a cheap solution. Just be certain it comes with a GigE port and don't run it with the lid all-the-way closed. Airflow around the keyboard is part of laptop cooling.

Stay with X86. It solves many issues that can't be solved with ARM at this point. How much is your time screwing around with issues worth? Plus not having enough throughput is an issue with ARM devices that I've seen.  Oh - and if you have a choice, get Intel networking onboard. Avoid all the other choices like broadcom and realtek. There are reasons.

For a really small office, you can just use an avahi server and it will run the DNS stuff automatically. No need for BIND or any manual configuration for new systems. [https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf) ...  hostnames will be addressed by hostname.local on the LAN with avahi providing the mdns service.

Also, might want to run a caching web proxy (squid) on the machine to make the internet feel faster. 

Don't know if any of this is helpful. Just providing some options. I suspect you'll find a different answer. Some of the AMD A4 systems could work too.

---

### Post by dam034 on 2016-08-30
> **TheFu said:**
> I think r-pi's are amazing, but not for something critical for 24/7 use. Plus for the CPU performance and I/O non-performance, they are way, way, way, way overpriced.
I want to know why r-pi isn't able to 24/7 use. For the temperature? Or for the performance?

> **TheFu said:**
> Stay with X86.
Yes, I'm going to install 32-bit OS.

> **TheFu said:**
> Also, might want to run a caching web proxy (squid) on the machine to make the internet feel faster.
This is a good idea ;)

> **TheFu said:**
> Don't know if any of this is helpful. Just providing some options. I suspect you'll find a different answer. Some of the AMD A4 systems could work too.
Well, I want a mini pc that runs a DNS server without delays on answering to the clients. Thus, I need the CPU able to this, nothing else. I don't need 500 GB of storage, because ubuntu server + dns server don't need more than 4-5 GB.

I can't get the product you have beacuse it isn't sellable in Europe.

I found this products on Amazon (in addition to r-pi):

[LIST]
[*][https://www.amazon.it/dp/B015EV086U/ref=wl_it_dp_o_pC_S_ttl?_encoding=UTF8&colid=3HGTIGJWZNWUR&coliid=I3C98QRWRPLJV8](https://www.amazon.it/dp/B015EV086U/ref=wl_it_dp_o_pC_S_ttl?_encoding=UTF8&colid=3HGTIGJWZNWUR&coliid=I3C98QRWRPLJV8)
[*][https://www.amazon.it/dp/B01A33EVYY/ref=wl_it_dp_o_pC_nS_ttl?_encoding=UTF8&colid=3HGTIGJWZNWUR&coliid=I3SE8AQW309JUK&psc=1](https://www.amazon.it/dp/B01A33EVYY/ref=wl_it_dp_o_pC_nS_ttl?_encoding=UTF8&colid=3HGTIGJWZNWUR&coliid=I3SE8AQW309JUK&psc=1)
[/LIST]

The first costs more than my budget, but I think it's good for what I need, the second appears good (features and price), but I can't edit the BIOS to delete android and install ubuntu server.

Unfortunately, I'm not even an expert about the BIOS or editing chip inside the PC, for this, I need a mini pc where, without particular modifications, becomes the server I need.

What do you think about the two products I linked you from amazon?



Thanks,
dam034

---

### Post by slickymaster on 2016-08-30
*Thread moved to **Server Platforms**.*

---

### Post by dam034 on 2016-08-30
I didn't get a satisfactory response, I need advices yet from the users TheFu, if possible.



dam034

---

### Post by QIII on 2016-08-30
Hello!

Please neither "call out" specific volunteers demanding advice nor expect answers to be forthcoming so quickly after your last post.  Those who volunteer here have their own lives and are often not around here.

Please be both polite and patient.

---

### Post by TheFu on 2016-08-31
x86 means "intel compatible", not ARM, not MIPS, not Qualcomm. I would avoid ARM unless it comes specifically designed to do what you want. I learned this the hard way, burned multiple times.

If you will run a proxy server, then more storage and CPU will be needed than for DNS alone.  Did you consider avahi?

---

### Post by dam034 on 2016-08-31
> **TheFu said:**
> If you will run a proxy server, then more storage and CPU will be needed than for DNS alone.  Did you consider avahi?

Actually I need only a DNS server for the office, in the future I'll see if there will need a proxy server.

I want to focus on the hardware, at the moment I just need 1GHz of CPU and 512 MB of RAM.

Can you tell me which of the products I posted in this topic (r-pi 3 and the two on amazon) would be the best for me? Or if there is another mini pc designed for this things?




Thanks,
dam034

---

### Post by TheFu on 2016-08-31
> **dam034 said:**
> 
Can you tell me which of the products I posted in this topic (r-pi 3 and the two on amazon) would be the best for me? Or if there is another mini pc designed for this things?


None of those are something I'd deploy. Already provided what I've done. Sorry it isn't helpful.

---

### Post by The Cog on 2016-08-31
To answer the original post, I think a RaspberryPi 3 comes very close to meeting your requirements. 

I'm not sure about putting Ubuntu on it though. I would think the Unity GUI might be needlessly heavy on resources. I have a Pi B here that has been running as a print server (USB printer) and voice chat server for a few years now. It runs the official PI OS Raspbian which is a tweaked Debian. I don't remember what the GUI is (haven't even seen it for well over a year) but I'm sure it's lighter weight than Unity. For the simple services like print server, 8-user voice server and your DNS server for 12 PCs I think even the original Pi is powerful enough, and the configuration is the same in both Raspbian and Ubuntu. That said, I can't help you with setting up the DNS server - there are aspects that I don't understand. I think the Fu probably knows a lot more about that than I do.

I don't think I would trust the MXQ Pro. It's not clear if you can replace Android and put a proper Linux distro on it. You can not just shove any old ARM Linux on any old ARM box like you can with x86 - the Linux has to be built for the specific hardware, such as Ubuntu for the Pi or Raspbian (Debian for the Pi).

---

### Post by SeijiSensei on 2016-08-31
I think you're way overestimating the amount of processing power needed to handle DNS queries in a office that size.  I'm sure you could run bind9 on a Raspberry Pi without problems.  Just pick a distro without a GUI.

---

### Post by coldraven on 2016-08-31
This person is running Squid on a Pi3. Would it be possible to use two Pis? DNS on one and Squid on the other.
[https://the-server.ninja/2016/03/26/using-a-raspberry-pi-as-a-squid-proxy-cache/](https://the-server.ninja/2016/03/26/using-a-raspberry-pi-as-a-squid-proxy-cache/)

---

### Post by SeijiSensei on 2016-08-31
I wouldn't run Squid on a Pi.  First you want a machine with enough storage to cache all the requests and write Squid's logs which can be extensive.  You could use a Pi with a USB drive or a really big memory card, but I'd just re-purpose an existing desktop machine with a decent CPU and memory for that task.  Also my Pi only has one Ethernet port.  A Squid implementation with "transparent" proxying works best on a machine with two network cards, one facing the Internet and one facing the local network.

---

### Post by dam034 on 2016-09-02
Actually, I don't need a proxy server. I know a proxy server needs 2 ethernet ports.

I'm thinking for a dns server, and this don't need much storage, but I think are sufficient 5 GB of storage.

For the RAM, 512 MB are sufficient.

Which product can I use for my dns server?


Thanks,
dam034

---

### Post by TheFu on 2016-09-02
A proxy server doesn't require 2 ethernet ports. That doesn't matter to you, since you only want a DNS server.

I would think that for a small, single purpose DNS server, less than 512MB storage would be required, provided you don't load a huge distro. 5G of storage would be fine, though I don't know where you'd find that size.  A 16G SSD is about the smallest I've seen.

"sufficient" is a hard term to determine for every situation. That is why I've recommended more capable systems, made with hardier parts that will likely be useful doing more too. There are lots of HW that _will work_, at least in the beginning.  Heck, you could probably find a $20 router box that will run an 8 yr old DD-WRT and that would be fine too. It isn't like DNS is a heavy load. Just don't put it on the internet (dd-wrt has lots and lots of unpatched bugs for most specific HW out there).

---

### Post by dam034 on 2016-09-02
I found [this product]("https://www.amazon.it/Vilros-Raspberry-Pi-Complete-Starter/dp/B01DC6MKAQ/ref=sr_1_3?ie=UTF8&qid=1472846538&sr=8-3") on amazon, a r-pi3 with complete kit.

When I have written 4-5 GB of storage would be fine, I didn't intend I want an HDD of that size, but the smallest that exists.

I found [this page]("http://www.ubuntu.com/download/server/arm") on ubuntu official site, where I can download the 16.04 version of ubuntu for arm, but I want to download the 14.04 server version. Where can I find it?

I want to know another thing, how can I install ubuntu server on the r-pi? Is the installation like a desktop pc?



Thanks,
dam034

---

### Post by SeijiSensei on 2016-09-03
> **TheFu said:**
> A proxy server doesn't require 2 ethernet ports. That doesn't matter to you, since you only want a DNS server.
In "transparent" mode having two ports makes things much easier.  You intercept outbound port 80 traffic from the local network and push it to Squid via localhost.  I usually build a box with Squid and masquerading, put it behind the egress router, and make it the default gateway for the network.

> **dam034 said:**
> I found [this product]("https://www.amazon.it/Vilros-Raspberry-Pi-Complete-Starter/dp/B01DC6MKAQ/ref=sr_1_3?ie=UTF8&qid=1472846538&sr=8-3") on amazon, a r-pi3 with complete kit.
I built a Pi from a similar kit.  While I haven't used it as a DNS server, I have no doubt it would do the job.  

> When I have written 4-5 GB of storage would be fine, I didn't intend I want an HDD of that size, but the smallest that exists.

I manage a nameserver for a network of over 250 users.  It's currently using about 900 MB of memory for this task.

That kit includes a 16 GB memory card; that's plenty for the operating system and any other storage you may need.  If you ever need more storage, you can attach a USB drive.

> I want to know another thing, how can I install ubuntu server on the r-pi? Is the installation like a desktop pc?

Installing software on a Pi is very different from installing Ubuntu onto a PC.  I suggest you use the "[Raspbian]("https://www.raspberrypi.org/downloads/")" distribution, a version of Debian designed for the Pi.  (Ubuntu is based on Debian, so Raspbian will look quite similar, especially at the command prompt.)

That kit you cited has "[NOOBS]("https://www.raspberrypi.org/downloads/noobs/")" installed on the SD card.  It provides an easy way to install Raspbian.

---

### Post by dam034 on 2016-09-04
I talked to my head office of the fact that an office DNS server can't be low-efficient.

He replied is willing to increase the budget, just to come out an efficient server. So I have shown him these two products:

[LIST]
[*][https://www.amazon.it/dp/B015EV086U/ref=wl_it_dp_o_pC_S_ttl?_encoding=UTF8&colid=33Z7TJKGTG48E&coliid=IB6DUW97DJRFQ](https://www.amazon.it/dp/B015EV086U/ref=wl_it_dp_o_pC_S_ttl?_encoding=UTF8&colid=33Z7TJKGTG48E&coliid=IB6DUW97DJRFQ)
[*][https://www.amazon.it/dp/B00HVTHQ4Q/ref=wl_it_dp_o_pC_nS_ttl?_encoding=UTF8&colid=33Z7TJKGTG48E&coliid=I3KE7RIS2TUV90](https://www.amazon.it/dp/B00HVTHQ4Q/ref=wl_it_dp_o_pC_nS_ttl?_encoding=UTF8&colid=33Z7TJKGTG48E&coliid=I3KE7RIS2TUV90)
[/LIST]

For the storage, I have no problem because in the office there are a dozen of unused 2,5'' hard disks. In the office there aren't solid disks.

So we reached 150 euros, but I think this mini pc is better than r-pi.

I want to install a 64bit version of ubuntu server 14.04 LTS.

I also want to install a web server to redirect all http request done to websites obscured by head office (like social), because in the office there are employees that visit those websites in working time.

I want to know your opinion about this choice to use more expensive products, but efficient. And I want to know if the RAM I linked on amazon is compatible with the mini pc I linked.





Thanks,
dam034

---

### Post by SeijiSensei on 2016-09-04
Do you really not have another PC lying around that you've taken out of service?  It would make a fine DNS server.

---

### Post by linuxdude1990 on 2016-09-05
Ubuntu has an ARM varient, as does Debian, OpenSuSE, and CentOS. 

Raspberry Pi 3 is perfect as is for anything in its specs. Personal experience having 9 of them across my home, and have even set up domain controllers, cash registers, etc. with them.

---

### Post by springshades on 2016-09-07
I honestly feel like most of this stuff tends to run over my head, so I try to find simple, hacky solutions that just work. I also realize that this is very different from what everyone else is suggesting, but what about daisy chaining something like this in with your current router? It's already running EdgeOS which can do quite a few things via GUI and still has the command line tools that you need to do anything more complicated. Another upside is that someone has probably already set up something very similar to what you want on EdgeOS before, so you may be able to find a guide for it somewhere. It's pretty cheap too.

[http://www.newegg.com/Product/Product.aspx?Item=0XK-000W-00080&ignorebbr=1](http://www.newegg.com/Product/Product.aspx?Item=0XK-000W-00080&ignorebbr=1)

---

### Post by TheFu on 2016-09-07
> **springshades said:**
> I honestly feel like most of this stuff tends to run over my head, so I try to find simple, hacky solutions that just work. I also realize that this is very different from what everyone else is suggesting, but what about daisy chaining something like this in with your current router? It's already running EdgeOS which can do quite a few things via GUI and still has the command line tools that you need to do anything more complicated. Another upside is that someone has probably already set up something very similar to what you want on EdgeOS before, so you may be able to find a guide for it somewhere. It's pretty cheap too.

[http://www.newegg.com/Product/Product.aspx?Item=0XK-000W-00080&ignorebbr=1](http://www.newegg.com/Product/Product.aspx?Item=0XK-000W-00080&ignorebbr=1)

There are 50,000 solutions to the OPs question.  All of the ones above from volunteers seem reasonable, at least to me. There are pros/cons for each too.  All the different provided options can work for the base needs.  Reasons for each have been provided and the OP just needs to decide and go.  

Hopefully, he will close this thread and tell us which he went with and update in a week how it is working.  Hopefully.

---

