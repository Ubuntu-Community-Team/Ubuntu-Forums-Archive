---
title: "Another fraud, I find cables labelled cat 6 dont work"
date: 2013-01-17
forum: The Cafe
---

### Post by sdowney717 on 2013-01-17
I bought a new 100 foot CMPLE cat6 500mhz grey cable.
Which of course was no good, my luck.
I did get a full refund including shipping

As soon as I got it it was overflowing its tiny box.
then I noticed the ends were melted.
Then I look at the 'gold' connectors and they look oddly tarnished
Then I plug it in and of course can only connect at 100, not at gigabit speeds.

I was wondering if it is worth it to put new ends on this and see if it can work at gigabit speeds?

I peeled back the cracked cover and do these wires look like it has enough twist?


What is a known good working cat 6 brand to buy?

some pics
[IMG]https://lh6.googleusercontent.com/-7Qg5TG9dxyc/UPgPrhwfbEI/AAAAAAAAEYo/KwAITGi8k9w/s1024/SS850845.JPG[/IMG]

[IMG]https://lh4.googleusercontent.com/-rHBQ8TekZAY/UPgPap51fkI/AAAAAAAAEYY/vDSt0Uyf-u8/s1024/SS850854.JPG[/IMG]

---

### Post by dannyboy79 on 2013-01-17
you don't need cat6 cables to get gigabyte speeds. check your ethernet ports on your boxes are set to full duplex. not sure where you heard that only cat6 cables produce gigabyte speeds? if the NIC is gigabyte, you'll get gigabyte speeds as long as both NICs are gigabyte

---

### Post by sdowney717 on 2013-01-17
All of my other cables are cat 5e and only 2 dont work at gigabit speed.

When I buy new cables I buy cat 6.

I have seen pictures of good looking cat6 where you can see the twists on the outer jacket and the cables look thicker.

This cat6 I bought is not any thicker than my cat5e cables and feels and looks the same.


So this looks better, any ideas?
Who would sell local at decent price? I am so used to buying online, I dont know where to go.
[http://www.pccables.com/cgi-bin/orders6.cgi?action=Showitem&id=ID15356988&partno=03799&search=CAT6&rsite=&rcode=](http://www.pccables.com/cgi-bin/orders6.cgi?action=Showitem&id=ID15356988&partno=03799&search=CAT6&rsite=&rcode=)

[IMG]http://www.pccables.com/images/100FT_CAT6_RJ45_NETWORK_CABLE.jpg[/IMG]

---

### Post by sdowney717 on 2013-01-17
Notice the huge twist diff between cat5 and cat6?

The cable I bought has very little twist, and consequently, of course born out by it did not work. 
Looking at this example, the cable I bought looks most like cat5.

[IMG]http://www.howtogeek.com/wp-content/uploads/2011/08/twist-comparison.png[/IMG]

[http://www.howtogeek.com/70494/what-kind-of-ethernet-cat-5e6a-cable-should-i-use/](http://www.howtogeek.com/70494/what-kind-of-ethernet-cat-5e6a-cable-should-i-use/)

---

### Post by Roasted on 2013-01-17
I bought a box of Cat6 cable from Home Depot, along with Cat6 connectors since nobody else in the area had any. I did my wiring job without issue and am quite happy with my Cat6 network at home. I very rarely buy pre-made cables since most of the cabling I do requires a very specific length, hence the box + connectors plan.

---

### Post by tgalati4 on 2013-01-17
There is a lot of crappy cable out there.  I make my own cables with Belden or Gepco (made in USA) cable, and decent Cat6 crimps.  A crimping frame is not that expensive and testing my cables vs store-bought has always shown that I get higher throughput with my own handywork.

---

### Post by Grenage on 2013-01-17
Structured cabling we obviously punch down, but I tend to buy in patch cables.  crimping cat6 to within spec in a PITA, and I know they are unlikely to be as good as a factory-form.

---

### Post by sdowney717 on 2013-01-17
Do you think buying Cat 7 would be more likely to work than cat 6 for my gigabit lan?

Item is 
Rosewill RCW-100-CAT7-BL 100 ft. Cat 7 Blue Shielded Twisted Pair (S/STP) Networking Cable
NewEgg sells for $20

Shielded cable, after buying what was supposed to be cat6 and getting garbage, I think maybe jump to cat7 might give me better chance of it working.
What do you think? I dont want to waste my time on lousy cables.

---

### Post by tgalati4 on 2013-01-17
One of the issues with buying 100-foot patch cables is that they are made with stranded cable.  OK for short patch cables and vibration environments, but you get a lot of signal loss with stranded cable at that distance.  That is why crimping your own cable (from a quality-controlled wire supplier) with solid copper cable makes sense at these distances.

And it's true, punchdowns and 3' to 6' patch cables don't fit this do-it-yourself category.  But for most home/small business structural wiring, you are better served crimping your own than relying on a 100' pre-made cable--if you want high performance.

---

### Post by sdowney717 on 2013-01-17
I have an 80 ft section of cat 5e running under the house which works most of the time at gigabit speeds. I get from 35 to 50MB/sec
Cable ends go into straight thru joiner female couplers set into the wall. Then I plug a short patch cord to PC and switch.

Sometimes the connection drops down to 100, or on a boot. Then I have to unplug and replug to restore 1000. Once it settles on a 100, you got to unplug and replug, it never adjusts itself higher.
This was with direct connection from PC to PC

Couple days ago I started using a 5 port trendnet gigabit switch, and will see if it stays on 1000. So far it seems to be more likely to stay at 1000.

So was wondering if that cat5e is sort of borderlne, works when it feels like it and if upgrading the cable would make it work better.

---

### Post by CharlesA on 2013-01-17
> **sdowney717 said:**
> 
So was wondering if that cat5e is sort of borderlne, works when it feels like it and if upgrading the cable would make it work better.

Depends on the cable quality. I've seen some CAT5e that would only run at 100mbps but the stuff I have runs at 1Gbps.

---

### Post by tgalati4 on 2013-01-17
Cat5e is "enhanced Cat5" rated at ~350 Mbits/sec or about 1/3 of gigabit speeds.  So although the router endpoints detect signal on 4 data pairs, the actual throughput is short of gigabit speeds and thus the routers will downselect to 100 mbits (Cat5 speed).  Cat5e simply means the cable passes a 350 MHz pulsed signal without too much rounding of the square waves.  By passing Cat5e specification, you can be resonably sure that you will get 100 Mbit/sec speeds out of that cable.  

With gigabit speeds, you really need 3 GHz performance out of that cable, and now we are talking microwave frequencies and different RF physics involved.  Just like you can conduct an audio signal with a coat hanger, but not video signal, high speed ethernet requires careful attention to cable construction, crimp, bend radius, and your endpoint equipment.

---

### Post by Bandit on 2013-01-17
When it comes to Cat 5, 5e and 6 cables, they will all physically work at 1000 base-T. This is because 10 and 100 base-T only require 2 pairs of cables, while 1000Base-T needs 4. The difference in Cat 5 and Cat 5e was the pitch of the cables to reduce cross talk. I used to think the "e" meant shielded, but I was wrong.  Now Cat 6 is the industry standard for Gigabit Ethernet and is recommend for that application. Reason being while many Cat5 & 5e cables can work at 1000Base-T, some companies try to save money and drop the twist per meter to the bare minimum to save on cost thus opening up cross talk and causing packet interference on the network and over all speed. Traditionally Higher Quality 5 & 5e cables from respectable brands offer more twist per meter then that of the Cat 5 & 5e specification requires, but your taking a gamble in todays hurting market. So best to stick to Cat6 and know its gonna work.

---

### Post by sidzen on 2013-01-17
i never had a cat5 or cat6 cable from monoprice.com fail me, so far.  by far the cheapest i've found, too

---

### Post by pqwoerituytrueiwoq on 2013-01-17
i have a 8ft that only works with some computers, and i have a 100ft that always works that was $6

i don't have a gigabit router

can you confirm your nic  can do 1gbps

---

### Post by CharlesA on 2013-01-17
> **Bandit said:**
> Traditionally Higher Quality 5 & 5e cables from respectable brands offer more twist per meter then that of the Cat 5 & 5e specification requires, but your taking a gamble in todays hurting market. So best to stick to Cat6 and know its gonna work.

+1. I have seen some really, really bad CAT5 and CAT5e but I haven't really dealt with CAT6.

> **sidzen said:**
> i never had a cat5 or cat6 cable from monoprice.com fail me, so far.  by far the cheapest i've found, too

monoprice is awesome.

---

### Post by sdowney717 on 2013-01-18
The nics or switches try to negotiate a gigabit speed. If the cable is sub par, perhaps not enough twists, then they can't do it. I have read many places that loosing the twist cant exceed 1/2 inch. And a lot of the problem is in the connector.

Then there is cross talking. If they can negotiate a gigabit speed, if the cable is sub-par, there may be so much cable noise that the gigabit throughput drops or the connection speed might auto drop lower to 100. (I think I have seen it.)

So far with the trendnet 5 port gigabit switch, the connection has stayed at a 1000. :p

I would have to crawl under the house to string another cable and that is no fun. 

I get up to 50MB/sec right now. I wonder if I could get much better than that even using a better cable.

---

### Post by sdowney717 on 2013-01-18
Regarding cat 6 terminations, I saw you can get terminal ends where the wire passes out the end and it allows you to snug it up real tight.
So I took some ends and used a tiny drill about 1.05mm to drill a hole for it. Then was able to pass the wires out and snug it up tight perhaps less twist loss. One advantage I immediately saw was I could easily verify the color coding.

Here I fixed another cable where the end was messed up. I do have a crimper.
[IMG]https://lh3.googleusercontent.com/-ec3D7CvoVbY/UPgPjz_XbwI/AAAAAAAAEYg/BxlsExESNic/s1024/SS850850.JPG[/IMG]

---

### Post by mips on 2013-01-18
> **sdowney717 said:**
> 
I would have to crawl under the house to string another cable and that is no fun. 

Or you could just use the existing cable as a draw wire...

---

### Post by sdowney717 on 2013-01-18
> **mips said:**
> Or you could just use the existing cable as a draw wire...

My worry would be the new cable would be damaged and then have nothing.
I have access everywhere, still have holes I cut in the garage ceiling I can use. If you draw, the big problem is from sill plate to wall in the crawl space, the cable will want to jam. The cable snakes around. it is not a direct run.

I wish the house had a full basement.

---

### Post by tgalati4 on 2013-01-18
You want to avoid sharp bends in the cable and you don't want to pull more than 35 lbs.  I use a rated pull string, but if it breaks, you end up crawling!

Also, keep it off of the ground under the house, because critters like to chew it.  A coil of Cat6 must look like a snake in the dark.

---

### Post by CharlesA on 2013-01-18
> **tgalati4 said:**
> 
Also, keep it off of the ground under the house, because critters like to chew it.  A coil of Cat6 must look like a snake in the dark.

Indeed. I've seen people run network cable thru a length of PVC to protect it.

---

### Post by pqwoerituytrueiwoq on 2013-01-19
> **sdowney717 said:**
> I wish the house had a full basement.
granted, but it is flooded

i wish the Linksys WTR54GL had a gigabit LAN 

> **sdowney717 said:**
> Also, keep it off of the ground under the house, because critters like  to chew it.  A coil of Cat6 must look like a snake in the dark. 	
is outdoor rated coax safe on the ground (covered with a sheet of plastic) under a house?

---

### Post by tgalati4 on 2013-01-19
There's no problem with running cable on top of the ground, as long as the jacket is intact.  It will remain waterproof.  But when critters run across it, they instinctively attack it causing teeth marks that break the PVC jacket.  Moisture and corrosion soon follow.  You can also fly it high in the trees, then the squirrels use it as a trapeze and they chew it as well.

---

