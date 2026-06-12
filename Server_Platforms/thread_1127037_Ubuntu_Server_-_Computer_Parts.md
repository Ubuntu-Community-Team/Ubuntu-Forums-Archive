---
title: "Ubuntu Server - Computer Parts"
date: 2009-04-16
forum: Server Platforms
---

### Post by Spectre5 on 2009-04-16
I'm interested in building a new PC for a pretty simple server.  It'll just be used as a web/email/media server to host several pages (with very low traffic - probably no more than 2-3 people on any of the sites at any given time).  The server must be good/quick enough to serve up some embedded videos, run php, etc, etc...

Now I need to do this as cheaply as possible while getting a server that meets my needs (I'm hoping for <$200 for the 5 components I need).  I will install Ubuntu Server on it with no GUI.  Can anyone suggest some components?  I'd like it to be very quite and low power (on 24/7) and the smaller the better...

It does NOT need a monitor, mouse, keyboard, or any optical drives (I'll use an old one for installation only).  I also have an old power supply I can use (300W) - but may need a new one if using a SATA hdd.

The parts that ARE needed are (I think these are the only 5 I need?):
Case (smaller is better)
Motherboard (I'm thinking micro ITX maybe?  Must have on-board video and an ethernet port)
CPU
Hard drive (>= 320GB)
RAM (>= 2GB)


I think those are the only parts I need...I just need to make sure that the mobo has on-board video as well as an ethernet port...

So for a server - what is a good CPU spec to be looking at?  I'm thinking that it should probably be at least dual-core?  I've heard a bit about the VIA C3 and the Intel Atom (I know they aren't dual-core, yet) - what does everyone think of these for a server?  Should I aim for 2GB of RAM?  More? Less?  Is it important to use a SATA vs PATA hard drive for a server?

What other factors are important for a web/email/media server?  What other things have I not considered?

Thanks!

Edit:  Also, one of the websites will be a mediawiki

---

### Post by BkkBonanza on 2009-04-16
If you're not going to have much traffic then just about anything can be used. You certainly don't need 2GB if you're trying to save money. Why not just get a $10/mo vps account? It will work for everything you need and you can run it for 2 years before it's going to cost more - and if you include power costs then even longer probably. Really, people who need to run these server apps for commercial purposes don't put them in a box at home. You gain far more by having it in a datacenter - better bandwidth and reliability. You learn just as much this way as well. I used to have a server at home but I got tired of the noise 24/7. Just another option to consider.

---

### Post by Spectre5 on 2009-04-16
> **BkkBonaza said:**
> If you're not going to have much traffic then just about anything can be used. You certainly don't need 2GB if you're trying to save money. Why not just get a $10/mo vps account? It will work for everything you need and you can run it for 2 years before it's going to cost more - and if you include power costs then even longer probably. Really, people who need to run these server apps for commercial purposes don't put them in a box at home. You gain far more by having it in a datacenter - better bandwidth and reliability. You learn just as much this way as well. I used to have a server at home but I got tired of the noise 24/7. Just another option to consider.

I know what you mean about the sound...my current server is a VERY old and VERY loud computer that now has freezing problems which is why I want to replace it.  I'd definitely like one quieter, of course just about anything would be quieter.

I want to have my server at home instead of paying for one because it is fun for me to maintain.  I like to work with it and learn as much as possible - that is my primary reason for it (to learn about them).  I think I can do a lot more learning by having my own.  I'm definitely not running a business or anything from it (I'd definitely pay if I was doing that).  I just run a page for some documentation on some code of mine, a wiki, and then a test page.

So 2GB of RAM is overkill - I don't think I'd go with less than 1GB though.  What about the processor?  The ATOM is SUPER low wattage which is attractive, but it is rather slow and is not dual-core.  What does everyone think about this?  Is the VIA C3 better/worse than the ATOM?

Later tonight I'll post a few items that I was preliminarily looking at to get some opinions on it...in the meantime, are there any other ideas?

---

### Post by skintythe1andonly on 2009-04-16
There is now a dual core atom

[http://www.legitnonsense.com/?p=372]("http://www.legitnonsense.com/?p=372")

I saw a review in linux format for an Asgard shuttle X27 which is a book sized desktop that is supposed to be very quiet. This runs the dual core atom

---

### Post by Spectre5 on 2009-04-16
> **skintythe1andonly said:**
> There is now a dual core atom

[http://www.legitnonsense.com/?p=372]("http://www.legitnonsense.com/?p=372")

I saw a review in linux format for an Asgard shuttle X27 which is a book sized desktop that is supposed to be very quiet. This runs the dual core atom

Where can I find this Asgard Shuttle X27 for sale?  I don't see to get many hits on google, I can't find it on Newegg or several other common online retailers...

EDIT:  Sorry, never this comment of mine!

---

### Post by lavinog on 2009-04-16
MSI wind pc is a nice setup for a home server
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856167037](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167037)
Just need to add memory (laptop memory)
and a sata drive.
It has a built in CF reader on the mobo for running the os off of the CF card. (this is handy if you want your HD to sleep during inactivity)

It comes with a dc powersupply (like a laptop.)
It runs really silent

---

### Post by Spectre5 on 2009-04-16
> **lavinog said:**
> MSI wind pc is a nice setup for a home server
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856167037](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167037)
Just need to add memory (laptop memory)
and a sata drive.
It has a built in CF reader on the mobo for running the os off of the CF card. (this is handy if you want your HD to sleep during inactivity)

It comes with a dc powersupply (like a laptop.)
It runs really silent

Wow, that does look pretty sweet...thanks!  I'll definitely keep it on my list of options to explore further!

---

### Post by Spectre5 on 2009-04-18
Bump.  Any other suggestions?  Do people think that the dual core is not necessary for my purposes?  Maybe it would be better to just save the money and get a lower ATOM processor?

---

### Post by juancarlospaco on 2009-04-18
> **Spectre5 said:**
> Any other suggestions?  Do people think that the dual core is not necessary for my purposes?  Maybe it would be better to just save the money and get a lower ATOM processor?

[This one ]("http://system76.com/index.php?cPath=29")for Supporting Ubuntu.

:P   ;)

---

### Post by chrisstewart on 2009-04-18
It may give yourself room for expansion to use and 64Bit Intel Atom and lots of power for Domain Login and Diskless Workstations IP Tables, Samba Server, Apache. I have purchased a Intel Atom Mini-Itx Board from Direct Computer Canada for 78.90 and 2 gigs of memory with a Shuttle case it was just over 200.00 and has been running flawlessly for 3 months now routing a simple home network and I have two diskless PC's running using PXE Boot so I would say its worth while and very affordable. Plus its only a 100watt power supply so its very GREEN

[http://www.directcanada.com/products/?sku=12200BD8483&vpn=BOXD945GCLF&manufacture=INTEL](http://www.directcanada.com/products/?sku=12200BD8483&vpn=BOXD945GCLF&manufacture=INTEL) 

Take it easy Chris

---

