---
title: "Recommended Graphics card for HP Elite 8000 SFF?"
date: 2017-09-19
forum: The Cafe
---

### Post by MasterNetra on 2017-09-19
Edit: Further research, I'm thinking, GeForce GTX 750 Ti, however apparently I will need to upgrade my PSU for it.

I want to get a Graphics card for this desktop (HP Elite 8000 SFF) I am using but not sure what to get for it, other then it probably should be a Nvida, but not sure how to find one compatible with this system. Something that handles OpenGL 3.0 or better (current intergrated graphics card only handles up to 2.1, though only 1.1 on wiindows 10). Any Recommendations? Btw it can be found on Amazon; ([https://www.amazon.com/gp/product/B0094JF1HA/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B0094JF1HA/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1)).

Specs:

(Processor): Intel Core 2 Duo E8400 (3.0 GHz)
(Ram): 4GB
(Graphics Card): Intel Q45/Q43 Chipset - Integrated Graphics 0 [A3] [Hewlett-Packard]
(Chipset): Intel GMA 4500(M)(HD)
(Motherboard): Hewlett-Packard 3646h
(Motherboard Chipset): Intel Q45 (Eaglelake-Q) + ICH10DO
(Storage): 250GB
(PSU): 240W (Proprietary, Can't change)

I'm currently duel booting Ubuntu 17.04 (64bit) and Windows 7 (64bit).

---

### Post by mastablasta on 2017-09-20
why should it be nvidia?

also you will need to upgrade PSU in any case if you want to do some gaming (which GTX750Ti is aimed at). 

make sure to check you PCI-e version on the motherboard as well. though you should be good, just make sure the version is at least 2.0. Some newer cards would not support the older vesions (whatever happened to standards and backwards support?!).

also if you plan to use a GPU with plenty of RAM, then RAM upgrade might be worth lookin into. but with GPU 2GB or less you will do fine.

when upgrading the PSU get one that is 80 bronze at least and i would get a 500 W one. more power never hurt anyone... :)

---

### Post by MasterNetra on 2017-09-20
> **mastablasta said:**
>  why should it be nvidia? ... 

Better supported in linux overall, AMD drivers tend to be a bit spotty/of a gamble at times as I understand it.

> **mastablasta said:**
> 
... also if you plan to use a GPU with plenty of RAM, then RAM upgrade might be worth looking into. but with GPU 2GB or less you will do fine.

when upgrading the PSU get one that is 80 bronze at least and i would get a 500 W one. more power never hurt anyone...


Aye, my system can be upgraded to 8GB of ram, but I'm more focused on getting the Graphics card, and sense the GTX750Ti is a 2GB Vram card I should be fine with it and I was intending on getting either a 400W or 500W PSU to begin with, sense as I understand it, PSU lose power capability over time and having that much more capability would make for a nice buffer.

---

### Post by mastablasta on 2017-09-21
> **MasterNetra said:**
> Better supported in linux overall, AMD drivers tend to be a bit spotty/of a gamble at times as I understand it.
AMD went nearly fully opensource now. the GPU pro can be added for gaming. otherwise best support is probabyl by intel, which is fully opensource. 

nvidia still has a bit of an advantage over AMD, but AMD is gaining momentum fast.  if i wanted long term support i would go with AMD, but in the short run and for gaming nvidia might be better (although i had bad experience with it and it's driver on 730 GT). 

> 

Aye, my system can be upgraded to 8GB of ram, but I'm more focused on getting the Graphics card, and sense the GTX750Ti is a 2GB Vram card I should be fine with it and I was intending on getting either a 400W or 500W PSU to begin with, sense as I understand it, PSU lose power capability over time and having that much more capability would make for a nice buffer.

for 2 Gb card you are indeed good with 4GB ram. 

get a quality PSU with at least 80 plus bronze. [https://en.wikipedia.org/wiki/80_Plus](https://en.wikipedia.org/wiki/80_Plus)

they cost more but your PC and environment will be thankfull for it.

---

### Post by mips on 2017-09-25
Get a 1050 or 1050ti without external power connector.

They draw <75W and you cpu is 65W so your existing 240W psu will be ok. Your psu is a proprietary hp unit anyway which you can't replace with a standard off the shelf unit.

---

### Post by MasterNetra on 2018-05-03
> **mips said:**
> Get a 1050 or 1050ti without external power connector.

They draw <75W and you cpu is 65W so your existing 240W psu will be ok. Your psu is a proprietary hp unit anyway which you can't replace with a standard off the shelf unit.

So this would be fine? - [https://www.newegg.com/Product/Product.aspx?Item=9SIA6ZP56T3450&cm_re=nividia_gtx_1050ti-_-14-487-290-_-Product](https://www.newegg.com/Product/Product.aspx?Item=9SIA6ZP56T3450&cm_re=nividia_gtx_1050ti-_-14-487-290-_-Product) , says 300W or greater is required but falls under your suggestion it seems.

Also yea your right it seems I can't upgrade my power supply ([https://h30434.www3.hp.com/t5/Desktop-Hardware-and-Upgrade-Questions/Got-a-hp-8000-sff-and-would-like-to-upgrade-it/td-p/6217947](https://h30434.www3.hp.com/t5/Desktop-Hardware-and-Upgrade-Questions/Got-a-hp-8000-sff-and-would-like-to-upgrade-it/td-p/6217947)). There is also mentioned that modern graphics cards, something about modern systems using UEFI Bios and this old system simply using BIOS.

---

### Post by pqwoerituytrueiwoq on 2018-05-03
Can you post a picture of the psu label, i want to see what the amperage on the +12v rail is
I am sitting ext to a dell that has a >700W PSU but can not handle more than a very low power gpu as it only has 18A on the +12 rail, but it can do 30A on the +3.3v rail

i think that case will require a low profile card, well you could use full size with a getto case mod

BTW the old GT 520 i picked up off ebay for $20 supports openGL 4.6 with the nvidia 390.48 driver
looks like it can do about 10fps in the heaven 4.0 benchmark on the lowest settings on a low res screen
> [h=1]Unigine Heaven Benchmark 4.0[/h] [TABLE="class: result"]
 [TR]
[TD="class: right"]FPS:[/TD]
[TD]**11.5**

[/TD]
[/TR]
 [TR]
[TD="class: right"]Score:[/TD]
[TD]**290**
[/TD]
[/TR]
 [TR]
[TD="class: right"]Min FPS:[/TD]
[TD]**5.9**
[/TD]
[/TR]
 [TR]
[TD="class: right"]Max FPS:[/TD]
[TD]**19.1**
[/TD]
[/TR]
 [/TABLE]
 [h=2]System[/h] [TABLE="class: detail"]
 [TR]
[TD="class: right"]Platform:[/TD]
[TD]Linux 4.15.0-20-generic x86_64
[/TD]
[/TR]
 [TR]
[TD="class: right"]CPU model:[/TD]
[TD]Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz (1864MHz) x2
[/TD]
[/TR]
 [TR]
[TD="class: right"]GPU model:[/TD]
[TD]GeForce GT 520 PCI Express 390.48 (1024MB) x1
[/TD]
[/TR]
 [/TABLE]
 [h=2]Settings[/h]  [TABLE="class: detail"]
[TR]
[TD="class: right"]Render:[/TD]
[TD]OpenGL
[/TD]
[/TR]
 [TR]
[TD="class: right"]Mode:[/TD]
[TD]1280x1024 fullscreen
[/TD]
[/TR]
 [TR]
[TD="class: right"]Preset[/TD]
[TD]Custom
[/TD]
[/TR]
 [TR]
[TD="class: right"]Quality[/TD]
[TD]Low
[/TD]
[/TR]
 [TR]
[TD="class: right"]Tessellation:[/TD]
[TD]Disabled[/TD]
[/TR]
[/TABLE]


---

### Post by MasterNetra on 2018-05-03
> **pqwoerituytrueiwoq said:**
> Can you post a picture of the psu label, i want to see what the amperage on the +12v rail is
I am sitting ext to a dell that has a >700W PSU but can not handle more than a very low power gpu as it only has 18A on the +12 rail, but it can do 30A on the +3.3v rail

i think that case will require a low profile card, well you could use full size with a getto case mod

[https://postimg.cc/image/v99peuhbf/](https://postimg.cc/image/v99peuhbf/) - Not great but should be readable if you click on it there to Zoom in. Also I had edited my reply I dunno if you seen the edited version before you posted your reply or not.

---

### Post by pqwoerituytrueiwoq on 2018-05-03
only 12A, the lowest card i could find the other week called for 18A
not that that makes much sense as that would exceed the limit on the pci-e slot (150W limit)
i guess that is what the want you to have to also run the rest of the system

What are you trying to run hopefully you can get by with a low power card like a gt 510/520/610/620/710/720
make sure you get the low profile bracket(s) if you need vga make sure it has both unless you can cut a blank out yourself for the plug

---

### Post by MasterNetra on 2018-05-03
Just trying to get the best I can for gaming, hoping to the point where I can run fallout 4 on it's lowest settings (can upgrade ram to 16GB ftw), early on when F4 first released I could run it (laggy but ran) with reduced textures and potato settings, a update KO-Ed that though (the update that added that store crap I think).

---

### Post by pqwoerituytrueiwoq on 2018-05-03
I would say for your current case/psu your best bet would be a GT 1030, but the price tag is ridiculous for the performance
my GPU would crush it performance wise and it is under 1/2 the price
the hard part for you is you have a weak PSU so you need a high efficiency GPU and a low profile card

but for the price of that card on newegg you could get a better used pc and upgrade the gpu and still spend less
maybe you can find a cheap used one?  under $50 would be reasonable IMO

---

### Post by MasterNetra on 2018-05-03
This system is the best cheap used one I could find and was less then $100, well minus warranty anyway. Didn't know I was going to be so locked down with it though, with being unable to change the PSU.

---

### Post by pqwoerituytrueiwoq on 2018-05-04
I found a low profile gt 1030 new at newegg for 80 today (still too much for the performance IMO)
[https://www.newegg.com/Product/Product.aspx?Item=N82E16814932060](https://www.newegg.com/Product/Product.aspx?Item=N82E16814932060) (low profile bracket is in image #6)
Though if the OP in this thread does upgrade maybe his used card will fit in your case: [https://ubuntuforums.org/showthread.php?t=2390770](https://ubuntuforums.org/showthread.php?t=2390770) (maybe you two can work out a deal?)

---

### Post by yqqwe on 2018-05-05
i think you can try amd r7 350 .it is cheap and with good performance,or if you have good budget , you can try something better. 
  

[HR][/HR]advice From web master of [https://hash.onlinetoolsland.com/](https://hash.onlinetoolsland.com/)

---

### Post by bcschmerker on 2018-05-05
The COMPAQ® 8000 Elite™ was offered with 240W and 320W power-supply units.  After reading the [official support page](https://support.hp.com/us-en/product/hp-compaq-8000-elite-small-form-factor-pc/4065894/document/c01926347) at Hewlett-Packard® Support&#8480;, most of the half-height video display adapters originally offered require the 320W supply.  Unfortunately, I haven't any interior pictures of the SFF, so cannot determine whether it will take the Shuttle® PC63A supply (a successor to the PC6300001 I retrofitted to my eMachines®/Acer® EL1210-09).

---

### Post by MasterNetra on 2018-05-10
> **bcschmerker said:**
> The COMPAQ® 8000 Elite™ was offered with 240W and 320W power-supply units.  After reading the [official support page](https://support.hp.com/us-en/product/hp-compaq-8000-elite-small-form-factor-pc/4065894/document/c01926347) at Hewlett-Packard® Support&#8480;, most of the half-height video display adapters originally offered require the 320W supply.  Unfortunately, I haven't any interior pictures of the SFF, so cannot determine whether it will take the Shuttle® PC63A supply (a successor to the PC6300001 I retrofitted to my eMachines®/Acer® EL1210-09).

Doubtful my case isn't a tower and requires SFF stuff.

---

### Post by MasterNetra on 2018-05-10
> **yqqwe said:**
> i think you can try amd r7 350 .it is cheap and with good performance,or if you have good budget , you can try something better. 


Except that it requires a 400W power supply and it's not a low profile which I need it to be. I assume your talking about this: [https://www.newegg.com/Product/Product.aspx?Item=N82E16814125940&Tpk=amd%20r7%20350](https://www.newegg.com/Product/Product.aspx?Item=N82E16814125940&Tpk=amd%20r7%20350) - The only amd r7 350 graphics card I could find on newegg.

---

### Post by pqwoerituytrueiwoq on 2018-05-13
Seems there are 2 versions of the gt 1030
[https://www.geforce.com/hardware/desktop-gpus/geforce-gt-1030/specifications](https://www.geforce.com/hardware/desktop-gpus/geforce-gt-1030/specifications)
When i said it would run your game i meant the 30W version

I did run a calculation on how what PSU wattage you would need
[https://outervision.com/b/JLOBTg](https://outervision.com/b/JLOBTg)
adding a GT1030 would make it need a 270W PSU
you have only have ~2 watts to run a GPU with that system
the 20W GT 1030 is the lowest wattage GPU they make, you only have 10% of that to work with
unless you modify the PSU or mod a new unit you can not add any hardware to that computer, you would be luck to even charge your phone with a usb port while watching youtube

---

### Post by axiomanarcho on 2018-05-15
> **MasterNetra said:**
> Edit: Further research, I'm thinking, GeForce GTX 750 Ti, however apparently I will need to upgrade my PSU for it.

I want to get a Graphics card for this desktop (HP Elite 8000 SFF) I am using but not sure what to get for it, other then it probably should be a Nvida, but not sure how to find one compatible with this system. Something that handles OpenGL 3.0 or better (current intergrated graphics card only handles up to 2.1, though only 1.1 on wiindows 10). Any Recommendations? Btw it can be found on Amazon; ([https://www.amazon.com/gp/product/B0094JF1HA/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B0094JF1HA/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1)).

Specs:

(Processor): Intel Core 2 Duo E8400 (3.0 GHz)
(Ram): 4GB
(Graphics Card): Intel Q45/Q43 Chipset - Integrated Graphics 0 [A3] [Hewlett-Packard]
(Chipset): Intel GMA 4500(M)(HD)
(Motherboard): Hewlett-Packard 3646h
(Motherboard Chipset): Intel Q45 (Eaglelake-Q) + ICH10DO
(Storage): 250GB
(PSU): 240W

I'm currently duel booting Ubuntu 17.04 (64bit) and Windows 7 (64bit).

You definitely need a better psu some thing with a 80+ gold rating and around 500w 

Also go for a nvidia 1050 gtx it wont bottleneck from your cpu to badly.

---

### Post by bcschmerker on 2018-05-20
**The Shuttle® PC63A is one of the most compact power-supply units on the market,** with 500W overall capacity.  Not every small form factor case will take it, however; I still had to do some cutting when retrofitting a Shuttle® PC6300001 (the PC63A's immediate predecessor) in my eMachines®/Acer® EL1210-09 in place of the stock 220W LiteOn® -- even though the units were of identical cross-sectional area, the master switch and fan were on opposite sides between them.

---

### Post by forrestcupp on 2018-05-22
I don't know how tech-savvy you are, but I wonder if you could get a cheap $20 case, transfer your motherboard, CPU, and RAM over, and then buy a standard PSU. Then you'd be able to get whatever GPU you want.

---

### Post by MasterNetra on 2018-06-12
> **axiomanarcho said:**
> You definitely need a better psu some thing with a 80+ gold rating and around 500w 

Also go for a nvidia 1050 gtx it wont bottleneck from your cpu to badly.

> **bcschmerker said:**
> **The Shuttle® PC63A is one of the most compact power-supply units on the market,** with 500W overall capacity.  Not every small form factor case will take it, however; I still had to do some cutting when retrofitting a Shuttle® PC6300001 (the PC63A's immediate predecessor) in my eMachines®/Acer® EL1210-09 in place of the stock 220W LiteOn® -- even though the units were of identical cross-sectional area, the master switch and fan were on opposite sides between them.

My PSU is a propertary HP,so replacing with a better doesn't seem to be a option.

> **forrestcupp said:**
> I don't know how tech-savvy you are, but I wonder if you could get a cheap $20 case, transfer your motherboard, CPU, and RAM over, and then buy a standard PSU. Then you'd be able to get whatever GPU you want.

I've never done such a thing. I've only ever replaced Ram and a Hard drive, attempted to do a CPU once but botched it.

---

### Post by pqwoerituytrueiwoq on 2018-06-12
> **MasterNetra said:**
> [QUOTE=forrestcupp;13769400]I don't know how tech-savvy you are, but I wonder if you could get a cheap $20 case, transfer your motherboard, CPU, and RAM over, and then buy a standard PSU. Then you'd be able to get whatever GPU you want.I've never done such a thing. I've only ever replaced Ram and a Hard drive, attempted to do a CPU once but botched it.[/QUOTE]
Was that before they put a IHS on the CPU?
anyway if that PSU in your case uses a proprietary pin out (or plug) for the motherboard, there is no upgrade path at all for it
at one point dell used the standard 24pin plug with a custom pin set so it looked like you could use any PSU then when you do you get the magic black smoke

I do not know what your budget it or how much shipping would be, but i do have a old core 2 duo system, you could pop your HDD into and i think your CPU is better but it may be the same socket so you could swap it over; the PSU does support what you want to do, but i would still recommend replacing it (there is no way it can do what that label says)
i even have a brand new PSU (520W Seasonic) on hand
If your motherboard has a standard 24 pin and standard 4pin plug as well as standard ATX mount points you can use any budget micro atx case you can find on newegg

---

### Post by MasterNetra on 2018-06-12
> **pqwoerituytrueiwoq said:**
> Was that before they put a IHS on the CPU?
anyway if that PSU in your case uses a proprietary pin out (or plug) for the motherboard, there is no upgrade path at all for it
at one point dell used the standard 24pin plug with a custom pin set so it looked like you could use any PSU then when you do you get the magic black smoke

I do not know what your budget it or how much shipping would be, but i do have a old core 2 duo system, you could pop your HDD into and i think your CPU is better but it may be the same socket so you could swap it over; the PSU does support what you want to do, but i would still recommend replacing it (there is no way it can do what that label says)
i even have a brand new PSU (520W Seasonic) on hand
If your motherboard has a standard 24 pin and standard 4pin plug as well as standard ATX mount points you can use any budget micro atx case you can find on newegg

I have a budget of about $50 atm. What is the specs on your Core 2 duo system? My CPU power is 3 GHZ, ramtype is DDR3 SDRAM - non-ECC.

"Was that before they put a IHS on the CPU?" - I dunno, it was on a even older system with a P4, half of it broke off trying extract the old CPU and other half was lodged in socket so that KOed things.

---

### Post by pqwoerituytrueiwoq on 2018-06-13
bare exposed die: [http://mixeurpc.free.fr/SITE_x86-guide/Photos/Grandes/25/AMD%20Athlon%2064%20X2%20Mobile%20QL-64%20AMQL64DAM22GG%2001.jpg](http://mixeurpc.free.fr/SITE_x86-guide/Photos/Grandes/25/AMD%20Athlon%2064%20X2%20Mobile%20QL-64%20AMQL64DAM22GG%2001.jpg)
pretty sure this old thing has ddr2 ram, i think it is 2.8Ghz maybe motherboard model: Intel DG965OT
if your system has 4 or 8gb sticks and you can downgrade the ram you could increase your budget as ram is stupid expensive right now, if less ram is still enough for your needs

---

### Post by MasterNetra on 2018-06-13
> **pqwoerituytrueiwoq said:**
> bare exposed die: [http://mixeurpc.free.fr/SITE_x86-guide/Photos/Grandes/25/AMD%20Athlon%2064%20X2%20Mobile%20QL-64%20AMQL64DAM22GG%2001.jpg](http://mixeurpc.free.fr/SITE_x86-guide/Photos/Grandes/25/AMD%20Athlon%2064%20X2%20Mobile%20QL-64%20AMQL64DAM22GG%2001.jpg)
pretty sure this old thing has ddr2 ram, i think it is 2.8Ghz maybe motherboard model: Intel DG965OT
if your system has 4 or 8gb sticks and you can downgrade the ram you could increase your budget as ram is stupid expensive right now, if less ram is still enough for your needs

No ram is still important. Again ultimately I want to be able to play fallout 4 at some point. The only thing the system has going for it compared to what I have already is that it's PSU isn't proprietary.

---

### Post by pqwoerituytrueiwoq on 2018-06-13
I do have a old junk case, if you do not care how it looks (one of the front bay covers is missing) you can have it and the junk still inside for what ever the shipping cost is
It will hold a mATX board and a ATX PSU
do not count on being able to use the front panel connectors, i pulled the plugs off to keep, it is planned to be dropped off at best buy for recycling
honestly at this point you would be better off with a DIY case (mount parts to a piece of wood with brackets and inset nuts) and making the worlds lowest preforming wall mounted pc as it would probably cost less than shipping that thing

---

