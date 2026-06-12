---
title: "How fragile are hard drives?"
date: 2008-04-10
forum: The Cafe
---

### Post by Exershio on 2008-04-10
I bought a new hard drive a few months ago, 250gb IDE, and today I did something that scared me more than a little. While my hard drive was spinning, I bumped into my computer desk and caused a violent shake, and the hard drive made kind of a scraping noise for about a second. Could this have caused any permanent damage? I'm not so concerned about the data on this drive as I am about the drive being in good condition.

I hope I didn't cause any sectors to break or what not. I don't know much about hard drives. What do you all think?

P.S.: I put the topic here because I don't think it belongs in "hardware and laptops" due to this not really being installation support. Feel free to move it mods if you think otherwise

---

### Post by caravel on 2008-04-10
I hate to alarm you, but the scraping was possibly the heads crashing into the disk platen surfaces.  This does do damage but sometimes the damage is not enough to cause a problem.  Have you checked the drive for errors (fsck)?

---

### Post by LaRoza on 2008-04-10
Hard disks shouldn't be moved when they are running. Whether it is damaged in any way is hard to tell without any more information.

---

### Post by Exershio on 2008-04-10
I haven't checked the drive for errors yet using fsck, but I'll do that in a bit.

What would the extent of the damage be? Loss of data? Completely broken hard drive? Or would a reformat be smart and skip over the busted sectors, ignoring them completely, making the hard drive as good as new but with a little less storage space?

---

### Post by wieman01 on 2008-04-10
But it's unlikely it's been damage. In my experience today's hard drives are fairly robust, even if you drop it they are likely to survive. You should check the drive for error and bad sectors though to be sure. A violent shake should not have caused any damage.

_**EDIT:**_
If the drive continues to make a strange noise as you have described, pull a backup immediately.

---

### Post by KiwiNZ on 2008-04-10
run a disk scan to see if there is damaged sectors.
I would run a back up now as well ,especially if it is still functioning.

---

### Post by Exershio on 2008-04-10
Thanks everyone for the fast replies. The drive isn't making any strange noises anymore. It's as quiet as it always is.

Once Ubuntu finishes updating (300mb of updates. >_>) I'll run an disk check and then back everything up. I really hope it didn't cause any permanent damage. This thing cost me $100 and I really don't have any money for a new one.

---

### Post by warbread on 2008-04-10
Is it a laptop or a desktop hard drive?  All hard drives have ratings for the amount of geforce they can withstand, and laptop drives are much sturdier than standard desktop drives are.  It's a different story when the drive is spinning, but I doubt there's been any permanent damage.  If your  drive can still read, then the head is fine.  Damage to the disk will manifest if it exists, but until then, there's no reason for alarm.

---

### Post by Exershio on 2008-04-10
Yes, it can still read and write. I'm just worried about errors popping up later on in life when I'm saving a large file or something and it ends up getting corrupted due to that broken sector.

Anyways, off to run a disk check on the entire drive to make sure everything's good. Thanks again.

---

### Post by billgoldberg on 2008-04-10
I've let my laptop drop from 0.5 meter high when it was running and there was nothing wrong with the hard drive (nor with anything else). It fell on the carpet though.

I think hard drives today are pretty robust. With the new ssd drives, damaging hard drives will be even harder. :p

---

### Post by wieman01 on 2008-04-10
> **billgoldberg said:**
> I've let my laptop drop from 0.5 meter high when it was running and there was nothing wrong with the hard drive (nor with anything else). It fell on the carpet though.

I think hard drives today are pretty robust. With the new ssd drives, damaging hard drives will be even harder. :p
But laptop drives sometimes come with some sort of 3D protection which is to say that they park the hards automagically as soon as the HD realizes it's falling... Laptop HD's have better protection than normal ones.

---

### Post by handy on 2008-04-10
Hard drives are surprisingly strong when their heads are parked.

They are quite vulnerable when the disks are spinning & the heads are in motion.

I think you have turned your hard drive into a lathe unfortunately for you.

After you have replaced it, pull the top off?  If you don't have a torque driver to fit, just drill the heads off the screws, there is usually one or 2 hiding under stickers.  When you get the top off, you will see what I mean about turning it into a lathe.

Now that you have the top off, pull out the magnet(s), they are incredibly strong, will hold things on your fridge that are quite thick.

Just trying to help you make the most out of a (nowhere near as expensive as they used to be) expensive experience.

---

### Post by SunnyRabbiera on 2008-04-10
Hard drives are pretty tough, they seem to be able to take a beating...

---

### Post by chewearn on 2008-04-10
When you bump a spinning harddisk, there are two possibilities:

1. The head is parked safely, without hitting the platter.  This is only possible for harddisk that has accelerometer, and able to detect bumps.

2. The head hit the platter; microsopic particles are chipped off from the bump

Harddisk with accelerometer is usually found in smaller harddisks used in portable devices.  Afaik, consumer desktop 3.5inch harddisk does not have accelerometer built-in.

Which bring us to the second scenario.  In this scenario, the harddisk is deadman walking.  As the disk platter spins at high speed and the magnetic head swings arm move, the microscopic particles get banged around inside, creating more particles.  It's a matter of time before more and more failure develops.

It's no accident that harddisks manufacturing have to be done in a clean room; to prevent any dust from getting inside.

---

### Post by wieman01 on 2008-04-10
> **SunnyRabbiera said:**
> Hard drives are pretty tough, they seem to be able to take a beating...
Not a beating though... I beat mine (laptop HD) badly the other day and it broke on me. No mercy. Broke another one (2.5 inch external HD) a minute later because I accidently let is drop (3 feet, no carpet). Pretty bad.

---

### Post by love2learn on 2008-04-10
[LEFT]The only knowledge I have about the subject is experience. I have dropped drives, intentionally smacked drives, and accidently tapped drives. They all behave differently when "touched". I still have a working 8gb WD drive I threw accrossed the room cause the head was stuck. The jar from the impact actually "fixed" the drive and amazingly enough, it doesnt even have bad sectors.
   On the flip side to that coin, I bought a WD raptor and put it into raid configuration with another raptor. Didnt like the raid card so I took it out and hooked up the raptors to the motherboard. The raptor started failing left and right after a fresh copy of windoze was put on it. Had to RMA it within the 3 months I had it. 
All I can reccomend is
I would deffinately backup your software if you care for anything that is on it. Pay attention to your warranties of your harddrives and if the head gets stuck LIGHTLY tap the edge of the hd on all four edges and it more then likely will give you a few more hours  of uptime on your harddrive. (use as a last option if desperate for information on hd but dont have the funds to take it to a proffessional)


 [/LEFT]

---

### Post by az on 2008-04-10
Hard disks are pretty fragile.

You should run a check on your hard drive.  See here how to do it using SMART:

[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

---

### Post by wieman01 on 2008-04-10
> **az said:**
> Hard disks are pretty fragile.

You should run a check on your hard drive.  See here how to do it using SMART:

[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)
Nah... back in the good ol' days when we were young, yes. But things have changed... ;-)

Just pulling your leg.

---

### Post by Dixon Bainbridge on 2008-04-10
I took a claw hammer to mine when I was disposing of it. After the second blow I remember that I need to take a folder of it, so I plugged it back in and fired it up. It worked with a massive dent in the top and the side hanging off.

I dropped another by accident down a flight of concrete stairs. It still works. :)

Hard drives are pretty tough.

---

### Post by LaRoza on 2008-04-10
> **Dixon Bainbridge said:**
> I took a claw hammer to mine when I was disposing of it. After the second blow I remember that I need to take a folder of it, so I plugged it back in and fired it up. It worked with a massive dent in the top and the side hanging off.

I dropped another by accident down a flight of concrete stairs. It still works. :)

Hard drives are pretty tough.

But don't trust them. One can jump out of a third story window and not be hurt, but that doesn't make it a rule.

---

### Post by Dixon Bainbridge on 2008-04-10
> **LaRoza said:**
> But don't trust them. One can jump out of a third story window and not be hurt, but that doesn't make it a rule.

No, you're right, but in general, they are pretty robust v. knocks. I'd always replace a drive every 5 years or so as they do wear out.

---

### Post by wieman01 on 2008-04-10
> **Dixon Bainbridge said:**
> No, you're right, but in general, they are pretty robust v. knocks. I'd always replace a drive every 5 years or so as they do wear out.
Laptop device probably every 3 years.

---

### Post by handy on 2008-04-10
> **Dixon Bainbridge said:**
> 
Hard drives are pretty tough.

When they are not in motion.

---

### Post by caravel on 2008-04-10
I once knocked a perfectly working hard drive off a table surface and onto a carpted floor.  Powered it up and it would do nothing more than tick and scrape repeatedly.  Dead.

You may be lucky having dropped an HDD and gotten away with it once but that does not mean that HDDs are "sturdy".  They're not.

---

### Post by herbster on 2008-04-10
I dropped my WD 500AKS a few months ago when it was in a Nexstar enclosure, off a regular desk to the floor. She was done for, got an RMA replacement.

Gots to be careful!!

---

