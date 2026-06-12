---
title: "Home file server - power consuption"
date: 2009-08-31
forum: Server Platforms
---

### Post by sir_jct on 2009-08-31
Could anyone please advise me on choosing secondhand hardware to configure a HOME MEDIA/ FILE SERVER?
As it will be an always-on server my main consideration, is that it must use as less power as possible.

ANY ADVICE WOULD BE GRATEFULLY RECEIVED.

---

### Post by gareththered on 2009-08-31
What about getting hold of an old laptop?  I have two running in my house at the moment one as a router and the other as a file & print server.

---

### Post by ugm6hr on 2009-08-31
In the UK, Viglen do an £80 box (using an Ubuntu UK podcast offer) which takes comes with a 40GB 2.5" drive.

[http://www.viglen.co.uk/webmail/5star-offers.html](http://www.viglen.co.uk/webmail/5star-offers.html)

Perfect for low consumption, but limited to 1 internal HD (and multiple USB ports for external).

---

### Post by armandh on 2009-08-31
nslu2 ?

[http://www.nslu2-linux.org/](http://www.nslu2-linux.org/)

or any Intel-atom board with 10/100/1000 lan

---

### Post by bartos on 2009-08-31
I use a Shuttle KPC K45. Added a $50 chip,$20 memory and a 1TB drive. It uses 30 watts idle and is rated for 100 watts. It is on 24/7. Perfect little machine that is expandable a bit.

---

### Post by hessiess on 2009-08-31
For lowest power consumption, look for something ARM based like the Beagleboard.

---

### Post by flatland2d on 2009-08-31
I recently built a desktop to run as a headless server.  It has:

AMD Sempron Sargas 140 45W CPU
2GB RAM
(2) 1TB Western Digital Green SATA-II Hard Drives, low power (one storage, one rsync'ed to the first)
(1) 100GB Western Digital IDE Drive (Ubuntu 9.04)
(2) 120mm fans, (1) 90mm fan

It uses 82 watts at idle.  Could be lower, but that works out to $1.47 per week in electrical cost.  Trying to go for anything less would not be very noticeable, except over the very long term.  The CPU heatsink is cool to the touch, and the exhaust fans blow out room temperature air.

---

### Post by ugm6hr on 2009-09-01
> **flatland2d said:**
> It uses 82 watts at idle.

For a home file server, this is not efficient.  The device I suggested uses under 10W.  Something ARM-based would be even better.  However, since the OP asked for second-hand advice...

Even my P4, 2xIDE HD standard desktop that I use runs at 55W for bootup and 30-35W the rest of the time.

For overall value for money and a healthy carbon footprint (and general green-ness), I would suggest looking for an old P3/P4 with 256+ MB RAM that someone would be prepared to give you for free (freecycle is a good site).  Add FreeNAS (on a USB stick - see the link below), and you have a completely free server that is fully-featured.  Remember, 2 HDs are generally a good idea for backup reasons.

---

### Post by TwiceOver on 2009-09-01
> **ugm6hr said:**
> For a home file server, this is not efficient.  The device I suggested uses under 10W.  Something ARM-based would be even better.  However, since the OP asked for second-hand advice...


82w is fine.  Chances are other "vampire" electronics are using up more than that on a regular basis.  Also the device you suggested is pretty much worthless for doing anything besides very basic sharing.  1x2.5" drive space?  That's pretty limiting.  Start chaining on USB enclosures and that 10w will quickly jump.

Unless you live in some state/country that has ridiculous power costs (Calisuckia) then I wouldn't worry too much about power consumption/cost.  The 82w mentioned above would be about $2.50/mo for me which I can easily recoup by not buying a soda at the gass station.

Just to add some suggestions.  ugm6hr's suggestion of using an older P4 setup is good.  The problem here is to make sure you know what you are getting.  A system with older DDR1 ram is going to get costly if you ever need more memory.  Also some older systems may not have SATA ports for drives.  I've seen very few IDE drives (possibly none) above 750gb.

If you are willing to throw some money at this.  I would go Intel Atom 330 (or better dual core if there is one now).  Some sort of case that can hold multiple hard drives (Since I have a rack at home I liked the Norco RPC-230).  Then slap in the drives that you want.

---

### Post by flatland2d on 2009-09-01
> **ugm6hr said:**
> For a home file server, this is not efficient.  The device I suggested uses under 10W.  Something ARM-based would be even better.  However, since the OP asked for second-hand advice...

Even my P4, 2xIDE HD standard desktop that I use runs at 55W for bootup and 30-35W the rest of the time.

For overall value for money and a healthy carbon footprint (and general green-ness), I would suggest looking for an old P3/P4 with 256+ MB RAM that someone would be prepared to give you for free (freecycle is a good site).  Add FreeNAS (on a USB stick - see the link below), and you have a completely free server that is fully-featured.  Remember, 2 HDs are generally a good idea for backup reasons.

The point is, the cost is so little, is it even worth making a contest out of who can build the lowest power computer?  Use common sense, but there is no need to engineer more hassle to save a couple bucks extra.  The OP mentioned he also wanted it to be a media server.  My server can transcode video in real time to my PS3.  It also has enough resources to handle anything else I throw at it someday, and it not limited to just file sharing.

You may want to check your wattage numbers again.  Most P4 processors I've seen uses at least 80W.  Even the latest super low power ones are 35W.  Factoring in inefficiencies of the power supply, power usage of the hard drives, motherboard, and all other associated electronics, and your processor must be running on practically nothing.

---

### Post by Hal58 on 2009-09-02
My primary server for Mail files (Sylpheed), Music repository (flac) and pictures (album art and photos) is a Koolu (Geode CPU, 512MB RAM) with an external 2.5" 250 GB Sata drive on a USB adapter.  A 300x Compact Flash on an IDE adapter internally holds the OS.  Most of the time I remotely mount files on the server with sshfs and transfer over a 100BaseT wired lan at around 4 MB/s.  OS is Ubuntu 8.04 Server.

 Power consumption ranges from 9-11 watts depending on activity.

I am preparing another server using an Everex Cloudbook (Via C7M CPU, 1GB RAM) with Wifi, camera and battery removed since the network core is already on an UPS.  The internal HD has been replaced with an 8GB 300x CF on ZIF IDE adapter and files to be served will be as on the Koolu.

 Preliminary power consumption is 8-11 watts in normal use falling to 7 watts idle with the LCD blanked.  With the C7M scaling the CPU speed from 800 MHz to 1.2 GHz, the idle power consumption really falls.

---

### Post by Whiffle on 2009-09-02
I'm using a dell dimension 4100.  It has a 866 mhz p3.  Runs 2 printers, hosts a website, and runs a backup system.  I measured it pulling about 50 watts.  I'd probably use something lower powered, but considering this was free...I'll use it.

---

### Post by danielgroves on 2009-09-02
I use an old IBM x61s laptop.  Does the job perfectly with it's 160GB HDD, 1.6GHz Core2Duo and 2GB RAM.

---

