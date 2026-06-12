---
title: "How to discharge a Li-Ion Battery"
date: 2008-09-21
forum: The Cafe
---

### Post by khalis on 2008-09-21
Seems like a newbie question, but I'm not talking about turning my screen brightness up and draining it.  I have my laptop battery opened and would like to manually place a load on it to drain each cell.  Its a Dell battery that after 14 months (exactly 14 months), went from about 80% of its normal capacity to around 5%.  It can only power this machine for around 5 minutes, because the battery is a ripoff.

I've opened the battery, since it carries no warranty anyway and tested each cell after a "full" discharge in the laptop and each cell individually reports 3.7V.  Awfully close to their normal 3.6V...  So anyway, I don't know enough about electricity to discharge this battery safely, so I was wondering what I would need to safely place a load on the battery to discharge it?

I'm afraid to buy new cells and replace them in case its the electronics that are just reporting "failure" and that's the reason it isn't working.  If that's so, then only a new battery with new electronics would work.

Specs:
11.1V 9-cell battery 80WH capacity. (3.6V/cell) 3 parallel cells in 3 series.

Any help at all would be appreciated.

---

### Post by lisati on 2008-09-21
I'm not sure about the "how to" with a laptop (presumably a similar solution *might* work), but with the Lithium-Ion batteries used by my camcorders I generally discharge them by leaving the camera switched on for a day or two.

---

### Post by khalis on 2008-09-21
I was looking for a way to do it with a proper external load, like a lightbulb or something.  What could safely handle 11.1V and the current its capable of producing?

---

### Post by master5o1 on 2008-09-21
remember that testing a cell with just a voltmeter is not as accurate as testing it with a bunch of resisters to assume the more actual load

---

### Post by lswb on 2008-09-21
12V automotive lamps would work. 12V current draw for some:

#1156 2.1 amps
#1003 0.94 amps
#89 0.58 amps
$57 0.24 amps

---

### Post by mips on 2008-09-22
Can you provide the cell details, brand, model, physical size, voltage & mAh rating.

I don't think your electronics are dodgy though. It might be worth repacking the the battery with new cells. If you do buy the best brand and highest mAh rating you can get.

---

### Post by mr.propre on 2008-09-22
You should never fully discharge a Li-Ion battery because of deep-discharge. What basically will brick your battery. Modern computers have a protection system that prevents this kind of discharges, but sometimes they fail, and I guess that happened to you. Only solution is buying a new battery.

People still think that you need to fully discharge batteries, but this was back in the old days when everyone was using NiCd batteries.

Edit: Another reason why you should just trow away your battery: because they can **explode**!!!

---

### Post by jespdj on 2008-09-22
As mr.propre says, I've also read that if you fully discharge a LiIon battery, it cannot be charged again, so don't try it. Tinkering with batteries yourself is not a good idea; they may contain toxic chemicals and if you mistreat them, serious accidents can happen (including explosions).

See [BatteryUniversity.com](http://www.batteryuniversity.com/) for detailed information on rechargeable battery technology.

---

### Post by khalis on 2008-09-22
I've spent quite a while learning about batteries and lithium-ion specifically.  The problem I'm having is that the battery electronics reports that it is dead (<10% of normal capacity), but there is no drop or change in voltage from a completely full charge, to a complete discharge.  I believe what happened is the computer was left on all night, on top of a table cover and it may have tripped the overheat detector on the battery.  (it was on AC)  In that one night, it went from 80% to <10% normal capacity and voltages on each cell are completely normal.

I'll try using a 12V auto lamp (i have a spare) and drain the cells until they drop below 11.1V, maybe 10V or so.  Then I'm going to try charging the battery in my laptop and see what kind of charge it will hold.  I'm guessing the electronics keep track of what capacity is in the battery and only allow that much to discharge, but if not I'll end up buying a new one.

Either way, its worth a try seeing as the battery lost its warranty _exactly_ 60 days before its demise.  So, there's nothing much to do with it anyway.

EDIT: The battery is a Dell Type U4873 80WH 11.1V 9-cell (3x3), I don't know the cell specifics, since they're wrapped and serials are covered.

---

### Post by khalis on 2008-10-07
After discharging with a 12V 50W lightbulb, I found it lost significant voltage in the first 15 minutes.  As such, I'm assuming the cells are actually faulty so I'm going to just invest in a new battery.

I could rebuild it, but the battery casing was snapped, glued and melded closed in the most annoying way possible.  I don't think anyone could have opened the case without completely destroying it.

---

### Post by mips on 2008-10-07
> **khalis said:**
> I don't think anyone could have opened the case without completely destroying it.

There are ways but it requires patience & a bit of time. You just have to be carefull.

---

### Post by Polygon on 2008-10-07
battery manufacturers have a magic device that discharges the battery instantly, also i hear monitor manufactures have something similar to this. is the only real safe way to open a monitor and stuff

---

### Post by handy on 2008-10-07
> **Polygon said:**
> battery manufacturers have a magic device that discharges the battery instantly, also i hear monitor manufactures have something similar to this. is the only real safe way to open a monitor and stuff

I know a few electronics technicians that work on CRT TV's & monitors & none of them have a tool to discharge them.  Each of them has been bitten on the nose at least once in their working life by 20,000 low amp', volts. 

Ow!

---

### Post by Ocxic on 2008-10-07
Don't throw it away, bring it to a battery recycling center, those this are toxic.

---

### Post by mips on 2008-10-08
> **handy said:**
> I know a few electronics technicians that work on CRT TV's & monitors & none of them have a tool to discharge them.  Each of them has been bitten on the nose at least once in their working life by 20,000 low amp', volts. 

Ow!

I don't work on them but I did get bitten once :)

And that tool he was talking about could be a screw driver to short the HV rail to ground.

---

### Post by lganimys on 2008-11-30
I had a similar problem where my sony laptop started shutting down after 5 minutes.

I removed the battery pack (I was lucky as there were screws and the cylenderical cells inside the pack could be removed) Then I used a 12 volts bulb to discharge the battery to about 10 Volts.
I again re-charged the battery by connecting it to the laptop.

The backup improved to about 20 minutes.

The I had no choice but to buy a OEM replacement or repair the existing battery pack.

I went to the market and purchased 6 pieces of 3.7 Volts Li-Ion battreries and connected then as before.

As I am an electronics hobbiest, I did not have much problems in fixing the same.

Finaly the backup returned to 2.5 hours. No heating or problems of any kind.

The Following link provides visual lesson on how to do it.

[http://www.electronics-lab.com/articles/Li_Ion_reconstruct/](http://www.electronics-lab.com/articles/Li_Ion_reconstruct/)

Ganesh Laxmanmurthy

[WWW.JobConsultancy.com](WWW.JobConsultancy.com)

---

