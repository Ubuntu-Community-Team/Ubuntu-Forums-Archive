---
title: "[hardware] I just fried my laptop"
date: 2010-11-14
forum: System76 Support
---

### Post by jtgeibel on 2010-11-14
I blew up my laptop and a new projector this morning.  I had plugged the laptop into the projector via HDMI and was running on battery.  After 10 minutes or so I grabbed my charger and plugged it into the wall (at a different outlet).  As I went to plug the power supply into the computer sparks shot out from the laptop's DC input jack.  The laptop and projector both turned off and are now dead :(

My hypothesis is that the two outlets were driven from different phases of the house AC feed.  However, the outlets should share the same earth ground so it still seems a bit odd (they are all 3 prong and I'm assuming the hot and neutral are wired appropriately).  A quick search for "hdmi sparks" shows that I'm not alone.  If my theory is correct, it would mean that the projector's signal common is also not isolated from AC ground.

Is there any way to determine the isolation (if any) of my HP-OK065B13 AC to DC adapter?

I'll probably be buying a new system76 laptop soon as I have not had any problems with it otherwise.  Is it possible to get an isolated DC power supply to make sure I don't do something like this again?

---

### Post by jdb on 2010-11-14
> **jtgeibel said:**
> I blew up my laptop and a new projector this morning.  I had plugged the laptop into the projector via HDMI and was running on battery.  After 10 minutes or so I grabbed my charger and plugged it into the wall (at a different outlet).  As I went to plug the power supply into the computer sparks shot out from the laptop's DC input jack.  The laptop and projector both turned off and are now dead :(

My hypothesis is that the two outlets were driven from different phases of the house AC feed.  However, the outlets should share the same earth ground so it still seems a bit odd (they are all 3 prong and I'm assuming the hot and neutral are wired appropriately).  A quick search for "hdmi sparks" shows that I'm not alone.  If my theory is correct, it would mean that the projector's signal common is also not isolated from AC ground.

Is there any way to determine the isolation (if any) of my HP-OK065B13 AC to DC adapter?

I'll probably be buying a new system76 laptop soon as I have not had any problems with it otherwise.  Is it possible to get an isolated DC power supply to make sure I don't do something like this again?

I would test your sockets to make sure they are wired properly.
Google on "AC socket tester", they don't cost much.

jdb

---

### Post by jtgeibel on 2010-11-16
> **jdb said:**
> I would test your sockets to make sure they are wired properly.
Google on "AC socket tester", they don't cost much.

jdb

Yeah, there is definitely something wrong with the outlet.  I am still a bit surprised that in such a world of interconnected devices that consumer electronics don't provide  at least 120VAC isolation to protect against such faults - even if the fault is in the house wiring.

---

### Post by jroa on 2010-11-16
I am an electrician by trade.  Just because they share the same ground, assuming they do, does not mean they share the same potential.  If they are on separate legs, and assuming 110V receptacles, you could have 220V between the hot prongs in each receptacle.  I am not very familiar with HDMI, so I can not say if the two devices need to be in phase, but I would think that every thing that goes between the cable ends would be digital or DC.  But it sounds to me like one of two things happened.  Either the ground potential at each receptecal was different, causing current to flow between them, or the charger is bad.  

My gut feeling is that there was a problem in the laptop charger.  The charger probably fed AC into the batteries instead of DC due to a faulty component.  If you think that it is an isolation problem, you might be able to check it by testing continuity between each of the AC prongs and the DC prongs, assuming that the charger did not get damaged.

---

### Post by jtgeibel on 2010-12-08
> **jroa said:**
> If they are on separate legs, and assuming 110V receptacles, you could have 220V between the hot prongs in each receptacle.

Thanks jroa, I actually took some measurements and discovered that the wiring is rather messed up.  The two outlets are definitely on separate legs, but to my surprise I was able to measure 120VAC between their ground pins.  Not only is the one outlet on a different leg, but the polarity is backwards; plus, both the ground and neutral lines are actually hot!  This meant I was able to measure 240V from ground pin of one outlet to hot pin of another.

I still think an isolating power supply somewhere in chain would have protected the equipment.  My work laptop seems to have an isolating charger (it has a 2 prong plug that doesn't enforce polarity) but have decided to not test my theory.

---

### Post by tlroche on 2010-12-08
> **jtgeibel said:**
> I still think an isolating power supply somewhere in chain would have protected the equipment.

Perhaps, but this is why there is a huge industry in surge suppressors, powerline conditioners, etc: consumer power supplies expect near-perfect AC, and (as you've found) ya can't always trust juice outta the wall.

---

### Post by tgalati4 on 2010-12-09
So, rather than carry an UPS around to give presentations, carry a $4 plug tester and check those outlets before using them.

I've seen some messed up electrical in my time.

I was hanging a church projector (big one) and I felt a tingle when I started to make connections in the back of it.  "That's not right."  I pulled out my plug tester and it lit up--No Neutral.  "That's not right."  Pulled the plate and the plug out of the wall.  Ground and neutral wired together.  "That's not right."  Traced the hot lead back to a switched lighting Jbox.  "That's not right."  

Someone, out of convenience, wired up power to the projector (which is 20' off the ground) by tapping into a hot leg of a switched light circuit.  There was no neutral--as you only switch the hot lead to the lights.  So they have power but no neutral to pull to the location.  So they use the JBox as both a ground and neutral.  The old projector had worked fine for 3 years then stopped working mysteriously.

The new projector works fine as well, after a complete rewiring.

Keep that plug tester handy.

---

