---
title: "Debian Vs Ubuntu for a Server"
date: 2009-12-02
forum: The Cafe
---

### Post by Warpnow on 2009-12-02
So, I'm planning to buy an older PC and turn it into a small webserver running webmin, apache, ssh, and probably mysql. I'm probably going to be buying an athlon era computer if I can, so I might be limited on ram. 

I figure it will be very similar running the two as a server, does anyone know any notable advantages/disadvantages? Also, which version of debian would you reccomend I try out for a server?

---

### Post by -grubby on 2009-12-02
If you run Ubuntu server, you won't get packages that are 90 years old.

---

### Post by Grenage on 2009-12-02
Debian is generally more stable, but there isn't much in it.  We've had pure debian and ubuntu servers, both have been as reliable as each other.  Ubuntu is just a bit more *bleeding edge*.

---

### Post by cascade9 on 2009-12-02
> **-grubby said:**
> If you run Ubuntu server, you won't get packages that are 90 years old.

You mean ubuntu 8.04 LTS? I wouldnt count the non-LTS versions as that similar to debian stable. Currently, Debian Stable (Lenny) is pretty much the same as 8.04 LTS.  Lenny has some things newer, LTS has other things newer. 

Of course, when 10.04 LTS comes out that will all change, but right now there not much difference between them. 

@Warpnow- I'd go with debian stable myself. I've used a few versions of Debian, and a few ubuntus,and on one machine 8.04 LTS was very unstable, when Lenny (and Etch when it was stable) runs OK. Of course, thats just one machine, so its not enough of a sample size to mean much.

BTW, I use debian for desktop use, I'm biased ;)

---

### Post by -grubby on 2009-12-02
> **cascade9 said:**
> You mean ubuntu 8.04 LTS? I wouldnt count the non-LTS versions as that similar to debian stable. Currently, Debian Stable (Lenny) is pretty much the same as 8.04 LTS.  Lenny has some things newer, LTS has other things newer. 

No, I meant 9.10. Running a non-LTS version on a server is fine. At least, this guy's kind of server.

---

### Post by fromthehill on 2009-12-02
> **Warpnow said:**
> So, I'm planning to buy an older PC and turn it into a small webserver running webmin, apache, ssh, and probably mysql. I'm probably going to be buying an athlon era computer if I can, so I might be limited on ram.
I don't know what your budget is but maybe it's a better idea to look at something like this [intel itx-board ]("http://www.mini-box.com/Intel-D945GCLF-Mini-ITX-Motherboard")

it's probably uses a lot less power (20-30watts with 2 hdd's)

I'm using a server with a celeron 220 at 900mhz with apache ssh vnc mysql torrent, ftp without problems

---

### Post by cascade9 on 2009-12-02
> **-grubby said:**
> No, I meant 9.10. Running a non-LTS version on a server is fine. At least, this guy's kind of server.

Fair enough. I would avoid 9.10 for servers, but if you think that the OP is fine with that, OK. I think that LTS is closer to stable, and the other ubuntu releases are closer to debian testing, but thats an opinion, not a hard fact.

> **fromthehill said:**
> I don't know what your budget is but maybe it's a better idea to look at something like this [intel itx-board ]("http://www.mini-box.com/Intel-D945GCLF-Mini-ITX-Motherboard")

it's probably uses a lot less power (20-30watts with 2 hdd's)

I'm using a server with a celeron 220 at 900mhz with apache ssh vnc mysql torrent, ftp without problems

Not even close to 20-30 watts. Not for that board anyway, its using the old, power hungry 945GCLF chipset. The 945GC chipset uses 22watts on its own. More like 45watts idle with a single drive-

[http://upgraderguides.com/index.php?type=5&id=77&page=8](http://upgraderguides.com/index.php?type=5&id=77&page=8)

---

### Post by fromthehill on 2009-12-02
> **cascade9 said:**
> Not even close to 20-30 watts. Not for that board anyway, its using the old, power hungry 945GCLF chipset. The 945GC chipset uses 22watts on its own. More like 45watts idle with a single drive-

[http://upgraderguides.com/index.php?type=5&id=77&page=8](http://upgraderguides.com/index.php?type=5&id=77&page=8)
I use a board with a celeron 220 with 2x1tb hdd which uses 25-30 watt.

I figured an atom would use less power than that but I didn't know about the chipset. I've tested other atom boards which used 17 watts (with a 2.5"hdd)

It really makes a difference which powersupply you use. a pico-itx powersupply will use far less than a cheap atx powersupply

---

### Post by cascade9 on 2009-12-02
Yes, power supply will make a difference. I wouldnt be suprised if your talking DC watts and the test I posted was talking AC watts (from the wall). That would make, ohh, maybe 20-25% difference. See here- 40watts AC, 31 watts DC (estimated)-

[http://www.silentpcreview.com/article780-page3.html](http://www.silentpcreview.com/article780-page3.html)

BTW, just in case anyone is causally reading this, that silent PC review  test is on the Intel D201GLY2 board, running a Celeron 215 CPU (earlier version of what fromthehill has, its a 27 watt TDP and the celeron 220 is 19 watts).

---

### Post by fromthehill on 2009-12-02
> **cascade9 said:**
> Yes, power supply will make a difference. I wouldnt be suprised if your talking DC watts and the test I posted was talking AC watts (from the wall).
the 25-30 watt was measured directly from the wall;)
[this one]("http://www.filron.com/info/products.php?productid=316424&prodview=desc")

anyways. I tryed ubuntu-server and debian-minimal to create a webserver. didn't notice any difference (exept sudo isn't configured on debian)

---

### Post by Icehuck on 2009-12-02
It's a home server right? You could run Arch Linux for a server because in the end it doesn't matter. Take whatever you can work with the easiest and just go from there.

What about stability because it's a server? It's home use and you don't need any remotely close to mission critical 99.6%(or whatever) up time. If you were a business that demanded stability I would tell you to use SUSE Enterprise Server or RHEL for a server.

---

### Post by beniwtv on 2009-12-02
I would go with Ubuntu 8.04.3, I use it on multiple servers at work and at home as my home servers. No problems at all. Mainly we use it for the predictable release cycle - 5 years on servers.

And for the PC itself, I'd get a fit-pc2: [http://www.fit-pc.com/web/](http://www.fit-pc.com/web/)
Works really well, is fairly powerful (take the Atom  w/ hyperthreading model) and consumes 7W without the hard disk - may consume a little bit more with the HDD, not sure as I just used a USB HDD.

Cheers,

---

### Post by cascade9 on 2009-12-02
> **fromthehill said:**
> the 25-30 watt was measured directly from the wall;)
[this one]("http://www.filron.com/info/products.php?productid=316424&prodview=desc")

anyways. I tryed ubuntu-server and debian-minimal to create a webserver. didn't notice any difference (exept sudo isn't configured on debian)

Fair enough. I really wish there was a 'standard' for measuring power consumption, but thats for another thread, another time. 

@ beniwtv- nice looking little box, but wow, they are expensive here. $795 (490 eruo, $735 US) for the ubuntu model, with 160GB hdd! o.O 

[http://www.yawarra.com.au/catalogue.php?page=fit-pc2](http://www.yawarra.com.au/catalogue.php?page=fit-pc2)

---

### Post by beniwtv on 2009-12-02
> **cascade9 said:**
> 
@ beniwtv- nice looking little box, but wow, they are expensive here. $795 (490 eruo, $735 US) for the ubuntu model, with 160GB hdd! o.O

Yeah, I got mine from them directly, without HDD (can get one here for cheap) - and paid in dollars (Euros to Dollars conversion has it's benefits sometimes :p)

---

### Post by earthpigg on 2009-12-02
if it where me....

id go with ubuntu 9.04 for now. 2-3 months after 10.04 LTS came out, i'd do a fresh install of that and then not worry about it again until 2013.

---

### Post by LookTJ on 2009-12-02
To me, there''s no real differences between the two(exception of sudo). Both are great average servers.

However, if you are planning on large servers that potentially could get lots of visitors daily, I would recommend FreeBSD or some other *BSDs.

Enjoy! :)

---

### Post by Warpnow on 2009-12-02
If I were going to do ITX, I'd buy this:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16856119013&cm_re=dual_core_atom-_-56-119-013-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119013&cm_re=dual_core_atom-_-56-119-013-_-Product)

I'm not going to be setting up the server for a couple weeks. So I've got time to think. I've given the ITX (dual-core atom) alot of thought, but am still not sure. It comes down to how much I want to spend.

---

