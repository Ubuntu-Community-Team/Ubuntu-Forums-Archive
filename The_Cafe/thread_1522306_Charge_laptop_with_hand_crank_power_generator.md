---
title: "Charge laptop with hand crank power generator?"
date: 2010-07-02
forum: The Cafe
---

### Post by Nick_Jinn on 2010-07-02
So there are a few similar models here....but what I am wondering is how I can find adapters for the outputs for these models so that I can use them to charge my laptop or phone while I am out....granted, its going to be a lot of hand cranking, but if you are lost or in a bind, its a pretty nifty thing to have. I think you would lose efficiency by going to a battery first, but that is another option that I also have not figured out.


[http://www.amazon.com/Ginsberg-Scientific-Generator-DC-Crank/dp/B0017W2NXC/ref=pd_sbs_op_2](http://www.amazon.com/Ginsberg-Scientific-Generator-DC-Crank/dp/B0017W2NXC/ref=pd_sbs_op_2)

[http://www.amazon.com/HyMini-Hand-Crank-Generator/dp/B002MXT8A6/ref=pd_sim_dbs_t_1](http://www.amazon.com/HyMini-Hand-Crank-Generator/dp/B002MXT8A6/ref=pd_sim_dbs_t_1)

**I guess you can find a **[B]HYmini battery somewhere, but not on Amazon where this product is listed, and I still dont know how to power my laptor or phone with it. :KS
[/B]

---

### Post by McRat on 2010-07-02
Anyone remember treadle? operated sewing machines?

Have a computer desk with a foot treadle under it and a flywheel hooked to a generator.

---

### Post by Nick_Jinn on 2010-07-02
Or have them wind up like an alarm clock supplying a few wats each, but have like 12 to 24 of them on the backside behind the screen. You wind them all up and you have power for 1 hour. It also has a battery that has a larger crank and also has solar power to add just a few wats directly to the screen if you have to turn up the screen brightness in daylight.

Its totally doable with an intel atom. 

That would be awesome....but these turn cranks already exist. I just want to know how I can charge a battery with one.

---

### Post by McRat on 2010-07-02
> **Nick_Jinn said:**
> Or have them wind up like an alarm clock supplying a few wats each, but have like 12 to 24 of them on the backside behind the screen. You wind them all up and you have power for 1 hour. It also has a battery that has a larger crank and also has solar power to add just a few wats directly to the screen if you have to turn up the screen brightness in daylight.

Its totally doable with an intel atom. 

That would be awesome....but these turn cranks already exist. I just want to know how I can charge a battery with one.

Not really knowledgeable about the latest lithium polymer technology, but if it's an externally controlled OEM recharger, you probably should be careful.  Battery damage, device damage, and explosion are risks if you over charge.  Like set your house on fire or lose some fingers risk.

Off of memory:

Battery charging is a whole science in itself, but in general you are feeding a small amount of current at a slightly higher voltage (about 10%) than the charged battery voltage is.  So you will need an ohm-volt meter to check either the battery or the charger and get your voltage.

There are single chip simple voltage regulators (they only have 3 wires) that will keep the voltage stable if you are in the right range.  Let's say you want 12v to charge a 11v battery, you can provide the chip anywhere from 8v to 20v and it will make 12v out of it (basic idea, you have to check the whitesheet for the chip).

You would probably want an LED that comes on when the voltage goes high enough to charge, and another to come on when you go too high.  IIRC, this is done with a few simple diodes and some resistors.  You are talking less than $10 in components.

Now, the Big Bang part.  You need to make sure the current (amps/milliamps) is not too high.  Current is limited by resistors (at least doing it the easy way).  Too low of current is not an issue, it just increases charging time.  Too high makes batteries explode or damages the recharging controller circuitry in the device.

Now from the practical perspective.  746? watts is one horsepower.  Most humans can only sustain about 1/4-1/2 horsepower for extended periods.  This is plenty of power for recharging, BUT that is with your legs.  No idea how much sustained HP you can be expected to generate with one hand.  If your notebook charger is 90w, it's going to be tough.  For a cellphone I haven't a clue, that might be doable.  It amazes me they sell 750w power supplies for desktop computers.  That's a lot of power.  

I think the coolest trick would be make a bicycle accessory that charges Cellphones.  This would be practical and doable.

---

### Post by Icebear on 2010-07-02
Nokia now sells a Bicycle Charger Kit
10 minutes ride at 6 mph will give you 28 minutes talk time

[http://www.fastcompany.com/1655978/nokia-phone-charger-dynamo-bicycles](http://www.fastcompany.com/1655978/nokia-phone-charger-dynamo-bicycles)

---

### Post by Nick_Jinn on 2010-07-02
Thanks for the heads up on the danger.

Thats awesome Icebear.

---

