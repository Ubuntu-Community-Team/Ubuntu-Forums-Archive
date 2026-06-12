---
title: "Network Server Monitoring opinions"
date: 2010-08-20
forum: Server Platforms
---

### Post by quietas on 2010-08-20
I've recently had an elderly Debian unit fail which had been running an ancient, but usuable, version of Nagios. While it worked, it was minimal and we would like to add some basic performance monitoring. Hard drive usage, RAM consumption, CPU, the basics.

I've played with Zenoss, Zabbix, Hyperic, PandoraFMS, Nagious, and I know of a few more like Open NMS, Groundworks, and others. Ubuntu is always my first choice for headless purpose built systems, so I thought I'd put out a question.

What, in your mind, is the best network monitoring solution for a multi-OS environment and why?

This could be Windows or Linux based for both the host and the scanning targets. Thanks in advance and I value any input.

---

### Post by arrrghhh on 2010-08-20
I really did like the Zenoss product.  Their enterprise edition was outrageously priced, but the core product is free - and gave a TON of functionality.

OpenNMS was OK but has some way to go before it competes with the big boys.  I haven't heard of/used Zabbix, Hyperic or PandoraFMS...  I'll have to check them out, thanks!

---

### Post by quietas on 2010-08-20
One thing I'll add also is that I have noticed most seem to do far more than I really need. Tell me when it's down, it's drive is full, it's out of RAM, or it's working too hard. More is nice, but something that does that and is easy to make work is key.

---

### Post by joeinbend on 2010-12-08
[2 cents]
Having been through testing all of the monitoring tools mentioned in this post in the past, I have to say that in my opinion SpiceWorks is still the best. Extremely easy to configure, does an excellent job of picking up your devices accurately and in-depth. My only complaint is they have not released a Linux version of this software yet, so this means you have to run it on Windows still. Personally I have a low-end system that I did a stripped-down XP install and that quietly sits running my SpiceWorks. Hopefully in the future they'll port a version to Debian.
[/2 cents]

---

### Post by quietas on 2010-12-08
> **joeinbend said:**
> [2 cents]
... I have to say that in my opinion SpiceWorks is still the best...
[/2 cents]

I've found I like Spiceworks and have it running on a VM full time. It's great for whole network review, but it really sucks in depth real time monitoring. I'm not needing up to the second SQL load monitoring or Exchange database stability, but basic hard drive capacity, CPU load, and primarily uptime.

I'm still looking for that all in one perfect system with an agent for the critical servers and yet has an overview of all devices on the network. Something as easy to deal with as Spiceworks, but has the monitoring capability of Hyperic or Zenoss.

---

### Post by arrrghhh on 2010-12-08
You can look at SolarWinds products, they seem to be a good mix of ease to install/use and configurability... But they're far from free (at least the ones you'd probably be considering ;))

---

### Post by rabinnh on 2011-02-07
Shameless plug warning, but check these YouTube videos out.  They show an inexpensive Icinga appliance that configures itself.

[http://www.youtube.com/watch?v=CY_2viaUpdI](http://www.youtube.com/watch?v=CY_2viaUpdI)
[http://www.youtube.com/watch?v=hSg2zA4mAmI](http://www.youtube.com/watch?v=hSg2zA4mAmI)

---

### Post by rubylaser on 2011-02-07
Zenoss works great for me. Although I've heard Spiceworks is great, I just can't bring myself to run a Windows box to monitor my network.

---

### Post by JohnYYC on 2011-02-07
I highly recommend taking a look at [Cacti]("http://cacti.net"). You can add plugins to it to email you reports and even alert you when machines are down. It also has a great support forum that is always active.

---

### Post by LightningCrash on 2011-02-07
There are a couple of approaches here.

A system like Monit can monitor for flaggable problems, like low drive space, processes dying, log file monitoring, etc.

Collectd can keep performance statistics on your systems using CSV or RRD files. This is useful for performing "What the heck just happened?!" post-mortems on your runaway servers. It's also good for keeping data on disk usage. 

Nagios is very good for polling SLA-driven services on your network, such as websites, SSH tunnels, user counts, etc. You can also collect data with pnp4nagios in RRD-style graphs.

---

### Post by ravingmad on 2011-05-26
I looked at various options myself and in the last few months I suddenly started getting one of my apache servers which would die at very random times. I eventually found monit and voila no more worrying about Apache or any service for that matter going down. It was a breeze to configure. Wish I had heard about it sooner :)

---

