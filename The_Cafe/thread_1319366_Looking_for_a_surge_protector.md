---
title: "Looking for a surge protector"
date: 2009-11-08
forum: The Cafe
---

### Post by blueshiftoverwatch on 2009-11-08
What's a good quality surge protector is that's less than $50? I was looking at [this one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812107131&cm_re=surge_protector-_-12-107-131-_-Product"). The stats look pretty good based on what little I know about surge protectors.

My house already has a surge/lightning protector built into the fuse box. My main concern is power spikes/sags that originate from within the house. Every time my refrigerator comes on the lights dim for several seconds, which can't be good for my equipment.

It would also be nice to have something with some sort of indicator light that would tell me when the unit has become worn out after years of stabilizing the power supply so that I know I actually have my equipment plugged into a surge protector instead of a glorified extension cord.

---

### Post by Paqman on 2009-11-08
> **blueshiftoverwatch said:**
> Every time my refrigerator comes on the lights dim for several seconds, which can't be good for my equipment.


It certainly won't be. Fridge motors are actually the biggest perpetrators of nasty transients on your home power supply. That's not good for electronics.

---

### Post by pwnst*r on 2009-11-08
[http://www.staples.com/APC-Back-UPS-ES-550VA-8-Outlet-Green-UPS/product_733726](http://www.staples.com/APC-Back-UPS-ES-550VA-8-Outlet-Green-UPS/product_733726)

that's in your price range.  i have the 750 and i absolutely love it.

---

### Post by blueshiftoverwatch on 2009-11-08
> **pwnst*r said:**
> that's in your price range.  i have the 750 and i absolutely love it.
I've never even looked at UPS's before because I just assumed they were overkill. How much more effective are UPS's than just a standard surge protector? Since it delivers a constant stream of power from the battery instead of directly from the line like a surge protector does, does that mean my equipment will be safe from pretty much any kind of power surge/sag short of a direct lighting strike to a nearby telephone pole?

The one you listed had an alarm that sounds when the battery gets low. Would it be loud enough to wake someone up from sleeping if the power went out at night and their bed was less than 10 feet away? It said it includes software to automatically shut the system down if your not around to manually do it. But I'm going to assume it's not Linux compatible.

---

### Post by Paqman on 2009-11-08
> **blueshiftoverwatch said:**
>  I'm going to assume it's not Linux compatible.

Actually quite often they are, since UPSes are commonly used with servers. Probably best to check with the manufacturer before you buy though.

---

### Post by Kevbert on 2009-11-08
UPS are good at protecting mains provided they are regularly tested (i.e. check that when the UPS power cord is removed the power is maintained). I used to work in a service department where we would regularly see failing UPS come in after bad weather/lightning strikes as the battery had never been discharged (and had the old memory effect like ni-cad batteries have).
I'm currently using a Zigor 850 UPS (which has a front panel display, but doesn't work directly with Linux). A good alternative is the SmartUPS made by APC which is supported by both Linux and Windows. Have a look at apcupsd by doing a search in Synaptic. You need a UPS that you can mute the audio alert when the UPS goes on to battery after an event.

---

### Post by CharlesA on 2009-11-08
Thanks for the info about apcuspd. Now I need to figure out if my BackUPS-ES 550 is supported and figure out how to configure it.

---

### Post by tom66 on 2009-11-08
Most surge protectors only last 2-3 surges.

They are also fire hazards. If there is a continued surge, unlike a fuse, they will not fail instantly and instead overheat and catch fire.

Just get a power supply with overvoltage protection. If a power supply gets fried it's not so bad.

---

### Post by pwnst*r on 2009-11-09
nah, get the UPS.

---

### Post by cascade9 on 2009-11-09
> **blueshiftoverwatch said:**
> I've never even looked at UPS's before because I just assumed they were overkill. How much more effective are UPS's than just a standard surge protector? Since it delivers a constant stream of power from the battery instead of directly from the line like a surge protector does, does that mean my equipment will be safe from pretty much any kind of power surge/sag short of a direct lighting strike to a nearby telephone pole?

Watch out, a lot of the cheaper UPSes are actually SPSes (standby power supplies). SPSes dont constantly stream power though the battery. 

[http://www.pcguide.com/ref/power/ext/ups/typesStandby-c.html](http://www.pcguide.com/ref/power/ext/ups/typesStandby-c.html)

When your talking what they use in server rooms, etc, they tend to be Online UPSes. They work a little differently to SPSes. 

[http://www.pcguide.com/ref/power/ext/ups/typesOnLine-c.html](http://www.pcguide.com/ref/power/ext/ups/typesOnLine-c.html)

Personally, I prefer a good surge protector to a SPS. SPSes (and UPSes) use environmentally nasty batteries, are heavy and hard to move around, etc.

---

### Post by pwnst*r on 2009-11-09
> **cascade9 said:**
> Watch out, a lot of the cheaper UPSes are actually SPSes (standby power supplies). SPSes dont constantly stream power though the battery. 

[http://www.pcguide.com/ref/power/ext/ups/typesStandby-c.html](http://www.pcguide.com/ref/power/ext/ups/typesStandby-c.html)

When your talking what they use in server rooms, etc, they tend to be Online UPSes. They work a little differently to SPSes. 

[http://www.pcguide.com/ref/power/ext/ups/typesOnLine-c.html](http://www.pcguide.com/ref/power/ext/ups/typesOnLine-c.html)

Personally, I prefer a good surge protector to a SPS. SPSes (and UPSes) use environmentally nasty batteries, are heavy and hard to move around, etc.

[http://nam-en.apc.com/cgi-bin/nam_en.cfg/php/enduser/std_adp.php?p_faqid=9223&p_created=1206033806&p_topview=1](http://nam-en.apc.com/cgi-bin/nam_en.cfg/php/enduser/std_adp.php?p_faqid=9223&p_created=1206033806&p_topview=1)


which is one of the models i linked to.

---

### Post by cascade9 on 2009-11-09
> **pwnst*r said:**
> [http://nam-en.apc.com/cgi-bin/nam_en.cfg/php/enduser/std_adp.php?p_faqid=9223&p_created=1206033806&p_topview=1](http://nam-en.apc.com/cgi-bin/nam_en.cfg/php/enduser/std_adp.php?p_faqid=9223&p_created=1206033806&p_topview=1)


which is one of the models i linked to.

Which is an SPS.  See here-

[http://www.apc.com/prod_docs/results.cfm?DocType=White%20Paper&Query_Type=3&Value=21](http://www.apc.com/prod_docs/results.cfm?DocType=White%20Paper&Query_Type=3&Value=21)

Go to "The different types of UPS systems" , dl (or just open it, no matter) then see page 9. APC Back-UPS models are Standby only. Yeah, its got backup power for a blackout, and does use the battery during brownouts but apart from that its just another surge protector/filter.  

BTW, from what I remember the clamping time on the low-end SPS UPSes is worse than a good surge protector/flter. Which is another reason why I dotn like low-end UPSes.

---

### Post by pwnst*r on 2009-11-09
ok.... i was referring to it's green feature.  you're the one tossing around sps as opposed to ups, for which i don't care about that since i know the difference.

---

### Post by pwnst*r on 2009-11-09
[http://www.bestbuy.com/site/APC+-+550VA+Battery+Back-Up+System+-+Black/9307788.p?id=1218081368684&skuId=9307788&st=apc](http://www.bestbuy.com/site/APC+-+550VA+Battery+Back-Up+System+-+Black/9307788.p?id=1218081368684&skuId=9307788&st=apc)

---

### Post by cascade9 on 2009-11-10
LOL, if you knew the difference between an SPS and a UPS, it would have been nice to say that to blueshiftoverwatch. ****

As for 'green' it might be more efficient than previous SPS/UPS models, and might come with a RoHS stamp, but its still packed with a lead/acid battery. Lead is nasty nasty stuff. 
****

---

### Post by blueshiftoverwatch on 2009-11-10
> **cascade9 said:**
> LOL, if you knew the difference between an SPS and a UPS, it would have been nice to say that to blueshiftoverwatch. ****
?

---

### Post by HappyFeet on 2009-11-10
> **blueshiftoverwatch said:**
> I've never even looked at UPS's before because I just assumed they were overkill.

I paid $45 for my UPS. I am sooooo glad I did, because we get frequent surges and brown outs in my area. I think all those surges killed a previous computer before I got a UPS.

---

### Post by The Real Dave on 2009-11-10
I've a Belkin surge protector, 4 plug, with dsl protection, a lifetime warrenty and guarntee in the region of 15,000Euro (though more expensive models go higher), for the low cost of 35Euro at my local hardware store. I bought a few, I love Belkin kit :)

---

### Post by necromonger on 2009-11-10
here is a good story a friend of mine had the best apc on the market lighting hit his home fried fridge heat pump 2 tv's freezer every thing but his computer.Get a whole house surge protector or ond you will pay his price.10 thousand dollars.

---

### Post by Joebubba360 on 2009-11-10
Having worked for a electric utility for over 10 years in their training department, I'd recommend one of the following: [http://www.tripplite.com/en/products/product-series.cfm?txtSeriesID=77&EID=78](http://www.tripplite.com/en/products/product-series.cfm?txtSeriesID=77&EID=78)
Nice to have insurance if your electronics get fried while using one of their units.

I have several of the tripplite iso-bars protecting my electronics at home in Texas where we get some very spectacular lightning storms. Never had a problem, except for the microwave that got fried because I didn't have a surge suppressor on it. (forgot about it)

UPS, to be of any use have to be rather large, expensive, and most consumer units are not the 100% run load/total isolation type. UPS for personal use is typically not recommended or needed unless you have processing tasks that must not stop for any reason. (Rare for a home user.)

A good surge suppressor is all that is really needed. Most use several transorbs to absorb the energy spike(s) between hot and neutral and neutral and ground (common mode). _They should also trip the unit off when the power drops out, requiring a manual reset_. Once the power goes down, you want it to STAY DOWN. The electrical 'bang' (called ringing) caused by the power going down isn't so bad, its the upswinging spike when the power comes back up that's the electronics killer. This is where the voltage clamp time rating of the transorbs comes into play. Good ones clamp very very fast (microseconds). 

Now, for the more important part. If your lights dim when your refrigerator comes on, that indicates major problems in your power system. You should get these looked at by an electrician very soon. You could have any number of issues causing this, all are bad: Undersized power panel and/or power feed, poor electrical connections due to loose wires and/or corrosion, ALUMINIUM WIRING W/O TRANSISTIONS TO COPPER (danger Will Robinson danger!!!!!), etc. 

The power panel ground is another often over looked part of the electrical protection system. More often than not, common mode noise, which is the power spikes that exist between the ground line and the neutral side of the line in, are the biggest cause of electronics dammage. With a good ground, the potential between the ground and the neutral side of the line due to inductive loads starting and stopping, (AC units, fans, refrigerators, etc.) should be <20VAC reactive. I have personnaly seen this value exceed 200 VAC reactive on a 120VAC line. This is not only is very dangerous to electronics, it is generally not very healthy for humans as well (as in potentially lethal).

I hope this helps.

---

### Post by blueshiftoverwatch on 2009-11-11
> **Joebubba360 said:**
> I'd recommend one of the following: [http://www.tripplite.com/en/products/product-series.cfm?txtSeriesID=77&EID=78](http://www.tripplite.com/en/products/product-series.cfm?txtSeriesID=77&EID=78)
I'll have a look at those. Why do most surge protectors not protect ethernet cables as well, is it mostly unnecessary?
> **Joebubba360 said:**
> Nice to have insurance if your electronics get fried while using one of their units.
They probably don't have many people taking them up on their warranties. But when they do, how often do companies actually make good on them? I've been sort of ignoring the warranties because I figured that when your dealing with huge companies they'll find some way to weasel out of holding up their end of the contract.
> **Joebubba360 said:**
> Now, for the more important part. If your lights dim when your refrigerator comes on, that indicates major problems in your power system. You should get these looked at by an electrician very soon. You could have any number of issues causing this, all are bad: Undersized power panel and/or power feed, poor electrical connections due to loose wires and/or corrosion, ALUMINIUM WIRING W/O TRANSISTIONS TO COPPER (danger Will Robinson danger!!!!!), etc.
It's only that one particular breaker that does that, the rest of the house is fine. Apparently when my house was built they hadn't heard of the idea of wiring one room to one circuit. So we'll have every outlet in one room on X circuit and except for one outlet that's on Y circuit, in my case the refrigerator and my computer are even on different floors. Probably the best coarse of action would be to get a long heavy extension cord and plug the refrigerator into another outlet to balance out the load.

Thanks for the detailed response.

---

### Post by BulletTootg on 2009-11-16
> **blueshiftoverwatch said:**
> I've never even looked at UPS's before because I just assumed they were overkill. How much more effective are UPS's than just a standard surge protector? Since it delivers a constant stream of power from the battery instead of directly from the line like a surge protector does, does that mean my equipment will be safe from pretty much any kind of power surge/sag short of a direct lighting strike to a nearby telephone pole?

The one you listed had an alarm that sounds when the battery gets low. Would it be loud enough to wake someone up from sleeping if the power went out at night and their bed was less than 10 feet away? It said it includes software to automatically shut the system down if your not around to manually do it. But I'm going to assume it's not Linux compatible.




A UPS is a much better investment. Surge protectors are nice but they don't do that much. Surges are only a small problem of different power problems that occur. For us we routinely have power sags thanks to the firm next door that turns on some heavy equipment. We've burnt out a few power supplies already and had some hardware failure. If the equipment is important, you should protect it with a proper UPS. We use several [SmartUPS 1500]("http://excessups.com/smartups-1500-sua1500-p-38.html")'s, they're more industrial than some of the other UPSs recommended. The 1500 has big batteries, outputs a sine wave, has avr boost/drop, power filtering and provides us a decent run time.


We also put our switches on the UPSs to make sure they're protected as well. If you're going to look for a UPS make sure you add up all your equipment first to know what kind of draw you have. Also, keep in mind not to load a UPS more than 80%, they run much less reliable at that point. My personal preference are the Smart UPS series, they're notoriously reliable.



T

---

### Post by blueshiftoverwatch on 2010-01-12
I ended up getting the [Tripp Lite TLP810NET]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812120302").

---

