---
title: "Hardware advise needed"
date: 2008-12-28
forum: Server Platforms
---

### Post by DoppyNL on 2008-12-28
Hi,

I need some advise on what hardware to pick for a new home server.

I want to do the following with the home server:
[LIST]
[*]run lamp
[*]run samba
[*]copy backup over DSL-line to other locations (using rsync)
[*]download from newsgroups (hellanzb) (in the background)
[*]burn iso-dvd's
[*]NO X-system (pure server)
[*]maybe run mp3's directly on the server via the soundboard to my hifi-set
[/LIST]

What advise can be given on:
[list]
[*]64bit vs 32bit processors
[list]
[*]Will I run into problems using 64bit? (ie: programs not working or more difficult to install)
[*]How big is the performance difference? is it worth it for a home server?
[/list]
[*]How much memory? some people say more then 2GB in a 32bit system is useless.
[/list]

On top of that, can any advise be given on:
[list]
[*]What processor best be used?
[*]What barebone best be used? or do it completely different?
[/list]

If you can direct me to some place where I can find this information, please do.

Tnx in advance.

---

### Post by HermanAB on 2008-12-28
You don't need much for that - an Eee PC 701 will do fine!

So, you could easily build a Google 'cookie tray' server for a couple hundred dollars.  It is X11 that takes resources.  Other things are limited by the internet network speed, which is slooooooow.  Therefore a mail, file or web server doesn't need much horsepower.

Cheers,

Herman

---

### Post by DoppyNL on 2008-12-29
So clearly, a 64bit processor is over the top for this situation. For educational purposes (and for other people who might end up in this thread later):

[list]
[*]Will there be problems when I use a 64bit processor and I want to install software? Or is that exactly the same as 32bit?
ok, the repository's are there to use, but are those for 64bit smaller?
[*]Is it useless to put in 4GB of memory in a 32bit system? (as I've heard)?
[/list]

tnx!

---

### Post by gtdaqua on 2008-12-29
32-bit Systems can max read 4GB (A single app windows can access only 2GB of memory space). If your apps want to have more than 4GB, then seriously consider 64 bit. Its possible to read more than 4GB in 32bit but I won't recommend that in your case.

64-bit on the server side enjoys better support than 64-bit desktop. Most of the processors released today are 64-bit capable ensuring scalability. 64-bit is the future. Even MSFT will release their Win 2008 Server R2 in 2010 in 64-bit only forcing developers to move away from 32bit and its limitations.

You will be able to see a small difference in performance on a 64bit 4GB machine compared to a similar 32bit machine.

You can consider AMD Quads which are relatively cheaper than the Intel Quads. Intel's Penryn Quads are actually double dual-core and not true quads. But the latest models are better (but costlier) than AMDs in terms of performance.

---

### Post by DoppyNL on 2008-12-29
Thanx for the reply. That's very clear! :)

Anyone can draw conclusions on that on what hardware should best be used.

---

### Post by volkswagner on 2008-12-29
I am a fan of going green.  Considering the machine will run 24/7, power consumption=heat and $.

I would consider at a minimum a 35-45 watt cpu, single or dual core.

I like the Intel Atom setup.

It is very capable for a headless server.  It will run 64 bit Ubunutu 8.04.1 out of the box.

I have this [board]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813121359") and still setting it up.  Others have it running.

It is a great basic setup.  If you want raid, you will need an add on card, or look elsewhere.

---

### Post by McLogic on 2008-12-29
All of these products use the latest technologies to save power. As this is a server, you don't need to pay attention to [the x4500HD graphics problems.]("http://ubuntuforums.org/showthread.php?t=889323")

[list]
[*] Do not fill your case with fans, just use one or two big & slow fans.
[*] Do not get a huge power supply, as supplies are most efficient at 60-85% output.
[*] A motherboard with on-board video will save money and power. (Intel G43 or G45 are good for this.)
[*] A motherboard with on-board gigabit will save you money and power vs an add-in card.
[*] DDR3 sticks that run at 1.5 volts will save you power.
[*] Any Core2 will have plenty of speed, and 45nm will use less power.
[*] Do NOT overclock, it really increases the power used by the system.
[*] Hard drives do not need cooling, if they have open slots above and below them.
[/list]

I assume that you have a case around the house (most people do). I would buy this mix for $540 (USD):
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813182161](http://www.newegg.com/Product/Product.aspx?Item=N82E16813182161)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115132](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115132)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820134792](http://www.newegg.com/Product/Product.aspx?Item=N82E16820134792)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136151](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136151)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817379008](http://www.newegg.com/Product/Product.aspx?Item=N82E16817379008)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16827106263](http://www.newegg.com/Product/Product.aspx?Item=N82E16827106263)


People say that the **64-bit speed question** is a wash if you have 4 gb or less of RAM. The Intel chips turn off the loop unrolling and macro-op fusion when they run in 64-bit mode. This negative, along with less efficient cache usage, counteracts the speed increase of the increased register file.

---

### Post by shizakapayou on 2008-12-29
I just built a new home server running Server 8.04.1, using the Atom board as shown a few posts up.  The total list:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813121359](http://www.newegg.com/Product/Product.aspx?Item=N82E16813121359)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820145180](http://www.newegg.com/Product/Product.aspx?Item=N82E16820145180)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16811154091](http://www.newegg.com/Product/Product.aspx?Item=N82E16811154091)

Total comes to $150 plus hard drives, which I already had on hand - I used a 5400RPM laptop SATA drive for everything but /home, and a larger SATA drive for /home.  Very little/no heat, no noise.  It's currently running Samba and NFS as a file server to my home machines - I keep all my music, documents, etc. on a server and play from there.  In addition, I ripped a few DVDs to it last night and streamed to my Xbox running XBMC - the server works great.

It doesn't sound like you'll see much load unless the LAMP stuff is for a public website.  I'd highly recommend the Atom board if light load is the case.

---

