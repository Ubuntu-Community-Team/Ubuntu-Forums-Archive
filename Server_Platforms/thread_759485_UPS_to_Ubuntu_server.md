---
title: "UPS to Ubuntu server"
date: 2008-04-19
forum: Server Platforms
---

### Post by frodemt on 2008-04-19
I am looking for an UPS that work well with Ubuntu.

My server has a rated VA of 350.

Do you know if this one will work in linux: [http://www.powerware.com/UPS/5110_UPS.asp](http://www.powerware.com/UPS/5110_UPS.asp)

This one is a bit more expensive: [http://www.apcc.com//resource/include/techspec_index.cfm?base_sku=BR800I](http://www.apcc.com//resource/include/techspec_index.cfm?base_sku=BR800I)

The first one will be more suited for my needs I think. Both of them are line interactive.

---

### Post by Koybe on 2008-04-19
I never tried those, I'm running a MGE UPS Ellipse on linux, it's working nicely.

---

### Post by Deathrend on 2008-04-19
I have rhoughly five servers on [http://www.newegg.com/Product/Product.aspx?Item=N82E16842102048](http://www.newegg.com/Product/Product.aspx?Item=N82E16842102048)
I cheat though.  I have the UPS hooked up to a 2003 server, that when it's shutting down, sends the needed shutdown commands via OpenSSH/Perl t kill the other servers on the UPS.  It also takes care of Wake On LAN when it comes back up.

Just an idea, overly complicated for something that could have a much cleaer way..

It works /most/ of the time! :)

---

### Post by frodemt on 2008-04-19
> **Koybe said:**
> I never tried those, I'm running a MGE UPS Ellipse on linux, it's working nicely.

I had a MGE Pulsar Ellipse 800VA UPS. It died on me after two years of service.

---

### Post by frodemt on 2008-04-19
Yeah, and the UPS must be able to hold up my server for 20 minuttes. Not sure if I am able to get it up by remote if the server is shut down by the UPS...

---

### Post by kdkirsch on 2008-04-19
Hi. I use an [APC BR800BLK 800 VA 540 Watts UPS]("http://www.newegg.com/Product/Product.aspx?Item=N82E16842101140") to provide backup power to my office server.
I use [APC UPS Daemon]("http://www.apcupsd.org/") to send a shutdown comand (connected to the server via USB) after 600 seconds of power outage. The settings are extremely configurable. I am a beginner-to-intermediate ubuntu user and I had no problems setting this up. It works great for me. Also, look at this thread: [APC UPS and using apcupsd ]("http://ubuntuforums.org/showthread.php?t=114748") Hope this helps.

---

### Post by andguent on 2008-04-19
> **frodemt said:**
> Yeah, and the UPS must be able to hold up my server for 20 minuttes. Not sure if I am able to get it up by remote if the server is shut down by the UPS...

Most BIOS's include the power management option for what to do after power returns. If you set it to always power on, it _should_ automatically power up once the UPS has had 20-30 seconds of good AC restored.

As for apcupsd, I've never found an APC brand UPS that software couldn't communicate with. Assuming it has a USB connector, it is dead easy (4 lines of .conf). The old serial connector models usually added another 15-90 minutes of muttering under your breath.

In the end, get something with a good warranty, expect that it will work fine, and then test it. I personally prefer to maintain a good ground connection even when the UPS has no power. Connecting the power of the UPS through a basic power strip should accomplish that.

---

### Post by frodemt on 2008-04-20
Thank you for your answers. I think I will give the APC a go then.

Not going to buy before early June, so I hope the prices will drop a bit until then.

---

