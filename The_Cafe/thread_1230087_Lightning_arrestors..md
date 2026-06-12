---
title: "Lightning arrestors."
date: 2009-08-03
forum: The Cafe
---

### Post by JillSwift on 2009-08-03
Someone mentioned worrying about thier surge protector being functional as a lightning storm rolled in and I got to wondering:

I have a [Delta CA302 R]("http://www.deltala.com/prod04.htm#CA302R") in my circuit breaker panel, which I think may have saved my bacon on a couple of occasions. Because it's deigned with lighting in mind, and doesn't protect against smaller surges, I also have individual surge protection on my delicate electronic stuff.

Does anyone else use lighting arrestors?

---

### Post by wirepuller134 on 2009-08-03
We use one on our outside wireless antenna.

---

### Post by HermanAB on 2009-08-03
I don't have a lightning arrestor, since the power lines are underground.  However, I have little surge suppressors (MOVs) on each power bar and one or two of them have blown up over the years - committing suicide to protect the stuff connected to it.

---

### Post by khelben1979 on 2009-08-03
No. 

I do own an APC surge protector (cheap one) which helps prevent the system from going down when lightning causes short blackouts (a few seconds), thereby not losing any data and prevents file corruption of the filesystems.

---

### Post by Tipped OuT on 2009-08-03
:P  I don't use anything. I don't think... :???:

---

### Post by Blu Fox on 2009-08-03
I think our power lines are underground but I wouldn't mind having a surge protector just in case. And besides, I live in THE LIGHTNING CAPITAL OF THE WORLD DX[SIZE=1] (aka, the sunshine state ._.)[/SIZE]

---

### Post by MasterNetra on 2009-08-03
Don't really know what those are. Some kind of grounding device?

---

### Post by JillSwift on 2009-08-03
> **MasterNetra said:**
> Don't really know what those are. Some kind of grounding device?
In essence, yes. They shunt voltage to ground during a lightning strike and through their capacitance they also limit changes in voltage to the outlet during the strike.

---

### Post by Sporkman on 2009-08-03
Heh heh, "lightning freedom" - well done. :)

---

### Post by dragos240 on 2009-08-03
I've never heard of one.

---

### Post by gletob on 2009-08-03
I have never heard of these before, They seem pretty interesting.

---

### Post by koleoptero on 2009-08-03
I believe in lightning freedom. If my equipment gets burned, all the more reason to upgrade. :P

---

### Post by wojox on 2009-08-03
> **Blu Fox said:**
> I think our power lines are underground but I wouldn't mind having a surge protector just in case. And besides, I live in THE LIGHTNING CAPITAL OF THE WORLD DX[SIZE=1] (aka, the sunshine state ._.)[/SIZE]

+1
It's saves me a lot in the summer.

---

### Post by HavocXphere on 2009-08-03
What follows is **based on theories and speculation**.:biggrin: Please correct if you know otherwise.

Afaik nothing is fast enough to catch a direct strike that is putting major voltage onto the lines. Those surge protectors with the reset buttons take a few miliseconds to cut the line...and a few milisecond of gazillion volts is more than enough to fry anything.:frown:

The fuse based systems usually need quite a bit of juice to get cut often much more than the system its supposed to protect.

Even UPSs are a bit sketchy for this purpose.

Backup UPS -> hopeless. Lightning will fry the PC easily.

Line-Interactive -> PC will probably survive if its not a direct strike

Double conversion UPS -> Solid chance of PC surviving irrespective of type of strike. (Hence they cost 10-20 times more;)) UPS dead in case of direct strike.

Fuse based arrestors -> Limit *extent* of damage in case of direct strike. Minor surges will go through.

Electronic (reset button type) arrestors -> Useful for cutting minor and major surges...again, the first few miliseconds will get through.

After seeing some of the damage lightning can do to trees my confidence in all these devices was severely dented.:-k

I think a 5 ton flywheel is probably the only sure way.:D

No idea how effective the device linked in the OP is...but the fact that they think a marketing pamphlet counts as "specs" does not inspire confidence.

> I think our power lines are underground but I wouldn't mind having a surge protector just in case.
Underground lines are 100% insulated...they wouldn't be much good otherwise. In fact the are probably safer lightning wise: 1. Can't get a direct strike. 2. Well insulated against indirect surges through the ground.

---

### Post by JillSwift on 2009-08-03
> **HavocXphere said:**
> What follows is **based on theories and speculation**.:biggrin: Please correct if you know otherwise.

Afaik nothing is fast enough to catch a direct strike that is putting major voltage onto the lines. Those surge protectors with the reset buttons take a few miliseconds to cut the line...and a few milisecond of gazillion volts is more than enough to fry anything.:frown:

The fuse based systems usually need quite a bit of juice to get cut often much more than the system its supposed to protect.

Even UPSs are a bit sketchy for this purpose.

Backup UPS -> hopeless. Lightning will fry the PC easily.

Line-Interactive -> PC will probably survive if its not a direct strike

Double conversion UPS -> Solid chance of PC surviving irrespective of type of strike. (Hence they cost 10-20 times more;)) UPS dead in case of direct strike.

Fuse based arrestors -> Limit *extent* of damage in case of direct strike. Minor surges will go through.

Electronic (reset button type) arrestors -> Useful for cutting minor and major surges...again, the first few miliseconds will get through.

After seeing some of the damage lightning can do to trees my confidence in all these devices was severely dented.:-k

I think a 5 ton flywheel is probably the only sure way.:D
I think the sure way is to control where the lightning strikes. But i doubt people would appreciate the sheer number of lightning rods involved ;)

> **HavocXphere said:**
> No idea how effective the device linked in the OP is...but the fact that they think a marketing pamphlet counts as "specs" does not inspire confidence.Their site does suck, does it not?

I am under the impression the device's capacitance gives it an ability to start reacting/conducting before the voltage has spiked passed the point of certain destruction. But I could easily be wrong.

Really, like all security, this is a matter of "one more layer", and in and of itself can not be considered in any way perfect.

> **HavocXphere said:**
>  Underground lines are 100% insulated...they wouldn't be much good otherwise. In fact the are probably safer lightning wise: 1. Can't get a direct strike. 2. Well insulated against indirect surges through the ground.
Sadly, most of the power lines in my city are still up on poles.

---

### Post by bkratz on 2009-08-03
> **JillSwift said:**
> Someone mentioned worrying about thier surge protector being functional as a lightning storm rolled in and I got to wondering:

I have a [Delta CA302 R]("http://www.deltala.com/prod04.htm#CA302R") in my circuit breaker panel, which I think may have saved my bacon on a couple of occasions. Because it's deigned with lighting in mind, and doesn't protect against smaller surges, I also have individual surge protection on my delicate electronic stuff.

Does anyone else use lighting arrestors?

I believe most houses bring in 3 phase (240 volts) and use phase to ground for 110(120) vac. Most likely part of your house is on one side of a single phase 110 vac connection and some of your house is on the other side (the second phase to ground connection). So you were lucky to pick the right one since the device you purchased was only single phase and only protecting one side. The reason being that some devices in your house require 240 like maybe the stove.

---

### Post by JillSwift on 2009-08-03
> **bkratz said:**
> I believe most houses bring in 3 phase (240 volts) and use phase to ground for 110(120) vac. Most likely part of your house is on one side of a single phase 110 vac connection and some of your house is on the other side (the second phase to ground connection). So you were lucky to pick the right one since the device you purchased was only single phase and only protecting one side. The reason being that some devices in your house require 240 like maybe the stove.
What "luck"? My cousin is a competent electrician, he put the thing in on the phase my "computer room" (aka bedroom) is on. :)

---

### Post by magmon on 2009-08-03
> **dragos240 said:**
> I've never heard of one.

Me either.

I have a surge-protected power supply that all my stuff is hooked up to. It has 8 outlets, and with the installation of my new(ish) computer, I have them all full xD.

---

### Post by bkratz on 2009-08-03
> **JillSwift said:**
> What "luck"? My cousin is a competent electrician, he put the thing in on the phase my "computer room" (aka bedroom) is on. :)

Don't move your computer to the dining room! And yes it would help since physics says that you can't have an instantaneous voltage change across a capacitor. By the way lightning strikes are in the nanosecond timing range or quicker.

---

### Post by koleoptero on 2009-08-03
> **bkratz said:**
> Don't move your computer to the dining room! And yes it would help since physics says that you can't have an instantaneous voltage change across a capacitor. By the way lightning strikes are in the nanosecond timing range or quicker.

That's what they say for coils (or however they're call in english?).

---

### Post by t0p on 2009-08-03
I don't have anything special.  Trip-switches by the fusebox.  But also underground power cables, which makes me pretty safe methinks.

---

### Post by bkratz on 2009-08-03
> **koleoptero said:**
> That's what they say for coils (or however they're call in english?).

I think this is what we call inductors. Instantaneous voltage changes would require an infinite current. Lightning is pretty close though since it is so fast,but here is a good explanation of both coils and caps with respect to voltage changes.

[http://www.mounttaylor.com/ref/electrical/capacitors-inductors-changes-in-voltage.html](http://www.mounttaylor.com/ref/electrical/capacitors-inductors-changes-in-voltage.html)

---

### Post by nubimax on 2009-08-03
There is a pepper tree 30 feet from my kitchen window works great as a lightning rod it has been hit three times in 9 years.  It does make a mess of the tree though.
M

---

### Post by JillSwift on 2009-08-03
> **nubimax said:**
> There is a pepper tree 30 feet from my kitchen window works great as a lightning rod it has been hit three times in 9 years.  It does make a mess of the tree though.
M
Ouchies. :shock:

---

### Post by MasterNetra on 2009-08-03
> **nubimax said:**
> There is a pepper tree 30 feet from my kitchen window works great as a lightning rod it has been hit three times in 9 years.  It does make a mess of the tree though.
M

Poor tree, it just has such bad luck. For heaven sakes get a lightning rod installed that goes higher then the tree and give the poor tree a break. Its ancestors after all are a large part of the reason we and all the other animals can live on land. I mean they did terraform it. I swear no respect for that which supports us...

---

### Post by MikeTheC on 2009-08-04
While I do have battery backups on all my critical gear in my house, I voted for Lightning Freedom because I wasn't aware Lightning ever broke the law, ergo attempts to arrest Lightning would probably result in charges of false imprisonment or unlawful detainment. We've already got enough idiots clogging our court system; the last thing we need is lightning entering into it like a bolt out of the blue.

---

### Post by JillSwift on 2009-08-04
> **MikeTheC said:**
> While I do have battery backups on all my critical gear in my house, I voted for Lightning Freedom because I wasn't aware Lightning ever broke the law, ergo attempts to arrest Lightning would probably result in charges of false imprisonment or unlawful detainment. We've already got enough idiots clogging our court system; the last thing we need is lightning entering into it like a bolt out of the blue.
TARDIS avatar, Xanth reference, and literalist humor.

"***Mom?! ***Can I keep him? I promise to feed him and change his litter box. Promise!" :lol:

---

### Post by jerrrys on 2009-08-04
I think [HavocXphere]("http://ubuntuforums.org/member.php?u=550474") got it right.  We have a metal chicken on the roof and for added protection a horseshoe over the door...

---

### Post by MikeTheC on 2009-08-04
> **JillSwift said:**
> TARDIS avatar, Xanth reference, and literalist humor.

"***Mom?! ***Can I keep him? I promise to feed him and change his litter box. Promise!" :lol:

Oooh! Oooh! And I have all my original Lego Moon legos, too! (In a box somewhere...) :p

---

