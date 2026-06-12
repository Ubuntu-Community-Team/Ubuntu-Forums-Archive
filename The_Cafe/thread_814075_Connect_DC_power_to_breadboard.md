---
title: "Connect DC power to breadboard?"
date: 2008-05-31
forum: The Cafe
---

### Post by Yes on 2008-05-31
I hate to sound like a total noob, but what do I need to connect DC power to a breadboard?  I know what it looks like and everything, I just need to know it's official name so I can find it online.

Also, I've seen some sites say that I need compactors around my 7805 chip to.  How many farads should they be?  

Thanks!

---

### Post by dasunst3r on 2008-05-31
To get DC power, you would want a power supply, which consists of a transformer, rectifier, and a capacitor.  For power supplies that allow you to control the voltage, there may be a DC-DC converter (buck, boost, buck-boost, etc.) between the regular power supply and the load.

For more insight on what capacitors you would need for the 7805, here's a little bit more information: [http://www.ee.washington.edu/stores/DataSheets/voltreg/7805.pdf](http://www.ee.washington.edu/stores/DataSheets/voltreg/7805.pdf).  I don't know what you're using it for, but schematics of typical applications start on Pg. 21.

---

### Post by tamoneya on 2008-05-31
what voltage do you need for the DC power.  The cheapest way is to find an old phone charger or some other power cord.  Check the voltage as it should be written on the back.  Then cut the cord that goes to the electronics, strip the wires and plug them in.  Shouldnt cost you anything since if you are like me you have piles of old electronics lying around.

---

### Post by Yes on 2008-05-31
I think I need 9-12V.  I have some old phone chargers, how do I know what wire is voltage and which is ground?

---

### Post by tamoneya on 2008-05-31
on those circular plugs ground is almost always on the outside.  Cut one of the wires and then check its conductivity with the outside of the plug.  If there is conductivity then it is ground otherwise it is V++.  The easier way however is to use a multimeter to measure the voltage.  If you get it backwards it will just measure as -9V or whatever.  If you dont have a multimeter however you should go with the previous suggestion.

---

