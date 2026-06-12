---
title: "looking for UPS advice"
date: 2010-12-22
forum: The Cafe
---

### Post by nerdy_kid on 2010-12-22
I am looking for a uninterruptible power supply for my web server and was wondering what everyone thinks of this one:  [http://www.newegg.com/Product/Product.aspx?Item=N82E16842101004]("http://www.newegg.com/Product/Product.aspx?Item=N82E16842101004")

I don't want to spend over $130 and I need it to power just the server and the router (minus the screen and all that) for at least 3 hours, preferably around 8.  Is the one I linked good for all that?  It says battery time 11.7 but they forgot to mention whether that was minutes or hours lol

---

### Post by oldsoundguy on 2010-12-22
for the length of time you stated, that is definitely NOT big enough. If you REALLY need that much time, you are going to be paying a LOT more.
I use APC 1400 units and am lucky to get 1/2 and hour with the load I have on them.
The cost is not the unit itself .. it is the batteries.

---

### Post by nerdy_kid on 2010-12-22
> **oldsoundguy said:**
> for the length of time you stated, that is definitely NOT big enough. If you REALLY need that much time, you are going to be paying a LOT more.
I use APC 1400 units and am lucky to get 1/2 and hour with the load I have on them.
The cost is not the unit itself .. it is the batteries.

oh ouch....was afraid of that.  I guess the 11.7 was minutes then lol

Maybe instead of using a UPS to supply AC power I could do some soldering and wire up a 20V lithium battery (plus some circuitry) that powers the server+router directly... cause my lappy is way more powerful then my server and I could squeeze 3 hours out of my 6 cell battery.  It would also end up being cheaper...  

The problem is in the summer our electrical company sometimes kills the power for a few hours so I need the server to survive that.

---

### Post by cariboo on 2010-12-22
If you need power for that long, you may be better off with a portable generator.

---

### Post by nerdy_kid on 2010-12-22
> **cariboo907 said:**
> If you need power for that long, you may be better off with a portable generator.

:lolflag:


na I'll figure something out, thanks everyone :D

---

### Post by CharlesA on 2010-12-22
> **cariboo907 said:**
> If you need power for that long, you may be better off with a portable generator.

Indeed.

The point of a UPS is to give you enough time to shut the system down properly if the power goes out, not keep said system running for hours on end - that's what a generator is for.

---

### Post by LazyBubba on 2010-12-24
> **nerdy_kid said:**
> I am looking for a uninterruptible power supply for my web server and was wondering what everyone thinks of this one:  [http://www.newegg.com/Product/Product.aspx?Item=N82E16842101004](http://www.newegg.com/Product/Product.aspx?Item=N82E16842101004)

I don't want to spend over $130 and I need it to power just the server and the router (minus the screen and all that) for at least 3 hours, preferably around 8.  Is the one I linked good for all that?  It says battery time 11.7 but they forgot to mention whether that was minutes or hours lol


There's no way that you can get a complete UPS solution that will provide you 8 hours of run time for under $130.00. The only way you could come close to that kind of run time is by buying a good UPS and attaching several external sla marine batteries. But, it would still cost you more than $130.00.


For $130.00, you should expect about 4-10 minutes of run time.

---

### Post by johntaylor1887 on 2010-12-24
> **LazyBubba said:**
> 
For $130.00, you should expect about 4-10 minutes of run time.

I bought a $40 UPS at bestbuy and get at least 20 minutes.

---

### Post by grahammechanical on 2010-12-24
Hi Nerdy_kid

I like your approach to things.

> na I'll figure something out, thanks everyone

May I suggest that you work out what a UPS actually consists of and then try to build your own one.  It is a battery with a charging circuit. It must have a switch over mechanism and a circuit to convert battery DC voltage to mains AC voltage. There are technical words for these things but I cannot think of them just now. 

Batteries are rated according to how many Amps they can supply for an hour. You need to know how many Amps your server uses an hour. This way you can work out how long the battery will run the server and from that how many batteries are needed to keep the server running for as long as you need it to. 

By the way, car batteries are designed to provide a lot of power for a short time; when the vehicle is started. You want batteries that provide a certain level of power over a long period. I do not think vehicle batteries are suitable. 

Regards.

---

### Post by oldsoundguy on 2010-12-24
> **grahammechanical said:**
> (snip)

By the way, car batteries are designed to provide a lot of power for a short time; when the vehicle is started. You want batteries that provide a certain level of power over a long period. I do not think vehicle batteries are suitable. 

Regards.

But Marine deep cycle batteries and aircraft batteries will provide power over a much longer time.

One of our trucks had 4 big marine batteries on it .. because once the equipment was removed and on stage, the truck was turned into a dressing room for the performers.  The batteries would run the lights for about 6 hours.  We even had a 120V circuit using an inverter mounted in the box.  Charging was done via an over sized alternator attached to the engine.

---

### Post by nerdy_kid on 2010-12-24
> **grahammechanical said:**
> Hi Nerdy_kid

I like your approach to things.



May I suggest that you work out what a UPS actually consists of and then try to build your own one.  It is a battery with a charging circuit. It must have a switch over mechanism and a circuit to convert battery DC voltage to mains AC voltage. There are technical words for these things but I cannot think of them just now. 

Batteries are rated according to how many Amps they can supply for an hour. You need to know how many Amps your server uses an hour. This way you can work out how long the battery will run the server and from that how many batteries are needed to keep the server running for as long as you need it to. 

By the way, car batteries are designed to provide a lot of power for a short time; when the vehicle is started. You want batteries that provide a certain level of power over a long period. I do not think vehicle batteries are suitable. 

Regards.

see that is where I am going to try and do things a little different.  Why switch DC to AC when the AC just gets converted back into DC again?  I am thinking that a little "hacking" to the power supply can get me a similar battery runtime that my laptop gets from it's puny battery.  All I need is three (if I remember right) different DC voltages to power the whole pc, and I certainly can cook those up.  I'll have to do some research on how to get three voltages out of one battery, but it shouldn't be too hard.  The tricky part will be getting the AC power (when it is on) to charge the battery.  I'll need at least a relay, and I'll prob buy a crappy charger from ebay or something and take it all apart and wire it up using the schematic that I haven't made yet.  Its a rather crazy idea but I think it shall work :D  as far as the battery goes, have no fear I will not use a car battery :D  I'll prob end up disassembling my old laptop battery to see if laptop batteries would infact be able to work and if I could get that working then I would buy a 9 cell dell battery and hook that up.  If not, then... well I haven't thought of that yet

---

### Post by CharlesA on 2010-12-24
Just a word of warning - You should ***never*** open up a computer's PSU unless you have the proper training and tools to deal with the voltages inside.

---

### Post by t4thfavor on 2010-12-24
I took an old APC 1500, and hooked some cheapo 12v batteries to it for a friend, it lasted forever, and since it was already a fairly healthy UPS in the first place, it could handle the charging load of the extra batteries.

If you have 130 to spend, you could get a larger second hand ups without batteries, and 2 (or so) deep cycle marine batteries. They will last quite a while without mains, but charging will take forever unless you give it a boost with a higher amp charger.

Remeber that the battery voltage needs to be wired so that it matches what the original batteries supplied. Most are 48v, but you can find some that are 18v, and some that are 36v.

Good luck..

I also have 2 TrippLite 1500's that would power a small server for 4-5 (never tested longer) hours easily without modifications.

---

### Post by tgalati4 on 2010-12-25
A cheaper solution is to buy a used, business grade APC UPS and put in new batteries and solder some cables that lead outside of the case to support additional batteries.  You can get several hours of load with a fan attached to the unit for extra cooling.  Most UPS heat sinks can't handle more than an hour of load.

Be sure to get the metal case UPS's.  The plastic ones melt and catch fire.

---

### Post by t4thfavor on 2010-12-25
My point was to make the load as small as possible, ad the UPS as large as possible to increase the amount of time you can have the UPS off mains.

My server is a <60 watt mini-ITX, no monitor, and it will last for quite some time with a APC backUPS es550 My TC gear is on a slightly larget TrippLite Smart1500 and consists of a 2924 Cisco switch, an old PC based bsd router, and a generic cable modem. It will also last over an hour off mains. Plenty of time to fire up that second hand <100USD gas generator, that can keep me running for days if not weeks :)

It's all about building multiple levels of protection, if you can't depend on the mains, you have to find a way around it.

In my defense, I live in a very cold climate, and have a small child. If the power goes out for any time at all, I will need the generator anyways.

---

### Post by mips on 2010-12-26
> **CharlesA said:**
> Just a word of warning - You should ***never*** open up a computer's PSU unless you have the proper training and tools to deal with the voltages inside.

If disconnected from mains the worst you are going to get is a 500V jolt if you don't discharge the capacitors. Still not a nice feeling though but not as bad as a tv/monitor though, speaking from experience.

---

### Post by CharlesA on 2010-12-26
> **mips said:**
> If disconnected from mains the worst you are going to get is a 500V jolt if you don't discharge the capacitors. Still not a nice feeling though but not as bad as a tv/monitor though, speaking from experience.

True, I suppose, but still not worth the risk imo.

---

### Post by cascade9 on 2010-12-26
> **nerdy_kid said:**
> Maybe instead of using a UPS to supply AC power I could do some soldering and wire up a 20V lithium battery (plus some circuitry) that powers the server+router directly... cause my lappy is way more powerful then my server and I could squeeze 3 hours out of my 6 cell battery.  It would also end up being cheaper...  

Thats not going to work the way you would like it to IMO. 

Decent laptops use low power CPUs, 2.5'' HDDs, lower power GPUs (if thet even have a GPU), etc. Pretty much every low power trick they can think of. Desktops tend to use much higher powered parts. 

So even if your laptop is 'more powerful than your server' doesnt mean it eats anwhere near as much power as the server does. 

> **grahammechanical said:**
> By the way, car batteries are designed to provide a lot of power for a short time; when the vehicle is started. You want batteries that provide a certain level of power over a long period. I do not think vehicle batteries are suitable. 

Car batteries will work. Some of the thing I've seen powered by acar batteries make the average computer look like a LED ligthbulb (2000 watt angle grinders, MIG welders, stuff like that)  You'd want a battery of batteries to run a computer for any lenght of time though.

Car batteries are much better idea than laptop batteries IMO.

---

### Post by nerdy_kid on 2010-12-26
> **cascade9 said:**
> Thats not going to work the way you would like it to IMO. 

Decent laptops use low power CPUs, 2.5'' HDDs, lower power GPUs (if thet even have a GPU), etc. Pretty much every low power trick they can think of. Desktops tend to use much higher powered parts. 

So even if your laptop is 'more powerful than your server' doesnt mean it eats anwhere near as much power as the server does. 


good point about the HDDs, but I still think laptop batteries could work.  I can get an hour from my laptop gaming on it, with HDD going, my nvidia geforce 8600M pinned, my cpu working, and wireless going.  So in total the battery can handle CPU+GPU+HDD+wireless+LCD+speakers.
I don't think the router+server together use more energy then that.  The server is an older custom machine with a 3.2Ghz celron cpu 1gb ram and a terrible ATI gfx card.

I could always be wrong of course, as I haven't measured exactly how much energy my server uses.


> **cascade9 said:**
> Car batteries will work. Some of the thing I've seen powered by acar batteries make the average computer look like a LED ligthbulb (2000 watt angle grinders, MIG welders, stuff like that)  You'd want a battery of batteries to run a computer for any lenght of time though.

Car batteries are much better idea than laptop batteries IMO.

I don't think a car battery would be a good way to go, the voltages are too low (6-12).  I probably could rig up some converters to raise the voltage, but I think it would be simpler just linking two laptop batteries up if I needed too.  Also I do not know that much about building circuit boards and would be skeptical of building a converter dealing with that much electricity.



I'll scribble out a partial schematic when I get a chance and see what you all think.

---

### Post by markp1989 on 2010-12-26
> **nerdy_kid said:**
> see that is where I am going to try and do things a little different.  Why switch DC to AC when the AC just gets converted back into DC again?  I am thinking that a little "hacking" to the power supply can get me a similar battery runtime that my laptop gets from it's puny battery.  All I need is three (if I remember right) different DC voltages to power the whole pc, and I certainly can cook those up.  I'll have to do some research on how to get three voltages out of one battery, but it shouldn't be too hard.  The tricky part will be getting the AC power (when it is on) to charge the battery.  I'll need at least a relay, and I'll prob buy a crappy charger from ebay or something and take it all apart and wire it up using the schematic that I haven't made yet.  Its a rather crazy idea but I think it shall work :D  as far as the battery goes, have no fear I will not use a car battery :D  I'll prob end up disassembling my old laptop battery to see if laptop batteries would infact be able to work and if I could get that working then I would buy a 9 cell dell battery and hook that up.  If not, then... well I haven't thought of that yet


Depending on the amount of power your pc needs, you might be able to run it from a pico psu,  they take 12v DC instead of 120/240v AC so you  dont need to convert the dc voltage from the battery in to ac I use one in my server as it take up little space, and is very efficient, my server idles at about 30w .

If you pair the pico psu with a pico ups and a decent SLA battery you can probably make your own ups kind of thing 


Pico PSU: [http://www.mini-box.com/picoPSU-150-XT](http://www.mini-box.com/picoPSU-150-XT)

Pico UPS: [http://www.mini-box.com/picoUPS-120-12V-DC-micro-UPS-battery-backup?sc=8&category=981](http://www.mini-box.com/picoUPS-120-12V-DC-micro-UPS-battery-backup?sc=8&category=981) 

You could look at a Shivaplug ([http://www.plugcomputer.org/](http://www.plugcomputer.org/)) , its a small arm system about the size of a wallwart  sized box, only uses about 5w of power, so you could probably power that of  even a crap ups for a pretty long time.

---

### Post by nerdy_kid on 2010-12-26
> **markp1989 said:**
> Depending on the amount of power your pc needs, you might be able to run it from a pico psu,  they take 12v DC instead of 120/240v AC so you  dont need to convert the dc voltage from the battery in to ac,

interesting, thanks for the info.  I am not going to be converting the dc from the battery into ac anyway, but this still could be useful.

---

### Post by cascade9 on 2010-12-27
> **nerdy_kid said:**
> good point about the HDDs, but I still think laptop batteries could work.  I can get an hour from my laptop gaming on it, with HDD going, my nvidia geforce 8600M pinned, my cpu working, and wireless going.  So in total the battery can handle CPU+GPU+HDD+wireless+LCD+speakers.
I don't think the router+server together use more energy then that.  The server is an older custom machine with a 3.2Ghz celron cpu 1gb ram and a terrible ATI gfx card.

I could always be wrong of course, as I haven't measured exactly how much energy my server uses.

HDDs are the least of the power drains. 

8600M- 20watts TDP. 
Intel Core2Duo M CPU- 35watts (or less). 
LCD, could vary depending on size/tech, but probably 20-45watts. 

Intel 3.2GPU Celeron- 65-85watts (depending on model). 
Desktop P4s had pretty much none of the power saving features of moden CPUs, so its going to use more at idle compared to newer CPUs.

 I dont know what else is in your server, but if its anything like the age of the 3.2GHz celeron then its going to use a lot of power as well. The onlder cards tend to have a much higher idle power consumption, and closer levels between idle and full power than modern cards. 
Eg, a x800GT (simialr age to the 3.2GHz celery) uses 27watts idle, 68watts at full load. 

Even without the video card, I'd guess that your celeron CPU alone will pull as much as the whole laptop, and that the whole system at idle uses abotu as much as the laltop does at full load. At full load, the celeron could use 4 times or more power than the laptop. 

I was going to say stuff about car batteries vs laptop batteries, but next time, I've I've got to go out.

---

### Post by mips on 2010-12-27
> **nerdy_kid said:**
> good point about the HDDs, but I still think laptop batteries could work.  I can get an hour from my laptop gaming on it, with HDD going, my nvidia geforce 8600M pinned, my cpu working, and wireless going.  So in total the battery can handle CPU+GPU+HDD+wireless+LCD+speakers.
I don't think the router+server together use more energy then that.  The server is an older custom machine with a 3.2Ghz celron cpu 1gb ram and a terrible ATI gfx card.

I could always be wrong of course, as I haven't measured exactly how much energy my server uses.


Your laptop at peak usage will not consume more than about 65W of power. With the LCD off and CPU throttled back it will use even less.

There is no way your server will use that little power, it will probably use about x2-x3 as much if not more.

If your web server is not to intensive in usage you could use one of those low power single board computers with a 2.5" HDD to run your server on as it consumes like 5-10W of power. You can use a plug computer with USB for the HDD or companies like Marvell have some very nice low power development boards that have LAN/SATA2/USB/VGA interfaces, some use as little as 1W. This would be the more logical solution to your problem.

---

### Post by cascade9 on 2010-12-27
Car batteries tned to hae a huge amount more mAh (millampere-hours) than laptop batteries. 

Car batteries can hit over 50,000 mAh. I cant recall ever seing a laptop battery with more than 7200 mAh. 

Not that mAh is a unit of energy, but it does give you an idea about how much more power a car battery has compared to laptop batteries......

---

