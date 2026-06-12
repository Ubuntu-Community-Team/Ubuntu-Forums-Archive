---
title: "Recommend a solid LTSP-compatible thin client"
date: 2010-10-06
forum: Server Platforms
---

### Post by lykwydchykyn on 2010-10-06
I've gotten approval for funding to get new thin clients for my LTSP setup since the current clients are too underpowered.  It seems like no thin client manufacturers want to actually tell you what hardware is in their clients though.

We acquired one of the few available from our regular vendors, a Wyse C50LE, but it's horrid with Ubuntu LTSP.  It uses a via graphics chip that doesn't work with the openchrome drivers and requires me to install the proprietary driver from via's website.  I'm not too optimistic about the future of via graphics support in the linux kernel either.

So, I need a recommendation.  My requirements are:
 - Graphics chip with solid Xorg support
 - compact formfactor (can't be much bigger than a VHS tape)
 - Not used/ebay/craigslist 
 - price ballpark about $350/unit or less

Anyone?

---

### Post by lykwydchykyn on 2010-10-07
bump.

---

### Post by druhboruch on 2010-10-07
How about Zotac Zbox?

[http://www.newegg.ca/Product/Product.aspx?Item=N82E16856173005&cm_re=zbox-_-56-173-005-_-Product](http://www.newegg.ca/Product/Product.aspx?Item=N82E16856173005&cm_re=zbox-_-56-173-005-_-Product)

---

### Post by lykwydchykyn on 2010-10-07
> **druhboruch said:**
> How about Zotac Zbox?

[http://www.newegg.ca/Product/Product.aspx?Item=N82E16856173005&cm_re=zbox-_-56-173-005-_-Product](http://www.newegg.ca/Product/Product.aspx?Item=N82E16856173005&cm_re=zbox-_-56-173-005-_-Product)

Have you used this with LTSP?

---

### Post by druhboruch on 2010-10-08
I don't run LTSP anymore.
I use Zotac as my STB and I run XBMC on it.

It is designed to be a thin client.  It comes with the bracket to attach it behind your screen.

You may find more info about this device on xbmc forum (thread in the hardware section)  and there is a review on xbmcfreak's website.

There is also a video on youtube.

If I run LTSP, I would be my first choice.
Here I sound like a sales guy:)

---

### Post by lykwydchykyn on 2010-10-10
cool.  Thanks for the info!

---

### Post by lykwydchykyn on 2010-10-18
bump; we're going to try the Zotac, but I'd like to hear from some more people if that's possible.

---

### Post by steamboatsailor on 2010-11-01
I have an Zotac Zbox, ZBOXSD-ID10-E. It works out of the box with Ubuntu 10.4 but I got problem using LTSP (based on Ubuntu 10.4).
I got an white screen instead of ldm-greeting. In this [tread]("http://ubuntuforums.org/showthread.php?t=1603894") I got it working on one of my LTSP-servers but when moving the Zbox to another machine I got stuck in the white screen problem. 
I havn't found out why but I guess that it is something  with screen resolution...

It's a nice machine but it has an cpu-fan so it's not the absolute silent client that I wish it was.

---

### Post by arnavk007 on 2010-11-01
I think you should go to disklessworkstations.com

---

### Post by lykwydchykyn on 2010-11-01
I installed a zotac for testing on friday.  So far it's working well but I had to manually specify the "nv" driver to make video work.  The auto-detected driver (I'm guessing nouveau) didn't work.

---

### Post by lifeboy on 2010-11-24
We use [http://bdsolutions.co.za/ebox/](http://bdsolutions.co.za/ebox/)

It didn't work with Jaunty (we had stay with Intrepid) due to some graphics problem, but it's works faultlessly with Lucid and now Maveric.

There are various processor options and configs.

Go have a look.

---

### Post by lykwydchykyn on 2010-11-27
Which model ebox did you use?  They look like they have the via Unichrome graphics chip, which is what was so problematic on the Wyse clients.

---

