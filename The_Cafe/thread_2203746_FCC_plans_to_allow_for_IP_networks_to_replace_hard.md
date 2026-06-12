---
title: "FCC plans to allow for IP networks to replace hard wired telephone systems"
date: 2014-02-04
forum: The Cafe
---

### Post by SurfaceUnits on 2014-02-04
[h=1]The U.S. Federal Communications Commission on Thursday voted to allow  telecom carriers to experiment with Internet Protocol networks replacing  traditional, copper-based telephone systems. The eventual goal is the  retiring of copper-based facilities.[/h][HR][/HR]             [HR][/HR]  
   According to FCC Chairman Tom Wheeler, the goal is to test the impact on  telephone customers, on emergency services and other issues. Problems  will be examined such as the service interruptions on  electricity-dependent IP networks.

The test won’t be a technology trial, Wheeler said. “We know how to build IP networks.”

“We  cannot continue to require service providers to invest in both old  networks and new networks forever,” said Commissioner Ajit Pai. “Every  dollar that is spent maintaining the networks of yesterday is a dollar  that cannot be invested in the networks of tomorrow.”

---

### Post by TheFu on 2014-02-05
Telcoms have been using VoIP for many years - since 2002 at least. It is just old laws that required POTS access through the universal access act forcing the RBOCs in the USA to provide that service to every address.

Most people didn't know that some RBOCs built completely separate IP and POTS networks to avoid local utility commission regulation of the IP networks. Sometimes the local commissioners would abuse their power for personal needs (look at phone LATA diagrams) and sometimes they would keep force huge "local" calling areas (look at metro Atlanta). LATAs are like area codes, but smaller. Calls that cross 1 LATA are usually considered "local", but calls that cross 2 LATAs are long distance. Before we all had LD included in our normal telephone service, the phone call from NY to LA was always cheaper than the LD call over 2 LATAs.

Since IP is not Public Utility Commission regulated, the RBOCs will be free to do what makes the most business sense. This can be great or terrible. It is unclear which. Historicly the RBOCs have been slow to offer VoIP services similar in capability and price from what others offer.  My neighbors pay about $30/month for POTS service without LD.  I pay $5/month for VoIP with a 3rd party provider and free inbound calls. By using Google-Voice to start all calls, they all appear as inbound, thus included in my usage.

If VoIP is allowed to replace POTS for universal service, then the PUC would necessarily regulate service. I think this is the hidden agenda. The RBOCs want out of the PUC regulation.

---

### Post by MoebusNet on 2014-02-06
If I understand the legalisms correctly, the traditional Plain Old Telephone System (POTS) requires law enforcement officials to obtain a court order from a judge before a wiretap can be installed. An IP-based telephone system would be treated the same as any other Internet data and would have to clear a significantly lower legal barrier to intercepting communications (by NSA, for example).

Am I mistaken in this understanding?

---

### Post by SuperFreak on 2014-02-06
Forgive my ignorance on this, I have never used VOIP service or had a cell phone. How would one connect to emergency services in a power failure ? Presumably in a prolonged power failure cell phones would run out of power and couldn't be recharged. VOIP wouldn't work at all in this scenario unless powered by alternative energy sources (small solar panel?). I was without power in December for about 3 days due to an icestorm but my back up, non cordless phone worked

---

### Post by MoebusNet on 2014-02-06
@SuperFreak: The traditional Plain Old Telephone System relies on a low-voltage signal modulated to carry communications over a copper wire network. The telephone network power is separate from the electric utility system's household power system, which is why it may work when your local neighborhood power is out. An IP-based system requires you to provide the power for your digital telephone, and the IP network power must be available as well.

---

### Post by SuperFreak on 2014-02-06
So if POTS was discontinued there would be no emergencies services for many people in the event of a prolonged power failure...Sounds like Pandæmonium to me not progress

---

### Post by TheFu on 2014-02-06
> **SuperFreak said:**
> Forgive my ignorance on this, I have never used VOIP service or had a cell phone. How would one connect to emergency services in a power failure ? Presumably in a prolonged power failure cell phones would run out of power and couldn't be recharged. VOIP wouldn't work at all in this scenario unless powered by alternative energy sources (small solar panel?). I was without power in December for about 3 days due to an icestorm but my back up, non cordless phone worked

E911 systems were put in over a decade ago. I was responsible for upgrades at a HUGE RBOC for a few years. These provide DB lookups for VoIP services based on the records from users. If a user moves or uses a portable VoIP device, there might be issues. Generally, it is not a big problem since 911 operators are trained to get location data on the call too. There is a mandatory government fee for E911, at least for USA-based VoIP providers.  Comcast VoIP devices have a battery backup included for the house. A dumb-phone connected will work the same. I don't know about cable infrastructure power backup - never worked for a cable company.

VoIP systems can be either native SIP phones or they can use an ATA device to convert normal phones into SIP.  If you own your own ATA, putting it on a UPS is a smart thing for a few reasons. They draw very little power, but the entire network equipment would need to have UPS - modem, router, any switches, ATA and any phones you'd like to use. With a 6-handset phone system at my house, this is the case and easy to accomplish.  The handsets are rechargeable and placed around the home for convenience.  In short, it is a change, but not THAT difficult. Plugging in a standard RJ11-only phone would still work provided the ATA thru to the modem are on a UPS.  If an RBOC deployed this stuff, I'm almost positive that a battery backup would be included to handle small outage periods - less than 6 hrs.

Another consideration is if any other devices use the VoIP line - home alarm systems and home medical devices like pace makers or defibrillators that call home. VoIP may or may not work with those protocols. The signaling is different.  Many people have issues with FAX machines too. Something to be aware, but hardly a show-stopper.

In the USA, cell phones have had GPS enabled for 911 calls for a very long time and cell towers should have 4-6 hrs of battery backup, just like POTS DSLAMs do.  I worked at 2 different RBOCs over the years.

For the last 10 yrs, I've been on VoIP and was comfortable doing because a cell phone was available AND nobody normally in the house was likely to need emergency services.  If your family has someone with needs to access 911, I would be concerned and very cautious about switching to VoIP.  Getting a huge (900VA) UPS just for the networking and ATA would be smart. I would guess that would cover at least 24 hrs, maybe more of being off the power grid. With a car, charging the cell phone should basically be unlimited, right?

---

### Post by SuperFreak on 2014-02-06
> **TheFu said:**
> E911 systems were put in over a decade ago. I was responsible for upgrades at a HUGE RBOC for a few years. These provide DB lookups for VoIP services based on the records from users. If a user moves or uses a portable VoIP device, there might be issues. Generally, it is not a big problem since 911 operators are trained to get location data on the call too. There is a mandatory government fee for E911, at least for USA-based VoIP providers.  Comcast VoIP devices have a battery backup included for the house. A dumb-phone connected will work the same. I don't know about cable infrastructure power backup - never worked for a cable company.

VoIP systems can be either native SIP phones or they can use an ATA device to convert normal phones into SIP.  If you own your own ATA, putting it on a UPS is a smart thing for a few reasons. They draw very little power, but the entire network equipment would need to have UPS - modem, router, any switches, ATA and any phones you'd like to use. With a 6-handset phone system at my house, this is the case and easy to accomplish.  The handsets are rechargeable and placed around the home for convenience.  In short, it is a change, but not THAT difficult. Plugging in a standard RJ11-only phone would still work provided the ATA thru to the modem are on a UPS.  If an RBOC deployed this stuff, I'm almost positive that a battery backup would be included to handle small outage periods - less than 6 hrs.

Another consideration is if any other devices use the VoIP line - home alarm systems and home medical devices like pace makers or defibrillators that call home. VoIP may or may not work with those protocols. The signaling is different.  Many people have issues with FAX machines too. Something to be aware, but hardly a show-stopper.

In the USA, cell phones have had GPS enabled for 911 calls for a very long time and cell towers should have 4-6 hrs of battery backup, just like POTS DSLAMs do.  I worked at 2 different RBOCs over the years.

For the last 10 yrs, I've been on VoIP and was comfortable doing because a cell phone was available AND nobody normally in the house was likely to need emergency services.  If your family has someone with needs to access 911, I would be concerned and very cautious about switching to VoIP.  Getting a huge (900VA) UPS just for the networking and ATA would be smart. I would guess that would cover at least 24 hrs, maybe more of being off the power grid. With a car, charging the cell phone should basically be unlimited, right?

Power failures can last longer than 24 hours (see my first post) and when they do emergency services become more important not less. I do use a UPS on my computer so I see that as a stopgap. We have had  two power failures lasting over 24 hours in the last 15 years and barley missed another in 1998 that affected millions of people in Quebec and Eastern Ontario. While these things don't happen very often I would be very concerned for my family's safety if we didn't have quick access to emergency services. Until this issue is resolved I don't think discontinuing POTS (which worked in all those power failures lasting days) is a good idea.
> With a car, charging the cell phone should basically be unlimited, right?
 I do not own either a cell phone or a car so that would not help me.

---

### Post by TheFu on 2014-02-06
> **SuperFreak said:**
> Power failures can last longer than 24 hours (see my first post) and when they do emergency services become more important not less. I do use a UPS on my computer so I see that as a stopgap. We have had  two power failures lasting over 24 hours in the last 15 years and barley missed another in 1998 that affected millions of people in Quebec and Eastern Ontario. While these things don't happen very often I would be very concerned for my family's safety if we didn't have quick access to emergency services. Until this issue is resolved I don't think discontinuing POTS (which worked in all those power failures lasting days) is a good idea.

 I do not own either a cell phone or a car so that would not help me.

Power failures definitely can and do last longer than 24 hours. I've had family who were caught in different storms with had power outages for 3+ weeks. One was due to a hurricane and the other was due to ice storms. The POTS systems were down in those areas too, so it really wouldn't matter. We all need to be responsible for ourselves and our safety as much as possible. Nothing can change that.

Locations with critical emergency connections are "on-file" with the power and telephone companies in the USA. Those locations get priority fixes during an outage.  OTOH, humans survived for 50,000 years without telephones, so how important is this really?

Where I live, I cannot recall any time in the last 15 yrs with power outages lasting more than 3 hrs and that happened once.  The most we usually see here is lights that flicker a few times a year and a few 5-10 second complete loses. Utility lines are buried here, so icing and tornadoes only matter for the HUGE transmission lines. Not much can be done about that anyway.

I haven't a clue about Canada telcom service (besides going to a conference in 2006 where they attended too). How do any FCC rulings impact you at all?  Canada is a different country with different laws last time I checked.  BTW, the VoIP service that I use is based in Canada. Thanks!

The main issue that I worry about with telecom infrastructure is telcoms wanting to dump wired connections and use wifi connections instead.  They are trying to get out of burying cable and all the hassle that entails. THAT concerns me much more than going with VoIP.

With all change, there are trade-offs. We have trade-offs with the POTS system today as well.  I don't know which is the better solution, just what I've decided for the needs of my family.

---

### Post by oldfred on 2014-02-06
How many people with POTS actually have a working phone when power goes out. My Mother-in-Law excluded who still has the at least 40 year old real dial phone on kitchen wall made by Ma Bell when the standards required 40 year life. But even her other phone is cordless and would not work when power is out.

I frankly was a bit surprised many years ago after buying new cordless phones that when power went out I had no phone service. So I keep one old push button phone just for emergencies and may soon cancel POTS service anyway as a package with cable, Internet & phone is actually a lot cheaper.

---

### Post by SeijiSensei on 2014-02-06
Verizon FiOS installations attach a rather large device called an Optical Network Terminal to a wall in your home that includes a storage battery to handle power outages.  Unfortunately Verizon [requires]("http://www.verizon.com/support/residential/internet/fiosinternet/troubleshooting/connection+issues/questionsone/128014.htm?CMP=DMC-CVZ_ZZ_ZZ_Z_ZZ_N_Z125") that its customers purchase replacement batteries if the original dies.  The ONT will start beeping regularly when the battery is nearing its end of life.  This little fact is never mentioned to Verizon customers when they sign up and is a constant source of customer complaints.  Sometimes you can sweet talk an installer into giving you a replacement battery from the truck.

The cost on these batteries has come down considerably.  I think they were close to $100 when I started with FiOS some years ago; now they cost [$30]("https://teleproducts.verizon.com/fios/index.cfm/eh/DisplayProducts?LOBCode=C&PromoTCode=A0760&PromoSrcCode=V&POEId=VU1SP&CMP=DMC-A0760").

I doubt these batteries would survive an outage of more than a day, if that long.  Luckily I have a cell phone and a fully-charged spare battery for it.  Nice thing about Samsung phones is that you can replace the batteries yourself!

---

### Post by SurfaceUnits on 2014-02-06
Basic Talk gives you the ATA and the first month free with no contract. Most phone calls become digital at some point and TELCO's aren't laying copper wiring any more. Couldn't they put VoIP ATAs in the DSLAMs or an additional CC cabinet?

A laymans look at the equipment  [http://www.skullbox.net/dslam.php](http://www.skullbox.net/dslam.php)

---

### Post by SuperFreak on 2014-02-06
> With a traditional phone the only connection is the single plug (RJ11 for POTS, Plain Old Telephone Service) that brings both power (50 VDC) and signals to your phone from a telephone switching center. The wires to your phone are unique to you, unlike the shared wires that bring the 120 VAC power to your home. More often than not the phone lines are run underground and not as susceptible to storm or accident damage as are power lines. When the power goes down the phone company provides generators for its switching operations that keep the system and your traditional phone operational. Remember, if your phone requires a separate power source, as most do today, it will not operate under these conditions. This is a case where older is better.

[http://southpalmbeachscore.blogspot.ca/2013/06/why-phone-keeps-working-during-power.html]("http://southpalmbeachscore.blogspot.ca/2013/06/why-phone-keeps-working-during-power.html")

---

### Post by mips on 2014-02-06
> **oldfred said:**
> 
I frankly was a bit surprised many years ago after buying new cordless phones that when power went out I had no phone service. So I keep one old push button phone just for emergencies and may soon cancel POTS service anyway as a package with cable, Internet & phone is actually a lot cheaper.

Cordless phones never work during a power outage (unless they have backup batteries) as the have to draw their power from the house mains supply to power the base station which also charges the handset.

---

### Post by mips on 2014-02-06
> **SuperFreak said:**
> Power failures can last longer than 24 hours (see my first post) and when they do emergency services become more important not less. I do use a UPS on my computer so I see that as a stopgap. We have had  two power failures lasting over 24 hours in the last 15 years and barley missed another in 1998 that affected millions of people in Quebec and Eastern Ontario. While these things don't happen very often I would be very concerned for my family's safety if we didn't have quick access to emergency services. Until this issue is resolved I don't think discontinuing POTS (which worked in all those power failures lasting days) is a good idea.

Your telephone exchange (or switching centre in the US) actually runs on 48V DC via rectifiers and large battery banks, should the power fail this will last for a few hours but the diesel generators are supposed to kick immediately when there is a power failure to carry the load. The 48V DC is also fed down your line to power your phone.

WIth VoIP I suppose they could do the same thing and supply your phone with 48V DC (or 24V) via technology similar to Power-over-Ethernet (PoE) but I doubt they will do this.

Maybe it's time for one of these connected to a truck battery :D

[img]http://web.tradekorea.com/upload_file/emp/200902/main/444459_main.bmp[/img]

---

### Post by SurfaceUnits on 2014-02-06
CBoIP ?

---

### Post by SuperFreak on 2014-02-13
>  "The second wintry storm in two weeks to hit the normally balmy south U.S. has encrusted highways, trees and power lines in ice, knocking out electricity to nearly a half-million homes and businesses." Kids are out of school, and houses are out of power, in much of a region that normally gets much rarer and lighter snowfall. If you're socked in, or if you're in the East Coast storm zone but have to venture out anyhow, what's been your experience? Some of the pictures are pretty impressive.
[http://news-beta.slashdot.org/story/14/02/13/140252/massive-storm-buries-us-east-coast-in-snow-and-ice](http://news-beta.slashdot.org/story/14/02/13/140252/massive-storm-buries-us-east-coast-in-snow-and-ice)

So why the hurry to get rid of legacy phone systems which are known to work during such events?

---

### Post by TheFu on 2014-02-13
> **SuperFreak said:**
> [http://news-beta.slashdot.org/story/14/02/13/140252/massive-storm-buries-us-east-coast-in-snow-and-ice](http://news-beta.slashdot.org/story/14/02/13/140252/massive-storm-buries-us-east-coast-in-snow-and-ice)

So why the hurry to get rid of legacy phone systems which are known to work during such events?

Why?
* Cost.
* Flexibility.
* Existing mitigation strategies are workable.

I'm currently in metro Atlanta with about 5M other people.  For the snow/ice yesterday and this morning, there were no power or data impacts at my location. Actually, any power outage of any sort is very unusual in my area.  The lights flickered yesterday, once, but not enough to impact any other systems. The microwave clocks didn't get reset, the TV didn't do anything.

Oh ... and my VoIP service has worked the entire time.

Just because I was without power, doesn't mean that others are not.  I think just under 200K homes were without power earlier today.  The sun is out, it is over 40deg and all the snow/ice has melted from most driveways and sidewalks in my neighborhood.  We had about 3 inches of snow on top of about 1/4 inch of ice.  Just checked the GA-Power outage information .. just under 185K are being reported now statewide. [http://outagemap.georgiapower.com/external/default.html](http://outagemap.georgiapower.com/external/default.html)

People don't like change, but is that reason enough to keep using the same basic technology from a hundred years ago? Should we still drive model-T cars or only use analog TV signals too?

---

### Post by SuperFreak on 2014-02-13
I have not seen the " Existing mitigation strategies" but know when our power went out for 3 days in December we had phone service with a traditional phone plugged into the wall for the entire time, my cordless phones obviously didn't work. I realize my statements sound backward but is it really known that the new technologies in place such as VOIP or cell phones will work for prolonged outages exceeding a few days? From what I understand of these systems they are reliant on batteries or regular voltage supplies unlike old technology phones which are low voltage and work during power failures because the phone companies employ back up generators.

---

