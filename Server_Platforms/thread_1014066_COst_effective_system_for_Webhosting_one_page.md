---
title: "COst effective system for Webhosting one page"
date: 2008-12-17
forum: Server Platforms
---

### Post by mikeym on 2008-12-17
Hi,

I'm looking for a bit of advice on producing a cheep to setup and run system to host one webpage. 

The page would need to run Apache, PHP and MySQL and have about 1-2Gb space for the site. The traffic would be extremely low 20 users accessing every couple of days each. 

I'm wondering what I can do to get a cheep older PC and throttle it down / install low power hardware / fans etc to get it running as economically as cheaply as possible. 

Thanks for sharing your experiences.

---

### Post by ubuser_7 on 2008-12-17
If its just one page, you can look at external webhosts. They will be really cheap.

---

### Post by mikeym on 2008-12-17
My experience is that you're looking a £50 per year and the one I have has Drachonian security settings for PHP which wont let you actually produce a site that works. I suspect this is likely to be common. 

Surely I can produce a system that is cheap to produce that costs less than this to run that I can setup myself.

---

### Post by ubuser_7 on 2008-12-17
While you can get it done for much less than 50 punds an year, but still I agree with you on security settings. In general it means a loss of control to me.

---

### Post by jcsteele on 2008-12-17
Is it just apache?  You won't be needing anykind of dns, mail, etc.?  If that is the case you can do it very cheaply with your existing internet connection - simply find some cheap hardware that works, install apache/mysql/etc., and use a dyndns service ([http://www.dyndns.com/](http://www.dyndns.com/)) that is available freely....if your lucky enough to have a static ip to the internet, a dyndns service is not required.  The hardware does not need to be anything special - you won't be running any type of GUI on it, so literally a Pentium 233mhz with a decent ammount of ram would work great....

If your doing this on your home network and you have a router, you can simply use port forwarding to redirect traffic to port 80 on the router to the internal server - then voila! your up and running.

You could also do this on your own machine without purchasing/finding more hardware - assuming your machine will be connected and running when it needs to be.

---

### Post by mikeym on 2008-12-17
This is pretty much what I'm wanting to do. It's more the hardware. Trying to reduce the power consumption as much as possible. 

What I was thinking was to buy a P3 or 4 from ebay for as little as possible. Buy some kind of Flash memory device like SD card or something to install the system on and house a couple of Gb of space (low power low noise), and find some way to reduce power and noise on the CPU fan and PSU. 

It's really advice on wheather this will work and where I could find the bits to reduce power (or what I can get away with in terms of pulling fans out of cases).

---

### Post by jcsteele on 2008-12-17
You will just have to look at the specs of the hardware - watt usage of the power supply, etc.  You also might want to look at alternatives to standard intel and amd chips then too....there are several cpus that you can find that use alot less power (alot less performance too) than an intel/amd.

In the past, I have used a soekris board with OpenBSD installed - everything runs from a CF card though and its geared mainly toward routing functions, not webserver..but anything is possible.  There is a wiki article at [https://wiki.ubuntu.com/Soekris](https://wiki.ubuntu.com/Soekris) for Ubuntu on the Soekris.

If all else fails, look on ebay, etc. for older hardware - most of the older cpus dont require a cpu fan, just a heatsink to be used - case fans can be removed too assuming the environment is cool as well.  If it was my project, I would honestly stay away from SD and CF type stuff since your machine is going to need a lot of read/write operations with mysql/php on board - a simple 2.5" (preferred) or 3.5" IDE drive would work great, and be a lot cheaper.  An older laptop might work well too.

---

### Post by mikeym on 2008-12-22
So what systems could I happily remove the CPU fan from and would I need to add a big heatsink? Also what about the PSU?

---

### Post by gTinker on 2008-12-22
[QUOTE=mikeym]So what systems could I happily remove the CPU fan from and would I need to add a big heatsink? Also what about the PSU?[/QUOTE]

I'd really like to help you mikem, are you aware of what a huge, difficult, question you've asked? In order to properly address the question, one has to have vast hardware experience with the old products you're talking about and probably also a quite a great deal of hands-on. However, you're in luck, I'm an old guy and fit the criteria. On the other hand, I don't have the time or inclination to scan through Ebay and find something that was for sale and fit the bill. If you have a friend, or if there is a LUG in your area, probably someone there has old parts and could advise you or sell you something. I know I could if you were near me.

But, there is still the chance for me to offer advice. 

One poster has already suggested using an inexpensive hosting service. Good advice for what you have described. Someone else to deal with hardware issues or failures, you only have to worry about your site and making sure the hosting service is still meeting your needs.

If you still want a hardware solution, I suggest one of the small mini-itx boards with a C3 processor. Small cases also can come equipped with small, energy efficient, power supplies. A fair number of those systems were made that only had a heatsink and ran in the range of 800MHz. These days, those older ones have been left behind and likely can be found for a reasonable price. Small footprint, takes little room, quiet. Given all the time you would be putting in trying to modify an old PC, it could be the most cost effective hardware solution.

Otherwise, I'll try to keep my eyes open for any questions you ask about old hardware. I doubt you could get away with removing the CPU fan from anything more than one of the low speed classic pentiums. Perhaps if you underclocked it and lowered the CPU voltage a tad. But that wouldn't really be a good use of your time. Old power supplies usually weren't very efficient.

If this was an enterprise situation, I would suggest you consider the total cost of ownership, including the time you will spend and frustration.

Good Luck!

---

### Post by windependence on 2008-12-23
There is a huge wave of these type systems coming available right now.

Try this board:

[http://www.intel.com/Products/Desktop/Motherboards/D945GCLF/D945GCLF-overview.htm](http://www.intel.com/Products/Desktop/Motherboards/D945GCLF/D945GCLF-overview.htm)

You should be able to get  that board for about $70 US. 

You can use an ATX case as the MITX board will work in that OR use a case like this:

[http://www.apextechusa.com/products.asp?pID=171](http://www.apextechusa.com/products.asp?pID=171)   about $59 US

The processor on the mobo uses about 4 watts, lower than anything you'll get on old hardware and it's DUAL CORE.  It runs at 1.6 GHz. Total power consumption with drives and all should only be about 30 watts.

-Tim

---

