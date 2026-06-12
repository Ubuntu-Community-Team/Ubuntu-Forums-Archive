---
title: "Is this good enough for a web server?"
date: 2010-07-25
forum: Server Platforms
---

### Post by fela on 2010-07-25
Hi, I've been building a website and it's live at the moment ([http://sixteennet.homelinux.org]("http://sixteennet.homelinux.org")), but I'm doubtful about the hardware it's running on. First of all, the details:

Debian Linux 5 (Lenny) with Apache2/PHP5
AMD Athlon LE-1600 2.2GHz CPU (scales to 1GHz at idle)
2GB DDR2 non-ECC memory
500GB SATAII HDD
cheap Gigabyte motherboard, micro ATX
VERY cheap PSU, could crap out any moment really, extremely loud, I keep telling the owner of the server (my dad) to get a proper PSU but he won't do it until it fails (I also keep telling him that if it does fail it'll kill everything else in the box :/ ).
MicroATX case with NO fans, all air flow around the case is provided by the PSU fan.

Now looking at this you would think that the temps are very bad, well really they're very good, CPU's never above 35C, nothing's above 42C, ever.

Anyway, so what I'm wondering is that if by some stroke of luck my site suddenly gets loads of hits (atm it doesn't really get any TBH, apart from my friends, even though it comes up on google if you search sixteennet), would the single core athlon be able to handle both the web server (apache) AND the mysql database (wordpress uses it) that the server also runs?

And yeah you don't need to tell me to get a better PSU :/

cheers

---

### Post by HermanAB on 2010-07-26
Plenty good enough.  Web servers are very efficient things.  I've been using similar hardware for years for small web sites and email.

However, the most important thing to do is to add a UPS.  Power quality is the main source of problems with servers.  Even the cheapest UPS will do, since interruptions are usually very brief - usually just a glitch lasting milliseconds to seconds.  So, don't wire the thing up to shut down when the power fails - that may cause the system to be down more than up.  Just plug the server into the UPS and drive a pencil or screwdriver through the UPS fault beeper to silence it...

BTW, nowadays 'cookie tray' servers are popular.  In the BBS days, we hung the computer parts on a peg board.  The advantage is easy access to the pieces and cooling with a big floor fan. 

Peace.

---

### Post by fela on 2010-07-26
OK great, that's good to know, it seems to be handling it well anyway - although if I login via SSH and run htop, and then load pages from the site, I can see apache2's CPU usage go right up while the page is loading (so I'm not sure how well it would handle multiple page requests simultaneously...like that's ever gonna happen though lol).

About the UPS, the power seems to be alright, not an issue even with the rubbish PSU. We don't seem to get power cuts around here (London), and the server's had good uptimes (it once had an uptime of quite a few months, but I had to reboot it to change a BIOS setting :(), I'll consider getting a UPS but I think a better PSU would be more worthwhile.

Cheers

---

### Post by KHS21 on 2010-07-26
It's great to see a fast hosted web page form your server, as I too am working on a web server, but mine is going to be built with old hardware, as this server task is mainly for education. However, it will be a fully functioning production server. From my research, those specs are more than enough.

---

### Post by Tylerjd on 2010-07-26
Yeah, I'm running a webserver/vpn/ssh/dns/mysql/ldap server on a 5 year old with 

Ubuntu 10.04 Server x64 (LAMPP install) 
AMD Athlon X2 64 (Dual Core, 2.2Ghz)
2GB DDR2 Memory
250GB Seagate SATA
2TB Western Digital Caviar Green SATA
ASUS Motherboard
300W (500w max) [BetTec] POS cpu

And I see my cpu usage from Apache spike every time I request a page. So its not just your setup that Apache2 uses high CPU, but I have my theories with PHP liking to eat my CPU.

---

### Post by mr clark25 on 2010-07-26
i wish my web server came close to yours!

mine is an old pentium 3 @1.0ghz, with 512mb of ram, running ubuntu server 8.04 with apache.

it seems to work fine. i did find an old ups unit to stick on it, so im good if the power cuts out for <5mins...

my website: mrclark.ath.cx

[quote=sixteennet]
(apart from design - I'm not good at design,                         			hence this website xD).
[/quote]

looks better than my website...

---

### Post by wojox on 2010-07-26
You could always try [Performance Benchmarks a Webserver]("http://www.cyberciti.biz/tips/howto-performance-benchmarks-a-web-server.html") fela.

---

### Post by lisati on 2010-07-26
Mine is a fairly low-traffic server and seems to cope reasonably well with 1Gb RAM and a 1.7GHz single core Sempron - it took me about 4 years to discover it was 64-bit!!!!

(When I say "low traffic" I'm not counting a couple of recent spam runs from China that seemed to be targeting my email system. It was partly own fault for not constructing a spamtrap properly - thankfully I was able to block the hosts involved without blocking legitimate email.)

---

### Post by fela on 2010-07-28
Thanks for the replies (and the traffic this post generated - according to apache's access file ;)), especially wojox - next time I get access to a Linux client I'll test my server a bit (say give it a torture test of 100000 requests with 1000 concurrent - how's that for some torture :P).

Oh and mr clark, I checked out your website. How about some CSS someday? :) just a suggestion :D

cheers

---

### Post by kevinthecomputerguy on 2010-07-28
Plenty good !
I run [http://woodel.com](http://woodel.com)    
(800mhz, 1GB ram, No sata ports, piece of junk Lacie Ethernet disk)

*don't buy one of these unless you plan on re-formatting to Linux, it comes with XP embedded and is a paper weight at best. Load Ubuntu \ Debian on it, and its a hot rod.

---

### Post by fela on 2010-07-29
> **kevinthecomputerguy said:**
> Plenty good !
I run [http://woodel.com](http://woodel.com)    
(800mhz, 1GB ram, No sata ports, piece of junk Lacie Ethernet disk)

*don't buy one of these unless you plan on re-formatting to Linux, it comes with XP embedded and is a paper weight at best. Load Ubuntu \ Debian on it, and its a hot rod.

Cool, although I would have thought there's not much server side code at all there - I mean the images and text are rendered by the client and it doesn't look like there's any PHP going on (and if there is it's unnecessary judging from what I saw of the site), so if I'm right the only load on the server is transmitting the data tell me if I'm wrong ;)

Oh by the way, I wouldn't dream of putting any version of Windows on a server.

---

### Post by kevinthecomputerguy on 2010-07-29
I must have missed where you said you needed SQL. I thought you we just asking about a web-server. My bad. 
 
If you click on the woodel accounts link, you can see its serving up Usermin to my users. Which is working out great for a box i almost tossed :- )
 
*That box comes pre-loaded from Lacie with "Windows Embedded Edition."
It sucked really hard before i put Linux on it.

---

### Post by Vegan on 2010-07-29
I am using an old Pentium III 667 based machine and outside of the disk limitations it works fine.

I use a USB card and USB sticks to provide storage for the web sites.

---

### Post by fela on 2010-07-29
> **Vegan said:**
> I am using an old Pentium III 667 based machine and outside of the disk limitations it works fine.

I use a USB card and USB sticks to provide storage for the web sites.

Awesome! I love it when people use old hardware that's still capable, instead of throwing it in the dump :D Although you wouldn't exactly be able to run facebook on that ;)

> **kevinthecomputerguy said:**
> *That box comes pre-loaded from Lacie with "Windows Embedded Edition."
It sucked really hard before i put Linux on it.

I should imagine it did ! Windows embedded edition, just the name sounds bad...out of curiosity how did you stick Linux on it, if it's an embedded device?

---

