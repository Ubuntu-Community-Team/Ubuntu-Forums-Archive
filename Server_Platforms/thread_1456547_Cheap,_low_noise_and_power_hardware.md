---
title: "Cheap, low noise and power hardware"
date: 2010-04-17
forum: Server Platforms
---

### Post by Zeophlite on 2010-04-17
Hello,

When I was younger I used to have old php/mysql web based game running from a friend's server that was housed at the university.  Long ago he shut it down, and so I've recently wanted to restart using Linux and servers and what-not.

So I want to buy a small server that I could keep near the home modem, and host my own php toys.  I was wondering what hardware would be recommended.  It would have to be more or less silent, self contained and cheap.  I've had a look at the [VIA ARTiGO Pico-ITX Builder Kit]("http://www.via.com.tw/en/products/embedded/artigo/a1000/index.jsp") but after reading [this]("http://www.hexus.net/content/item.php?item=11976&page=9") article I'm rather disheartened by it.  Which isn't good because it sounds about right - 1 GB ram, 1Ghz processor, quiet, low powered, small - just apparently unusable.

I live in Australia, but anything under AUS$900 I can get sent here without having to spend extra on duty, etc.  I don't really want to spend that much (less than $400 really) unless you can suggest a need.

I want to be able to run a LAMP (Linux, Apache, MySQL, PHP), basically.  Maybe with some mail  servering.  I've just bought a domain name, too.

The main things I'm looking for are motherboard, cpu and case, that are quiet, low power and cheap.  And the capability of the machine, once I've loaded Ubuntu onto it and the above - that is, how long will it last (# visitors / unit time) before it stops working.

I apologise if what I've written seems like I'm asking this forum to google for me.  I am, but I've never used Linux outside of limited university work (I'm not a computer science major), and I've hit a mental roadblock - I don't know what I need to accomplish my aims, and I want to see what someone with more direct experience suggests.  In the end, I want to have this server to be able to learn more about them.

Thanks for all your help.

Daniel

---

### Post by cascade9 on 2010-04-17
The main issue with linux and the VIA is the #%& unichrome video- awful support. That VIA would probably do the job for LAMP (depending on how many requests it gets). The main issue in that review seems to be 'it hasnt got as much power as an intel core2duo mobile CPU'- which is true.

If you want something low powered, the easiest way it with an Intel Atom setup, or a AMD 'e' series setup. Mobile Core2Duos are pretty low pwered as well, but you would probably have to import one, and a socket P (core2duo mobile socket) motherboard as well. 

 A cheap socket p motehrboard will set you back $170 US- 
[http://www.newegg.com/Product/Product.aspx?Item=N82E1681315315](http://www.newegg.com/Product/Product.aspx?Item=N82E1681315315)

Then $220 on a socket p CPU-
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819111010](http://www.newegg.com/Product/Product.aspx?Item=N82E16819111010)

I'd go for the atom/AMD myself.

---

### Post by ian dobson on 2010-04-17
Hi,

maybe have a look at a intel atom system. Their low power/performance it OK (quicker than a VIA), and the prices are quite good.

Regards
Ian Dobson

---

### Post by jflaker on 2010-04-17
There are a few things coming out lately

Bubba Low-Power Fanless Linux Box 
[http://www.ecogeek.org/content/view/425/]("http://www.ecogeek.org/content/view/425/")

Marvell's Plug Computer: A tiny, discrete, fully functional 5 watt Linux server
[URL="http://www.tgdaily.com/hardware-opinion/41525-marvells-plug-computer-a-tiny-discrete-fully-functional-5-watt-linux-server"]http://www.tgdaily.com/hardware-opinion/41525-marvells-plug-computer-a-tiny-discrete-fully-functional-5-watt-linux-server
[/URL]
Google for many more at different power and price points

---

### Post by dfreer on 2010-04-17
Something like this would be great:
[http://promos.asus.com/US/eblast/EeeBox/index.html](http://promos.asus.com/US/eblast/EeeBox/index.html)

Basically anything Intel Atom Based. Newegg has some decent mobo/cpu combo's if you like to build yourself:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813500027](http://www.newegg.com/Product/Product.aspx?Item=N82E16813500027)

---

### Post by Zeophlite on 2010-04-19
Thanks for all your replies.

I'm thinking of getting the [ASRock ION330]("http://www.asrock.com/nettop/overview.asp?Model=ION%20330").  The price range is a bit higher (~$380 for the barebones mobo) but I feel it's more complete.  It also supports OpenCL (which I have just learnt), and also it has HD playback, so I could possibly experiment with it as a HTPC.

I'm just wondering what limitations I'm setting on myself by using this.  What essential servery applications won't I be able to run well or even at all?  I also wanted to run [Redmine]("http://www.redmine.org/") off my website, but that shouldn't be a problem.

Again, thank you for your time.  I'll make sure to inform you of how it goes!

Daniel

---

### Post by Vegan on 2010-04-19
There are some fanless PSU and video cards on the market, the CPU cannot easily be cooled, but I have seen aftermarket fanless coolers.

---

