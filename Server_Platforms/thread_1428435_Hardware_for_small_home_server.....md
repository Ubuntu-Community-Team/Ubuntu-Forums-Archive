---
title: "Hardware for small home server...."
date: 2010-03-12
forum: Server Platforms
---

### Post by ragtag on 2010-03-12
Hi,

  I'm looking to set up a small server at home with low power consumption and a small form factor. The plan is to mainly use it as a backup server for files, so it should have space for one 3.5" drive. There are a lot of different NAS solutions available, with some built in variant of Linux, but I would like to run Ubuntu server on mine.

  Do you know of some nifty hardware that might fit the bill? :D

---

### Post by Dayofswords on 2010-03-12
i use a old 350mhz dell, full size =p

---

### Post by srt4play on 2010-03-12
m350 enclosure + pico power supply + one of the mini-itx intel atom boards. 3.5" drive won't fit but if you don't have a lot to backup a large 2.5" drive should work.  I run this setup for an Asterisk server and it works great, makes for a nice low power server.

---

### Post by a.walker on 2010-03-12
You don't really need a whole lot of processing power to run a small home server. Hence, the above mention of a PIII; however, you might want to look into something that has low power consumption. If you're willing to work a bit with your hands, you can build a fairly inexpensive atom-powered desktop from parts on newegg. The amount of money that you save on your electric bill will at least partially offset the cost of the computer.  If you want something that's already put together you can check out the [Meerkat NetTop]("http://www.system76.com/product_info.php?cPath=27&products_id=91") at System76. It even comes with Ubuntu pre-installed.

---

### Post by Akita on 2010-03-12
Throw a gig or 2 of laptop memory, a SATA drive and a CF card in an MSI Wind barebones mini-desktop ([http://www.newegg.com/Product/Product.aspx?Item=N82E16856167032](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167032)). It has a CF slot on the motherboard internally that you can use as a boot+O/S drive. Set the HDD to spin-down in 5-15 min when not used. It's Intel Atom based and uses and external 65W brick like a laptop. Runs cool and uses less power than a dim lightbulb :-)

I've built several including a few using an adapter to put a 2nd drive in the CD bay to do RAID1 on /home (the HDDs). You can do one easily for < $200 and with a GUI-less Ubuntu on it, it will kick the *&^% out of just about every "toy" NAS box I've seen and be way more flexible and configurable.

---

### Post by Agent ME on 2010-03-12
A [SheevaPlug kit](http://www.globalscaletechnologies.com/p-22-sheevaplug-dev-kit-us.aspx) isn't very expensive, and uses very little power, and has a spot for a USB drive (a USB hard drive would be good). I think one of these would be completely perfect for a home server.

---

### Post by Letrazzrot on 2010-03-12
> **Akita said:**
> Throw a gig or 2 of laptop memory, a SATA drive and a CF card in an MSI Wind barebones mini-desktop ([http://www.newegg.com/Product/Product.aspx?Item=N82E16856167032](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167032)). It has a CF slot on the motherboard internally that you can use as a boot+O/S drive. Set the HDD to spin-down in 5-15 min when not used. It's Intel Atom based and uses and external 65W brick like a laptop. Runs cool and uses less power than a dim lightbulb :-)

+1 -- this is what I am currently using, so far works great.  I actually installed Ubuntu Server on a partition from a USB thumb drive.  It took me a couple of tries to get the thing to boot from the thumb drive, but other than that minor hurdle installation went without a hitch.

---

### Post by ushills on 2010-03-13
have a look at plugcomputer.org, you can connect usb drives to them and they use almost no power to run.

---

### Post by The Real Dave on 2010-03-14
Ubuntu Server will run on just about anything. My main server is a 1.7Ghz Pentium IV with just 384Mb of RAM. It's running NFS, Samab, SSH, rTorrent with about 10Gb of torrents loaded, Squid and Apt-Cacher-NG along with some other stuff. All that at 200Mb usage. You can see more about my servers, and pictures of them [here]("http://linuxexpresso.wordpress.com/hardware/")

What I would probably do is find a cheap laptop, install Ubuntu Server on it, and add extra drives through USB. Won't be the fastest, but it would be cheap and use very little power. 

You could also get a small case, and an Atom board. 

You might wanna have a look at some of the servers in the [Show Us Your Server thread]("http://ubuntuforums.org/showthread.php?t=334293&page=39") in the Cafe. Some of the servers there are just what your looking for :)

---

