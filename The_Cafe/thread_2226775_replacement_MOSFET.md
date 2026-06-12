---
title: "replacement MOSFET"
date: 2014-05-28
forum: The Cafe
---

### Post by squakie on 2014-05-28
I know this isn't an Ubuntu question, so I hope posting it here is ok.

I have a cheapy Haier sound bar that has stopped working - doesn't turn on.  I did some testing on the power board and found that a MOSFET is no good.  Problem is, I can't seem to find a replacement or substitute with appropriate ratings.

MOSFET:  SSF5N60C

Anyone got any ideas besides just junking the thing?

Thanks!
Dave

---

### Post by pqwoerituytrueiwoq on 2014-05-29
how did you confirm it was the mosfet that was bad?
can you link it's data sheet?

---

### Post by tgalati4 on 2014-05-29
I presume this is a small mosfet that is used to automatically turn the sound bar on and off when an audio signal is detected.  I have repaired similar devices (like subwoofers) using similar devices but with higher specifications--higher current, higher voltage, different packaging.

If this is a primary audio power mosfet, then there are lots of those available--and lots of fakes.  Real ones cost $3 to $5, fake ones cost $0.30.

Sometimes the solder traces go bad, so the mosfet may still be working.  Try resoldering the connections--include other mosfets on the board.

If the mosfet shows evidence of burning, then it is possible there are other components that are damaged.  Because mosfets control a lot of current, when they fail, they tend to take out nearby resistors, transistors, and IC's.  So carefully inspect the nearby components.  They are called flame-emitting transistors for a reason.

---

### Post by squakie on 2014-05-29
When I do the leakage tests with an ohm meter there is one set that instead of having infinite resistance it instead has resistance that keeps falling back towards zero.   That's all that I remember for the time being for testing a MOSFET.

The data sheet is too large to attach here 900+k, limit is a LOT smaller than that.  It's a PDF file I downloaded off the net.

I'm not sure exactly what it is being used for - but I assume it's purely in the power supply as that's the board I took out to start my testing.  The unit quit turning on either via the remote or by the power button on the unit.  That's why I started looking in the power supply board.  While the AC comes to the board, the power switch is coming in a ribbon-like cable that connects to another board (I assume the tuner/input selection/volume [and I assume the amp transistors or IC's] are on that other board).  I've never taken that board out yet as I wanted to start at the power supply and work in, given the failure.

That's about all I know, and while I can get my way around a piece of electronic equipment to some degree, without a schematic I am lost.  I'm no expert - far, far, far from it.  More like a hobbyist who knows just enough to screw something up ;)

---

### Post by tgalati4 on 2014-05-29
You need to test the mosfet when removed (carefully) from the motherboard.  A shorted capacitor can cause a power supply to fail.  Any leaking or bulging capacitors?  Otherwise, general power supply mosfets are a dime a dozen.  Just about anything will work.  The key is to get the correct legs attached.  Many MOSFET's have different leg arrangements.

Looking at the cutsheet, you need a fast-switching, power-supply rated MOSFET with the following:

5.0A,600v,RDS(on)=2.4&#937;@VGS=10V

5 amp capability cold, 2.5 amps at 100C
2.4 ohms when 10 volts are applied to the gate.
600 volts rated overall (probably to take some overage from power surges--a common power supply killer)

So look through the electronic catalogs for something similar and mark the legs of the motherboard with a sharpie so you know which leg goes where.  Your search continues.  Or you could pull one out of an old PC power supply and cross your fingers.

---

### Post by squakie on 2014-05-30
Yep - I already removed it prior to testing it - 45 or so years ago I learned a "little" lesson in the high-voltage supply for a TV (tube back then) and testing things in-circuit, called (1) drain the dang thing first ;) and (2) watch anything filtering to ground, etc..  It was interesting watching sparks coming back out of my arm near the grounding cage and them my arm a little out of control for a few minutes ;)  At any rate, yep - I've tested things for the most part out of circuit as you really can't get any true readings otherwise.  I had tried to cross-reference on the part number at several of the "big" part suppliers but nobody had a direct cross.  I guess I do need to do the slightly more time consuming of ratings match ;)  Thanks for the detailed info because that will help me a lot in my quest!

Thanks!

dave ;)

---

### Post by tgalati4 on 2014-05-30
I have repaired a few TV's in my time--solid state, though.  I've been zapped a few times, even taking precautions to ground and discharge things.  Good luck in your search.

---

### Post by Jonor on 2014-05-30
Reminds me of the school lesson a teacher stealthily wired a *certain* size capacitor up the wrong way to a small battery and placed it at the bottom of a large ceramic laboratory sink a while as a warning of what not to do ;) , it sure tested the strength of seating when it went thwudddd !

---

### Post by squakie on 2014-05-30
Yep - somethings, while they can be a "little" dangerous, that happen by accident in working with this stuff can be "fun".  I remember blowing apart one of those paper electrolytics once - and man did that thing STINK when it did.  

tgalati4 - thanks so much for your help!

---

### Post by squakie on 2014-06-01
tgalati4 - how do you think a FQPF8N60C would match up?

---

### Post by tgalati4 on 2014-06-01
Better specifications than the orginal:  7.5 amps cold versus 5 amps, 3.5 amps hot versus 2.5 amps.  1.2 ohms versus 2.4 ohms when switched on.  Less resistance means less heat.  Power = I*R^2.  So when hot:  The old one would need to dissipate 14.4 watts at 2.5 amp draw.  The new one would dissipate 3.6 watts--so it will not get as hot and last longer.

Make sure you get the correct legs into the holes on the circuit board.  Check the cutsheets for the leg arrangements.  That is most important.  Use some heat paste between the mosfet and the heat sink.  Not too much, but enough to cover with a thin layer.

---

