---
title: "Raspberry Pi: should I?"
date: 2013-11-18
forum: Ubuntu, Linux and OS Chat
---

### Post by lykwydchykyn on 2013-11-18
Yeah, this isn't about Ubuntu, but I wanted some opinions because you guys have steered me right in the past. 

Since the Spring, I've been doing Arduino projects with the kids and they love it.  Now my oldest wants to check out the raspberry pi.

Raspberry Pi's are cheap, right?  Well sort of.  You can get a Model A for $25, but of course you really want the Model B at $35.  Then you need a power supply (ding!), an SD card (ding!), a wifi adapter (ding!), and a case (ding!).  Of course to connect keyboard, mouse and wifi, you need a (powered) USB hub(ding!); and since our monitors are VGA, we'll need an HDMI-to-VGA adapter, but it needs to be one known to work with a Pi (because some don't, apparently) (oh yeah, ding!).  Suddenly the $25 proposition is approaching a $100 proposition.

I work in IT, and have family that work in computer recycling, so we have no shortage of old PCs running (or capable of running) Linux (So, yeah, we already have XBMC on our TV PC, we already have a Debian server running this and that, etc.).  I thought a Pi would be nice because of the small form factor and the GPIO connectors.

So, if there are any RPi enthusiasts reading, what do you think?  

- Is there a cheap way to get up and running with the Pi, or am I right that it's going to take $50 - $60 in accessories to get going?
- Is there something really cool/educational we could be doing with the Pi that we can't do with a spare PC or an Arduino?
- Any other thoughts??

---

### Post by papibe on 2013-11-18
Hi  lykwydchykyn.

I have one running [raspbmc]("http://www.raspbmc.com/"), and working as a HTPC.

I barely have made any extra expense since:
[LIST]
[*]I use my tablet charger as a power supply (Nexus 7).
[*]I use a wired connection (ethernet).
[*]I use no case (I blow compressed air over it as often as I can).
[*]I use a TV as a monitor.
[/LIST]
Regards.

---

### Post by Iowan on 2013-11-18
I have a couple of Pi's. I did the Model B. eBay for cable/adapter/power supply. I had a USB keyboard/mouse combo (Pi has two USB sockets)  and don't need Wifi on it yet. Mine is a bit prone to hang - dunno if the SD is not completely stable (Sandisk Ultra - Class 10), but after the first re-format/reload, I put Arch on it instead of Raspian. It's a bit trickier (for me) to get other stuff loaded onto Arch. Either Raspian came with xrdp, or i installed it - then I didn't need the monitor or keyboard... although a bit more sluggish. I also bought kits to play with the GPIO. I've used the 8in/8out card, built (but not tried) the stepper motor, and still haven't assembled the 32 I/O expander.

I also have a couple of BeagleBone Blacks that I haven't had a chance to use very much. One came with a Debian image instead of the default Angstrom Linux, and the other has an Ubuntu image on SD - which can be copied to onboard eMMC. Somewhat faster processor, but only one USB port. The cable that comes with it generates a "USB eth0" - which doesn't work on the Debian BBB, although SSH via true ethernet port works. I haven't investigated "capes" to use the GPIO (many more than the Pi provides).

I don't have cases for any of them... although the BBB fits nicely into an Altoids tin.

---

### Post by lykwydchykyn on 2013-11-18
Thanks for the replies.  I guess some of those things I can do without, but the real killer for me right now is the VGA/HDMI thing.  Using HDMI isn't really a practical option for us, and the only converter I've found that works (according to reviews) is $24 -- nearly doubling the price right there!  

I guess I was hoping that there was something similar out there that used VGA output and cost less than (RPi + adapter), but I haven't been able to find anything.

Just thinking, if I have to spend $60+ I can get something a lot cooler and more educational than yet-another-linux-box.

---

### Post by Iowan on 2013-11-18
I bought a used monitor with DVI input for $10. Also got a HDMI cable for $10 (cheaper on eBay). HDMI-DVI adapter was ~$2.50. So, I got more hardware, but about the $24 price you mentioned. I've been using it to learn Python to control the GPIO. If/when I get the stepper card working, I may consider using a wireless adapter to build a robot. 
I suppose an Arduino could probably do much the same thing, ( I don't have any of those - yet) but this is as close to the hardware as I've been in ... decades.

I'm not trying to sell you one (or the other). I got tired of buying aging computers - intending to make them my next workstation/server. At least these don't take up a much room ;)

---

### Post by v1k1ng1001 on 2013-11-18
I remember reading an article about a year or so ago about different alternatives available to the raspberry pi.  You should hunt around for other options that might work better for you.

---

### Post by joyousjake on 2013-11-18
Just to say, $100 is still pretty cheap. And if he loses interest, use it as a server, or maybe hook it up to your tv and use it as your media player.

---

### Post by tgalati4 on 2013-11-18
I would take one of the old PC's and put plain Debian on it, then set up a bunch of services on it.  Measure the power usage with a Kill-a-watt meter.  Now challenge your kids to duplicate those services on a RaspberryPi and measure the power.  You go from 50-90 watts to 5-7 watts.  Running a server 24/7, the RaspberryPi will pay for itself in short order.  Have the kids do the cost calculations.

You are correct, The HDMI to VGA is expensive because it is a digital-to-analog conversion.  HDMI to DVI is digital-to-digital and much cheaper.  So find an old monitor with DVI or a cheap HDMI TV.  The analog video (yellow conector) is hard to program with because the resolution is poor.  It's OK for basic status or a simple front end for instrumentation.

You only need a powered USB hub if you are running USB hard drives.  Mice and keyboards run OK directly.  

I would like to know what cooler stuff you can buy for $60.

Most kids want to go directly into robotics--now that gets expensive.

---

### Post by lykwydchykyn on 2013-11-19
> **Iowan said:**
> I bought a used monitor with DVI input for $10. Also got a HDMI cable for $10 (cheaper on eBay). HDMI-DVI adapter was ~$2.50. So, I got more hardware, but about the $24 price you mentioned. I've been using it to learn Python to control the GPIO. If/when I get the stepper card working, I may consider using a wireless adapter to build a robot. 
I suppose an Arduino could probably do much the same thing, ( I don't have any of those - yet) but this is as close to the hardware as I've been in ... decades.


I think we've got one monitor that does DVI, so that's a possibility.  It could be swapped for a VGA if I needed to dedicate the DVI to a Pi.  We've done some things controlling the arduino using Python programs, but mostly by having python send serial commands to the arduino, and then writing a firmware thing on the arduino to translate the commands.  I have a feeling directly coding for the GPIO in Python is a little more fun.

> **v1k1ng1001 said:**
> I remember reading an article about a year or so ago about different alternatives available to the raspberry pi.  You should hunt around for other options that might work better for you.

Yeah, I tried to google up some of those articles.  All the articles I found showed boards that cost more and still used HDMI output. :(

> **joyousjake said:**
> Just to say, $100 is still pretty cheap. And if he loses interest, use it as a server, or maybe hook it up to your tv and use it as your media player.

Erm, yeah, $100 isn't cheap in my world, unfortunately.  Also I have loads of Linux boxen, like I said; I think we may have like, 8 Linux machines going in the house, and I only had to pay for two of them (the rest were given to me by friends/family/coworkers).  And those two I got off a gov't surplus auction at $65 each.  

Point being, you can see that dropping $100 to just have yet another Debian box (if that's all the Pi turns out to be for us) isn't the best use of funds.

> **tgalati4 said:**
> I would take one of the old PC's and put plain Debian on it, then set up a bunch of services on it.  Measure the power usage with a Kill-a-watt meter.  Now challenge your kids to duplicate those services on a RaspberryPi and measure the power.  You go from 50-90 watts to 5-7 watts.  Running a server 24/7, the RaspberryPi will pay for itself in short order.  Have the kids do the cost calculations.


That's a compelling point.  I don't know how these machines affect our electric bill (it isn't horrendous, but who knows?); I might buy myself a Pi just for that reason.  I'd hate to give it to my son just to abscond it for the family file server, though :).
> 
You are correct, The HDMI to VGA is expensive because it is a digital-to-analog conversion.  HDMI to DVI is digital-to-digital and much cheaper.  So find an old monitor with DVI or a cheap HDMI TV.  The analog video (yellow conector) is hard to program with because the resolution is poor.  It's OK for basic status or a simple front end for instrumentation.


That makes sense; I kind of figured the yellow output was not going to be a usable option.

> 
You only need a powered USB hub if you are running USB hard drives.  Mice and keyboards run OK directly.  


That's good to know; I think I'd read someone complaining about having problems with peripherals without a powered hub, but you know how the internet is.

> 
I would like to know what cooler stuff you can buy for $60.


I had in mind maybe an Arduino kit; you can get a pretty happening arduino starter kit for well under $60, with servos and sensors and whatnot.

> 
Most kids want to go directly into robotics--now that gets expensive.

Ain't it the truth?

---

### Post by 1clue on 2013-11-19
To me it depends entirely on what you want to use it for.  If you want another low-powered Linux box then I'd say no.  If you want a gadget controller for electromechanical experiments, then it seems to be about the cheapest way to get into that sort of thing, the arduino boards seem to be more expensive and MUCH more expensive when you start adding things that the pi already has.

I've been contemplating a pi ever since I heard of one, but for me the problem is time.

Doesn't the pi have a composite tv out as well?  You could find any old TV and hook it to the yellow RCA jack, right?

---

### Post by Bucky Ball on 2013-11-19
Yep, about AU$100 is right. Pi B model, powered hub, hdmi cable, sd card, this and that. Use it to watch catch up TV and stream vid and music from the other machines on the network. Works a treat, but sounds like you could do that with any number of setups you have easy access to by using recycled (which is a MUCH better idea than buying new stuff, for the planet, not just your wallet). 

We have it plugged into the TV in the living room and life wouldn't be the same without the little critter. As for educational stuff, I don't use it for that but LOTS of people do (surprised you're asking us about that aspect as there is tons of things to do with Pis on the interwebs). ;)

---

### Post by ssam on 2013-11-19
You might be able to find a retailer doing a starter kit, eg [http://www.microdirect.co.uk/Home/Search/Electronics/Raspberry-Pi/](http://www.microdirect.co.uk/Home/Search/Electronics/Raspberry-Pi/)

The raspberrypi is good at somethings but not everything. I use one as a music server, running MPD hooked up to my hifi, and another as a desktop machine that mostly just has terminals ssh'ed to big computers. I have also used them to run video loops on screens at events. I would not want to use one as my main desktop, though it may get a lot more practical if they get a wayland based DE going.

They are also good for embedded projects where you need more CPU power than you can get on an arduino. Also good for having something that is cheap enough to not worry about it breaking.

If you are interested in learning electronics then an arduino is worth looking at. If you want something that will make a more useful desktop, then there are a few other arm boards, often with a dual core armv7 (several times faster than the armv6 in the raspberrypi).

---

### Post by Dragonbite on 2013-11-19
> **lykwydchykyn said:**
> Thanks for the replies.  I guess some of those things I can do without, but the real killer for me right now is the VGA/HDMI thing.  Using HDMI isn't really a practical option for us, and the only converter I've found that works (according to reviews) is $24 -- nearly doubling the price right there!  

I found one for $5 in Amazon ([BestDealUSA HDMI Input to VGA Adapter Converter For PC Laptop NoteBook HD DVD]("http://www.amazon.com/dp/B007PLL4CK/ref=wl_it_dp_o_pd_nS_ttl?_encoding=UTF8&colid=26MAAKTAKD6VG&coliid=IZ7RTOQ0Y8LL9")).  Here is an Amazon search result [list]("http://www.amazon.com/s/ref=sr_kk_3?rh=i%3Aelectronics%2Ck%3Ahdmi+to+vga+converter&keywords=hdmi+to+vga+converter&ie=UTF8&qid=1384871009"), seems plenty to choose from unless I am looking at this wrong.

> **lykwydchykyn said:**
> 
I guess I was hoping that there was something similar out there that used VGA output and cost less than (RPi + adapter), but I haven't been able to find anything.

Just thinking, if I have to spend $60+ I can get something a lot cooler and more educational than yet-another-linux-box.

I am looking at trying to get a Raspberry Pi and fool around with it, plus use it in a few instances if I can manage it. I too an often a recipient of old machines and Linux is great way to breathe new life into them.

One of the things I like is that, unlike traditiional CPUs, the electricity requirements is much less so it shouldn't impact my bill much. Plus with no fans it should be completely silent (even my quiet CPUs get noisy if you are looking for peace and quiet).

I think part of the appeal, beyond cost, is the flexibility of placement.  I read somebody took one of those portable solar chargers and was able to use that to run the RP, or could use batteries.  Be really cool to set it up to a laptop battery and plugged in so if power goes out the laptop battery kicks in until power is restored.

Some of my project ideas I may or may never get to:
[LIST]
[*]**Backup Server : **connect a USB hard drive and use it as a backup server pulling from the existing NAS server (a backup server of the network server)
[*]**Upload Server : ** connect to shared drives (dropbox, copy.com, spideroak, etc.) so that the client drops files into the appropriate folder (which runs quick on the local network) and it uploads everything to the cloud storage while I can do whatever else I want on my system (even shut it down)
[*]**Web server** (I know.. boring :) )
[*]**Firewall Server : ** Add a USB network and connect between the modem and the wireless router. If possible include content filtering (Dans Guardian).  
[LIST]
[*]Take the modem, RP firewall and wireless router and place on a UPS so if the power goes out we have some time the laptop is still connected until batteries run out
[*] Set up as a wireless router to replace the above mentioned router so if the power goes out the batteries last much, much longer
[/LIST]
[*]**Wireless Repeater : **, can put this just about anywhere (tempted to put one out in the barn so my wifi reaches the hammock! :lolflag:
[*]**Print server : ** for older non-networked printers
[*]**Surveillance Cam : ** attach webcam(s) to it and hang it out in the barn so that it dolls out cam shots and I can sneak a peek without going out there in the cold to check on the horse
[*]**Bridge : **I run the computers at our church auction and currently my laptop connects to the public wifi and bridges that connection to a (wired) router which everybody working on my software connects to.  Be great to set up a RP, possibly using batteries instead of plugging in, so I can place it where it can get the best connection and run the wire to the router to extend it.
[*]**Browser anywhere : ** Chromebook-like setup (just a browser) so that can set it up in places used infrequently
[*]**3D Printer : ** to handle 3D printing.. of course I have to get a 3D printer first...
[/LIST]

Of course, first I have to get one

---

### Post by Dragonbite on 2013-11-19
Just ran across this : [iTunes Server on Raspberry Pi]("http://misapuntesde.com/post.php?id=314&lang=en")

---

### Post by lykwydchykyn on 2013-11-19
> **1clue said:**
> To me it depends entirely on what you want to use it for.  If you want another low-powered Linux box then I'd say no.  If you want a gadget controller for electromechanical experiments, then it seems to be about the cheapest way to get into that sort of thing, the arduino boards seem to be more expensive and MUCH more expensive when you start adding things that the pi already has.

I don't know where you've been looking for arduinos; I've found Uno R3 clones for as little as $10.  And all you need to program an Arduino is a USB cable and some kind of PC (I have a celeron 800 system running Debian that I dedicate to the task of Arduino programming).  I bought my current one as part of a kit for ~$60, included a breadboard, project shield, tons of components, wires, sensors, etc.  Just bought another kit on sale for my second son; it was under $30, included an Arduino Mega (clone), servos, IC's, wires, breadboard, etc.  

They're kind of apples and oranges, though; I can see your point about adding things like networking or storage to the arduino, but that's not really the point of the arduino (at least for us).  I'm not really waffling between the two as a question of features, but rather as a question of educational or practical investment.

> 
Doesn't the pi have a composite tv out as well?  You could find any old TV and hook it to the yellow RCA jack, right?

Very low res.  Not good for programming, from what I understand.  Might take me back to the days of TI-BASIC and Parsec, I guess :D.


> **Dragonbite said:**
> I found one for $5 in Amazon ([BestDealUSA HDMI Input to VGA Adapter Converter For PC Laptop NoteBook HD DVD]("http://www.amazon.com/dp/B007PLL4CK/ref=wl_it_dp_o_pd_nS_ttl?_encoding=UTF8&colid=26MAAKTAKD6VG&coliid=IZ7RTOQ0Y8LL9")).  Here is an Amazon search result [list]("http://www.amazon.com/s/ref=sr_kk_3?rh=i%3Aelectronics%2Ck%3Ahdmi+to+vga+converter&keywords=hdmi+to+vga+converter&ie=UTF8&qid=1384871009"), seems plenty to choose from unless I am looking at this wrong.


Initially I saw those two, but as I started reading the reviews I noticed that many people had problems using them with the RPi.  Some threads on the RPi forums suggested that you needed a special powered adapter, and the "certified" adapter is $24.


So basically my takeaway is that, compared to a recycled PC, the RPi gives me lower power consumption, smaller footprint, and GPIO pins; that I can probably get a working setup for around $50 using things I already have; and that it might be a better gift for Dad than the kids at this point :).

---

### Post by Dragonbite on 2013-11-19
Thanks for the heads-up on the HDMI - VGA adapter!  I'll have to keep that in mind if I get a Raspberry Pi.  I did hear the power adapter can be finicky, though.  

For more money there is [Beagle Bone]("http://beagleboard.org/Products/BeagleBone")

---

### Post by Dragonbite on 2013-11-19
[openSUSE on RaspberryPi with ownCloud]("https://dragotin.wordpress.com/2013/11/19/opensuse-on-raspberrypi-with-owncloud/")

---

### Post by mamamia88 on 2013-11-20
Mines collecting dust in a drawer so I would vote for no.    Get a used pc on ebay or craigslist and you'll be much happier.

---

### Post by tgalati4 on 2013-11-20
I have both an arduino and a raspberrypi on my workbench.  I'm still fiddling with both and finding a home for each.  One will probably be a koi pond monitor with warning text messages for out-of-bounds conditions--protecting 200 fish in a 7,000 gallon pond.  The other will probably interface with a home alarm system sending out text messages in place of the analog phone modem dialer.

I also have a project for using the Pi for amusement park trams and mp3 announcements based on GPS coordinates with WiFi to automatically update announcement packages throughout the day.  I have the system working on a microATX platform, but it uses 12 watts and is 8"x8"x3", so shrinking it to a Pi would reduce power and the size of the weatherproof enclosure.

A quick web search will find all kinds of projects.  How about a kitchen warning system:  temperature monitor behind the oven and dryer, overtemperature of the refrigerator (by reading the thermistors  on the control board), water leak detection under the washing machine, sink and dishwasher.  One arduino with networking could provide this protection and avoid costly repairs or fire.

---

### Post by RoyLongbottom on 2013-11-21
[FONT="Verdana"]At least after setting up, you have another PC,  and don’t need GUI access, you can boot and execute RPi terminal commands from a PC or laptop, after installing Putty.RPi directories and files can also be manipulated via the network.[/FONT]
[FONT="Verdana"] [/FONT]
[FONT="Verdana"]Using a cheap unpowered USB hub, USB flash drives and powered hard disks can be used at the same as keyboard and mouse.[/FONT]
[FONT="Verdana"] [/FONT]
[FONT="Verdana"]The RPi is useful for learning, compiling and running programs. I have compiled and run a series of benchmarks  using C/C++, Java and OpenGL ES, mainly with minor changesto my Linux (Ubuntu) versions. Benchmarks, results and source code (FREE) are available via the following.  [/FONT]
[FONT="Verdana"] [/FONT]
[FONT="Verdana"][http://www.roylongbottom.org.uk/Raspberry%20Pi%20Benchmarks.htm](http://www.roylongbottom.org.uk/Raspberry%20Pi%20Benchmarks.htm) [/FONT]
[FONT="Verdana"] [/FONT]

---

### Post by joyousjake on 2013-11-25
Another thing is portability. Go visit grandparents, connect it to their tv, and work on a desktop (albeit slow), rather than some dumbphone.

---

### Post by lykwydchykyn on 2013-11-25
Just a follow up.... I decided not to do the Pi (yet).  After talking with my son about his level of interest in the Pi, it seems to come mostly from a desire to run minecraft Pi edition.   This, plus the fact that we just got him a refurb laptop for his birthday (he put Lubuntu on it, runs great), means he's less motivated about the Pi.  

Don't fear, though, I got him something just as cool and geeky.

I'm also still interested in setting up a Pi to replace my energy-guzzling old P4 server.

---

### Post by JRV on 2013-11-25
> **lykwydchykyn said:**
> 
- Is there something really cool/educational we could be doing with the Pi that we can't do with a spare PC or an Arduino?


I hooked up a 8x8 led matrix to an RPi and programmed a multiplexer in a second thread.

This won't work on an Arduino for three reasons:

It needs 16 digital pins, the Arduino has 14, and the RPi 21.
The Arduino can not run a multi-threaded program.
The RPi is no hot rod, until you compare it's 700 MHz to the Arduino's 16.

To be fair to Arduino there are things an Arduino can do that the RPi can not.
Most notably the RPi does not have an analog to digital converter onboard,
while the Arduino has 6 analog input pins.

---

### Post by help_me2 on 2013-11-25
I use my Pi for OpenElec (XBMC media center) and absolutely love it. You get over 250 internet "TV" stations to choose from, and never get tired of watching it. I have easily spent over $100 dollars for accessories and whatnot. I put heatsinks on the Pi, and overclocked it to 900mhz. With heatsinks and one of those little USB powered fans blowing on it, you could easily get to 1000mhz and make it a little more snappy. 

If you install the NOOBS package at the start, it will allow you to multi-boot several OS's like arch, debian, XBMC, fedora, etc....... If you get a Pi, here are a few things I can I highly recommend: 
[list]
[*]Powered USB Hub 
[*]MicroUSB power supply
[*]USB Powered fan
[*]Wireless mini keyboard/trackpad combo 
[*]Acrylic case w/open sides for good airflow 
[*]Heatsinks
[*]And any good quality Class 10 SD card.[/list]

Enjoy!

---

