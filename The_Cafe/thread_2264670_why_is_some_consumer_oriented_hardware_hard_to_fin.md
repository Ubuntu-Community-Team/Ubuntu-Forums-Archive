---
title: "why is some consumer oriented hardware hard to find?"
date: 2015-02-09
forum: The Cafe
---

### Post by mastablasta on 2015-02-09
I am really puzzled by the whole thing. I realise that some hardware may be sold to businesses for other use or as some embedded devices but seriously I can not understand why some hardware that was marketed to cosnumers is not even sold anywhere.

I was searching for some specific hardware and was comparing some specs and reviews and analisys, reading various blogs... anyway "wasted" time it seems. I then see this hardware was presented for example in 2013 yet finding a motherboard with this APU is extremely difficult. after quite long search I found one manufacturer that stopped making them (at least from the comments on boards). the product wasn't that good anyway (or rather had a fan issue). I then found one or two more similar but within a much higher price range and that was it. and the APU I was after is actually not bad. 

it puzzles me that time was invested into developing the product, probably considerable engineer hours, marketing was present, they are flashed at fairs and such. new articles, reviews... and then nothing . you can't get it anywhere for that kind of price. they just are not there. or they disappear within months. do these tech companies have so much money they can afford such dead ends? moreover why do they do it if the product is good and praised in reviews for it's good performance at a price.

take for example AMD E-450 (which is now condiered "old tech")- you do a search on motherboards and there is plenty with E-350 chip - a chip that is even older, with overheating issues (they were corrected with 450), much weaker GPU (again corrected in 450 series). yet I can easilly find new E350 or even E240 but not E450. it's similar with newer chips. or some atoms. ok I understand how some of these products might find it's way into like flight entertainment systems and such, but I am surprised that you can't find them readily available on consumer market. there is plenty of Core i boards, or FM or AM3 or whatever the new AMD socket is. but these little things that have good performance at low cost... even if you can find them the choice is really very limited.

is the margin so thin on them or what? and if it is why are they even bothered in making them and marketing them?

---

### Post by TheFu on 2015-02-09
The E-450 was the last of that model line, before AMD switched to A{number} based stuff.  I own an E-350 and haven't been able to find those anymore for the same price I paid the 3-4 yrs ago when it was purchased.
Why aren't these available? The answer is probably a mix of reasons - low consumer acceptance, low margin, no vendors wanted them because running Windows sucked on that level of hardware, so only media center and NAS devices were made.  Intel came out with new competition, and jumped beyond for the same price point, .... etc.... 

The E-350s didn't have USB3 - at least mine didn't.  Perhaps there was a major issue with USB3 drivers in the E450?
I found an E-350 for $50 here ... that has USB3, so it is a newer version than mine.  Also has GigE networking.  For a server, it is capable for almost any home use, just not running GUIs. Thanks to the GPU, it does handle h.264 video at 1080p resolutions and below well.  Ran Unity on it for about 20 min. It was painful.  Now it boots directly into Kodi (new name for XBMC).

Plus much of the low cost world has become excited about $50 ARM solutions.  At my LUG yesterday, a masters student wanted to make a cluster using 8 Raspberry Pis.  He didn't know what or why, just that he did.

AMD lost me when they switched to the A-naming. They don't seem to ahve any $50 APUs, which is what I spend 3-4 yrs ago on the fusion E350. In theory, a new APU should be 4x faster at that price today. Theory.

The AMD A4-4020 is 3x faster, but 50% more expensive (around $80), but also sucks 65W of power. Unacceptable.

[http://www.hardware-revolution.com/best-cpu-apu-processor-january-2015/](http://www.hardware-revolution.com/best-cpu-apu-processor-january-2015/) has some interesting recommendations.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157513](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157513) - perhaps a cheap celeron is an option? The "Shopping Insight" section shows other alternatives.

---

### Post by mastablasta on 2015-02-10
actually e series moved into E1 and E2. I think E1 are C series renewed while E2 seems to have some descent power: [http://www.amd.com/en-us/products/processors/notebook-tablet/e-series-apu](http://www.amd.com/en-us/products/processors/notebook-tablet/e-series-apu)#
[TABLE="class: ms-rteTable-default, width: 100%"]
[TR="class: ms-rteTableEvenRow-default"]
[TD="class: ms-rteTableEvenCol-default"]E2-6110
[/TD]
[TD="class: ms-rteTableOddCol-default"]Radeon R2
[/TD]
[TD="class: ms-rteTableOddCol-default"]4
[/TD]
[TD="class: ms-rteTableEvenCol-default"]1.5 GHz
[/TD]
[TD="class: ms-rteTableEvenCol-default"]500 MHz
[/TD]
[TD="class: ms-rteTableOddCol-default"]2 MB
[/TD]
[TD="class: ms-rteTableOddCol-default"]DDR3L-1600
[/TD]
[TD="class: ms-rteTableEvenCol-default"]15 &#8203;W
[/TD]
[/TR]
[/TABLE]

and though they mnention these are for laptops you can actually get mini itx boards with some of these. but the issue is there just aren't many of them.

also for example A4-6210 has TDP 15W - but it seems all these are aimed at laptops. why not stick them into desktops? it looks like other desktop APUs from the A series have 65W and more power usage. though they are GPU and CPU. according to wiki i3 haswell uses about 54 W, but likely it has a weaker GPU and stronger CPU. and it costs more. I don't know one would have to take two similar ones out to compare. I am not so familiar with current models to do that.

E-450 and windows starter with 2 GB ram (actually 1,5 since GPU takes the rest) - runs fluently. so does Kubuntu 64bit. I can also run virtualbox servers on it. dedicate one CPU to vbox and it will still run well. I plan to upgrade to 6GB ram since it has one slot free.

---

### Post by tgalati4 on 2015-02-10
The same trend is happening with Arduino and other open-source microcontrollers:  Why am I spending $25 to $35 for a microcontroller board when I can use a $2.50 chip and a few components to accomplish the same thing?  

It does seem that a lot of money is wasted on product development--a fraction of that would go a long way in contributing to open hardware standards.

---

### Post by mastablasta on 2015-02-11
well yes. I mean they develop it, they market it, present it and there is nothing to be found. I mean if no one wants to put them on their motherboard why not help manufacturers or at least try to put on some yourself or work in partnership.

but here is the funny thing as I was surfing the web tracking one motherboard - they ran out of the stock. they actually ran out. though it seems a new revision was made so perhaps they have it now or will have it again. anyway if you can sell something and profit why stop doing it? I mean these are not really that old models or APUs, plus others do part of the marketing for you (the APU part). strange...

i work in sales and sometimes we would sell old things. and sometimes there is a market for them. if i see someone buying it, i make sure we supply it. i was selling huge amount of some parts until a year ago that were used in CRT monitors and TV. we are talking over 5000 pcs a month. at a very special price, but still had big margin. the ones we were selling to were not even the final client. so they earned well on these as well. anyway my point is if there is a market for it, it is kind of strange to me that one would not sell it and even stranger that someone would develop the whole thing, do all the marketing, certification... and then not sell it.

---

### Post by TheFu on 2015-02-11
As a business owner, I spend more time trying to pick the projects we work and stop employees from doing lower-profit things that we used to do.  It is about optimizing profits and making certain we are always forward-looking, not stagnant.  That is a marketing thing.  Large brands want to be perceived as "forward looking" - so if they have 20 CPU lines running, they can't continue running CPUs from 4+ yrs ago. They need to run newer, if not better, CPUs on those lines.

After all, when was the last time you bought a Via CPU or a PowerPC?

---

### Post by mastablasta on 2015-02-12
that makes sense. but most I am looking for are relatively new CPUs introduced in end of 2013 and 2014.

---

