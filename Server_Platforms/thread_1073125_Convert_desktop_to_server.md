---
title: "Convert desktop to server ?"
date: 2009-02-18
forum: Server Platforms
---

### Post by armageddon08 on 2009-02-18
I have an old desktop with the following specs:
Processor: Intel Pentium 4 with H/T (64-bit)
           2.93 GHz
HDD: Internal-80GB SATA
     External-160GB
RAM: 1GB

Can I convert my desktop into a home server for media streaming/sharing and internet connection sharing ?

---

### Post by ghindo on 2009-02-18
Absolutely.  I've even heard of people converting old laptops into servers.  It's not ideal, but it works.

---

### Post by armageddon08 on 2009-02-18
> **ghindo said:**
> Absolutely.  I've even heard of people converting old laptops into servers.  It's not ideal, but it works.

So could you tell me how do I go about doing it ?

---

### Post by HermanAB on 2009-02-18
Linux is Linux is Linux....

You don't have to do anything to turn a desktop or laptop into a server!  

However, if you are a sucker for punishment, do:
$ sudo init 3

Cheers,

Herman

---

### Post by ghindo on 2009-02-18
> **armageddon08 said:**
> So could you tell me how do I go about doing it ?Well, what would you like to know, specifically?  There's a lot to go over.

---

### Post by armageddon08 on 2009-02-18
> **ghindo said:**
> Well, what would you like to know, specifically?  There's a lot to go over.

Just that if you could point me somewhere I could begin...

---

### Post by ghindo on 2009-02-18
> **armageddon08 said:**
> Just that if you could point me somewhere I could begin...Well, there are various things you could with the computer itself.  You could undervolt the CPU, you could buy bigger hard drives, put them in RAID, etc..

As for software, it depends on what you want to do.  There are lots of different distros that are excellent for servers.  Generally, you want to find something without X, as it's less taxing on the hardware.  What do you want to do with your server?

---

### Post by armageddon08 on 2009-02-18
> **ghindo said:**
> Well, there are various things you could with the computer itself.  You could undervolt the CPU, you could buy bigger hard drives, put them in RAID, etc..

As for software, it depends on what you want to do.  There are lots of different distros that are excellent for servers.  Generally, you want to find something without X, as it's less taxing on the hardware.  What do you want to do with your server?

Basically, I want to use it for media streaming and ICS...

---

### Post by ghindo on 2009-02-18
> **armageddon08 said:**
> Basically, I want to use it for media streaming and ICS...Hm, I'm not sure.  I know there are distros that specialize in that sort of thing, but I don't know them off-hand.

---

### Post by handy on 2009-02-18
I use [*_FreeNAS_*]("http://www.freenas.org/") to backup my important data & to store/stream video on my home LAN.

It is dead easy to set up, it is beautifully made, the web browser via client GUI wants for nothing.

You can set it up as Transmission torrent slave, which will be the most difficult thing you will ever do with it.

FreeNAS supports various types of RAID, soft, hard & fake.  Which of course could be the other difficult thing depending on your hardware.

I chose not to use RAID, as the home LAN will be the bottleneck, & using RAID in my situation is a waste of money on hardware, electricity & it will be noisier.

***[Edit:]** I just noticed that you want to use your server for internet connection sharing.  FreeNAS is no good for you then.  I actually have another $5- from the rubbish dump headless box, which runs [[I]_IPCop_*]("http://www.ipcop.org/") with the [*_Copfilter_*]("http://www.copfilter.org/") add-on; this box is a firewall/router/proxy/& other services box, which gives you complete control over what network is allowed to do.[/I]

---

### Post by jerrrys on 2009-02-18
Hay handy:
i would like to find some reading material on freeNAS, know of any pdf's out there? thanks

---

### Post by dmizer on 2009-02-18
FreeNAS is fantastic for a file sharing platform.

I suggest you stick with a hardware router for ICS rather than try to fiddle with IPtables and configure your own.

---

### Post by handy on 2009-02-18
> **jerrrys said:**
> Hay handy:
i would like to find some reading material on freeNAS, know of any pdf's out there? thanks

As dmizer stated, FreeNAS is great as Network Attached Storage, for which it is a very specialised build. It is not designed to be used for anything else, & is stripped down to under 75Mb in size in an effort to make it faster & more reliable & secure.

So, it won't allow you to use it for ICS.

In my previous post I linked to the FreeNAS website which is a good start regarding reading matter, sourceforge also has some very good forums relating to FreeNAS.

---

### Post by jerrrys on 2009-02-18
thanks handy

---

### Post by armageddon08 on 2009-02-18
Thanks guys! Sorry for posting in the wrong sub-forum.

---

### Post by handy on 2009-02-18
> **armageddon08 said:**
> Thanks guys! Sorry for posting in the wrong sub-forum.

I did it for ages when I first started here, it took me over a year to even notice that the now defunct Backyard sub-forum even existed! ;)

---

