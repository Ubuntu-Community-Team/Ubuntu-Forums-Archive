---
title: "build a little home webserver"
date: 2009-07-28
forum: The Cafe
---

### Post by cazz on 2009-07-28
Hello.

I have search here and over the internet about what I can use as a server at home.

I was thinking about use ubuntu and have Apache2 with MySQL and PHP. and a FTP server.
I going even have a SSH server to make it easy to maintain the server.

I going to try to have it on 24/7 and I live in a small flat so I dont like to to take alot of space and I dont want to hear it.

After I have search here and the internet I found two machine 

a fit-pc ([http://www.fit-pc.com/fit-pc1](http://www.fit-pc.com/fit-pc1))
I have even see a fit-pc2 but I dont know anything about it and what is going to cost.

Here I find an another machine name NSLU2 ([http://www.linksysbycisco.com/US/en/products/NSLU2](http://www.linksysbycisco.com/US/en/products/NSLU2))

it is cheap but a NSLU2 is not original design for use as a server so I dont know if I'm so good to create one for my needs.

so right now I have no idea what to do.


**/Update**

the fit-pc2 is more powerfull and I can buy it from the homepage ([http://fit-pc2.com/wiki/index.php?title=Main_Page](http://fit-pc2.com/wiki/index.php?title=Main_Page))

but what I have read about NSLU2 it sound fun too.

---

### Post by zachtib on 2009-07-28
I'm using the Intel Atom board for my next mini-server: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813121359](http://www.newegg.com/Product/Product.aspx?Item=N82E16813121359)

it's $80, just add RAM and hard drive.  It has a 1.6GHz dual core CPU on the board.

---

### Post by cazz on 2009-07-28
> **zachtib said:**
> I'm using the Intel Atom board for my next mini-server: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813121359](http://www.newegg.com/Product/Product.aspx?Item=N82E16813121359)

it's $80, just add RAM and hard drive.  It has a 1.6GHz dual core CPU on the board.

Nice very nice :)
But I was looking for something that is working out of the box.
so I dont need to buy any case or adapter.

---

### Post by bear24rw on 2009-07-28
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856167032](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167032)

just add HDD and RAM

---

### Post by cazz on 2009-07-28
> **bear24rw said:**
> [http://www.newegg.com/Product/Product.aspx?Item=N82E16856167032](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167032)

just add HDD and RAM


Very very intresting, it is bigger but cheap.
I'm just afraid of the fan it have.

But that is something to think about.

---

### Post by zekopeko on 2009-07-28
I think that somebody on planet ubuntu or gnome uses an eeepc 1000 for his web server. the plus side is that you have an integrated ups, screen and keyboard/touch-pad, HDD, RAM.
I have an asus eeepc 1000h and the battery last around 5h while using gnome. With the improvements in power management the next Ubuntu server edition is bringing this could probably be extended to 8 or more hours. Also the fan on any Atom computer I used was really silent and it only kicked in under heavier loads, the ones that a usually server isn't under.

EDIT: you might want to try looking into the Sheeva Plug. It's ARM based so it shouldn't have an active fan.

---

### Post by bear24rw on 2009-07-28
> **cazz said:**
> I'm just afraid of the fan it have.

i have one which i've been running literally 24/7 since last Christmas with a TB harddrive and xubuntu. it does get a little warm but my HDD temp was always about 40C. I wouldnt worry about temperature. I've also seen someone make a fan mod with where they drilled a hole in the side and slapped on a 120mm

---

### Post by cazz on 2009-07-28
well it sound very very good :)

Do anyone know how much power consumption it take.
What I know it fit-pc2 take less then 10 watt

The bad side of the fit-pc2 it that dont have VGA. 
I did see that MSI Wind PC and that was nice :)

---

### Post by Barrucadu on 2009-07-28
I'm also using a miniITX Atom board for my home server, which I built last week. It's a nice little thing. As said, just add HDD and RAM. Connect a monitor and CD drive whilst you install your distro of choice, then do the rest over SSH.

---

### Post by ericab on 2009-07-28
> **zachtib said:**
> i'm using the intel atom board for my next mini-server: [http://www.newegg.com/product/product.aspx?item=n82e16813121359](http://www.newegg.com/product/product.aspx?item=n82e16813121359)

it's $80, just add ram and hard drive.  It has a 1.6ghz dual core cpu on the board.

+1

---

### Post by cazz on 2009-07-28
well I did find on MSI homepage 
"Low power consumption, less than 40W at full-speed operation"

What I remember, most of that is because it have a HDD inside and that take most of it so if I want to use a memory stick it going to take less power, If I know want that :)

But I trying to find information if the Power Supply can use 230V (have that in Sweden)

---

### Post by cazz on 2009-07-28
Have just got information it only ship within the U.S. and to Canada. 

So I have to buy ut somewhere else

I have found that I can buy one here in Sweden but it cost almost 400 USD
But I do get at DVD, 160GB HDD and 1024 MB ram include in that price.

---

### Post by thisllub on 2009-07-28
I use a Virtual Machine for a webserver.

---

### Post by zekopeko on 2009-07-28
> **cazz said:**
> Have just got information it only ship within the U.S. and to Canada. 

So I have to buy ut somewhere else

I have found that I can buy one here in Sweden but it cost almost 400 USD
But I do get at DVD, 160GB HDD and 1024 MB ram include in that price.

for that price it's better to look for a eeepc with a hdd.

---

### Post by K.Mandla on 2009-07-28
Find a leftover laptop, drop a big hard drive in it, start up FreeNAS and put the thing in the closet. ;)

---

### Post by vpadro on 2009-07-28
I'll go always for the NSLU2, I have one! :D
Sheevaplug doesn't seem too bad.

---

### Post by gn2 on 2009-07-29
I have an NSLU2, but I think it might struggle with how you want to use it.

Have you considered an [EeeBox]("http://event.asus.com/eeepc/microsites/eeebox/en/index.html") or an [Acer Revo]("http://www.acer.co.uk/acer/product.do?link=oln93e.redirect&changedAlts=&kcond48e.c2att101=61300&CRC=2090480396")?

---

### Post by cazz on 2009-07-29
I can buy a MSI Wind PC Atom 1.6 MHz CPU Intel 945GC 1 x 200Pin Intel GMA 950 Barebone - Retail (Black) from Amazon and I maybe going to do that.

THe NSLU2 sound good but what I have read it is slow for MySQL and that.
I even going to stream some movieclip that I have create so I dont think I can use NSLU2.

Yes I have think about a laptop but I'm afraid it going to sound to much.
Some laptop have very bad fan that almost always is on.

So I have to see if I going to buy a MSI wind or something else.

---

### Post by armandh on 2009-07-29
I use an NSLU2 
just set a fixed IP address and set the router to HTTP forwarding [to the fixed address]
set passwords, access groups, etc
done

the problem is the slow up link speeds of home connection to the net

---

### Post by ukripper on 2009-07-29
Have you checked your upload speed first? It will be serving the web.

---

### Post by ssam on 2009-07-29
some options:
sheeva plug - very low power, very small
beagle board - very low power (5 watts)
via mini itx ( [http://mini-itx.com/store/?c=2](http://mini-itx.com/store/?c=2) has power consumption for a number of boards, note that atoms may be low power, but the chip set that comes with them uses a lot)

basically you'll need to choose between arm and x86. arm is very low power, probably fast enough for your needs, will need slight more specialist distros than x86.

among the arm choices most do not have everything you'd expect on a computer vga/dvi, sata, ethernet etc, but you can probably make do without them (eg usb-ethernet adaptors).

also remember the rough approximation that 1 watt running for 1 year costs ~$1 or ~£1 or ~&#8364;1. [http://www20.wolframalpha.com/input/?i=15+watt+*+%C2%A30.12+per+kwh+*+1+year](http://www20.wolframalpha.com/input/?i=15+watt+*+%C2%A30.12+per+kwh+*+1+year)

---

### Post by cazz on 2009-07-29
> **armandh said:**
> I use an NSLU2 
just set a fixed IP address and set the router to HTTP forwarding [to the fixed address]
set passwords, access groups, etc
done

the problem is the slow up link speeds of home connection to the net

But what I have read the PHP and MySQL make it very very slow

---

### Post by cazz on 2009-07-29
> **ukripper said:**
> Have you checked your upload speed first? It will be serving the web.

I have fiber so I have plenty of speed for my upload :)

---

### Post by cazz on 2009-07-29
> **ssam said:**
> some options:
sheeva plug - very low power, very small
beagle board - very low power (5 watts)
via mini itx ( [http://mini-itx.com/store/?c=2](http://mini-itx.com/store/?c=2) has power consumption for a number of boards, note that atoms may be low power, but the chip set that comes with them uses a lot)

basically you'll need to choose between arm and x86. arm is very low power, probably fast enough for your needs, will need slight more specialist distros than x86.

among the arm choices most do not have everything you'd expect on a computer vga/dvi, sata, ethernet etc, but you can probably make do without them (eg usb-ethernet adaptors).

also remember the rough approximation that 1 watt running for 1 year costs ~$1 or ~£1 or ~&#8364;1. [http://www20.wolframalpha.com/input/?i=15+watt+*+%C2%A30.12+per+kwh+*+1+year](http://www20.wolframalpha.com/input/?i=15+watt+*+%C2%A30.12+per+kwh+*+1+year)

hmm ok.

well I did find at the Amazon 
[http://www.amazon.com/exec/obidos/tg/detail/-/B001E71IE0/ref=ord_cart_shr?%5Fencoding=UTF8&m=ATVPDKIKX0DER&v=glance](http://www.amazon.com/exec/obidos/tg/detail/-/B001E71IE0/ref=ord_cart_shr?%5Fencoding=UTF8&m=ATVPDKIKX0DER&v=glance)

so I maybe going to buy it, I just have to figure out what power it need if I need to buy a new adapter (In sweden we have 230V and a diffrent kind of jack)


that was a very very good link to calculate the cost of have a computer on :)

---

### Post by ssam on 2009-07-29
> **cazz said:**
> 
THe NSLU2 sound good but what I have read it is slow for MySQL and that.
I even going to stream some movieclip that I have create so I dont think I can use NSLU2.

the sheevaplug and beagleboard are significantly faster than the NSLU2. [http://matrix108.wordpress.com/2009/05/24/sheevaplug/](http://matrix108.wordpress.com/2009/05/24/sheevaplug/)

---

### Post by cazz on 2009-07-29
> **ssam said:**
> the sheevaplug and beagleboard are significantly faster than the NSLU2. [http://matrix108.wordpress.com/2009/05/24/sheevaplug/](http://matrix108.wordpress.com/2009/05/24/sheevaplug/)

heh yes I have read a little about it.

I have to see what I going to do.

The easy for me is to buy it in sweden, then I have easy to have support if something is broken.
It is also a chance that I have to pay duty on it and even tax.

But you all have give me something to go on.

---

### Post by cazz on 2009-07-29
It feel more and more that I maybe going to buy a sheevaplug.
I have not decide it yet but a sheevaplug is maybe more fun and a
challenge then install a OS and server from a basic computer :)

---

