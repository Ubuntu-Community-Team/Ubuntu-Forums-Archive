---
title: "how do power supplies work?"
date: 2007-03-09
forum: The Cafe
---

### Post by billdotson on 2007-03-09
So as I understand it a watt is 1 joule per second.  An amp is the amount of electrical current and a volt is the indicator of the possible energy that can be transferred between the two ends of the circuit.

So if I have a 550 watt PSU with a +12V, -12V, +3.5V, -3.5V, +5V, -5V rails and say the +5V rail has 40amps the 12V has 32amps and the +3.5V rail has 18 amps.  What does all this mean?  When you hear what you need for a video card or something it says requires a 350watt PSU or something of that nature.  According to the def's the power supplies electrical charge of 'x' amps runs through the voltage rails and the energy expended by that produces approximately 550 joules per second?

Also, say if you have an electric fence and it says "high voltage stay away", does it really matter (obviously for an electric fence but think about it if you weren't sure the fence was dangerous) about how high the voltage is if there aren't enough amps to travel through the voltage?? because the voltage is potential of electric current.. not the actual current..?

oh yeah and what does the + and - in front of the rails mean.. and should you judge the strength/quality of a power supply not on watts but on the amperage per rail?

---

### Post by John.Michael.Kane on 2007-03-09
Have a read.
[How Pc Power Supplies work]("http://computer.howstuffworks.com/power-supply1.htm")

[Anatomy of Switching Power Supplies]("http://www.hardwaresecrets.com/article/327")

[Power Supply Tutorial]("http://www.hardwaresecrets.com/article/181")

[ohmslaw]("http://www.the12volt.com/ohm/ohmslaw.asp")

---

### Post by billdotson on 2007-03-09
nice I will check them out

---

### Post by azkehmm on 2007-03-09
I've always learned that the volts hurt, the amps kill.

---

### Post by mips on 2007-03-09
[http://computer.howstuffworks.com/power-supply.htm](http://computer.howstuffworks.com/power-supply.htm)
[http://computer.howstuffworks.com/power-supply1.htm](http://computer.howstuffworks.com/power-supply1.htm)
[http://en.wikipedia.org/wiki/Switched-mode_power_supply](http://en.wikipedia.org/wiki/Switched-mode_power_supply)
[http://science.howstuffworks.com/electricity.htm](http://science.howstuffworks.com/electricity.htm)


Voltage refers to a potential difference which can be both positive and negative thus the +/-.
+5V 40Amp basically means that at 5V you have 40Amp of current available or you can draw 40Amps of current at that voltage, no more but less is ok.

Electric fences have high voltage and VERY little current so it does not kill you. Things is it can still give you a nasty shock (been there done that got the badge). Same goes for stun guns and tazers. The shock is enough to deter you or immobilise you. In some cases potential difference like those found in the back of tvs, monitors, microwaves are enough to throw you across a room and possibly make you heart stop.

The current is the DANGEROUS one that kills you. 10+milliAmps (0.01A) can cause you serious harm, 60+milliApms (0.06A) can KILL you!!! Then again very high voltages like lightning will also kill you.

---

### Post by billdotson on 2007-03-09
wait so if volt is the potential difference (which is the quantity related to the amount of energy that would be required to move an object from one place to another against various types of forces) how can it have charge.. it just sounds like it is an indicator of how much energy is needed to do something.  

so alternating current and direct current.. the ac comes in from the outlet and is converted into DC power od 3.5, 5 and 12Vs.  Why exactly determines the volts for the DC (just how much the parts need to run?)?  direct current is used for a PC because the electricity goes into the capacitors and keeps the machine running.  When you turn the machine off (by pressing the on/off button) you are telling the PSU to calm down and provide only enough current to turn the power back on by the on/off switch.  So the capacitors just eventually release their charge when there isn't dc into them?

---

### Post by Ocxic on 2007-03-09
yes, caps will eventually discharge, voer time, the bigger hte cap that longer it'll take.

---

### Post by JAPrufrock on 2007-03-09
DC current goes in both directions- hence the + and - signs.  The + current is going in the opposite direction to the - current.  If the two wires to a DC motor are switched, the motor will turn in the opposite direction.  In some DC circuitry the direction of current is very important.  

AC current is alternating- it goes in one direction, and then switches to the other direction.  The switching is done very rapidly;  120 changes in direction per second means that the  system goes through 60 cycles.  If the two wires to an AC motor are switched, the motor still turns in the same direction.

Watts = amps x volts.  So if the voltage of an AC current is 120, and a device is sucking up 10 amps, the total number of watts is 1200.   740 watts is equal to 1 horsepower (approximately).   A 15 amp circular saw has approximately 2.5 hp.

---

### Post by billdotson on 2007-03-09
so if volt is the potential difference (which is the quantity related to the amount of energy that would be required to move an object from one place to another against various types of forces) how can it have charge.. it just sounds like it is an indicator of how much energy is needed to do something..

---

### Post by JAPrufrock on 2007-03-10
Think of voltage as the force or electrical pressure pushing electrons through the circuit.  In DC circuits the voltage pushes the amps in a certain direction (hence the + and -).   Resistance, measured in ohms, is what obstructs that flow.

The best way to think of electricity is by using the water hose analagy.  I found this on the web:

A good and often used analogy is a garden hose. When you hook up the hose and open the valve, water should come out the other end. How much water and with what force depends on the amount of water available (amps), water pressure (volts) and resistance in the hose (ohms).

Even if there is an infinite amount of water available, flow will vary with force and resistance. The greater the force (water pressure), the more water will flow. If pressure falls, possibly when everyone in the neighborhood wants to water their lawn at the same time, the available water supply to your faucet falls and the force at the hose diminishes. Even if force and available supply remain constant, flow may vary with resistance in the hose. Put a kink in the hose and you’ve increased resistance, reducing flow. Use a larger hose and water will flow more freely. Close a nozzle and you’ve increased resistance. The three components — force (volts), flow (amps) and resistance (ohms) — are inter-related. The relationships can be calculated using the formula (Ohm’s Law) E=IR, where E is the voltage, I is the amperage and R is resistance.

Volts times amps are watts. Watts are a measure of work being done, as in a 100-watt bulb or a 60-watt motor.

---

### Post by viciouslime on 2007-03-10
> **JAPrufrock said:**
> AC current is alternating- it goes in one direction, and then switches to the other direction.  The switching is done very rapidly;  120 changes in direction per second means that the  system goes through 60 cycles.  If the two wires to an AC motor are switched, the motor still turns in the same direction.

Just a quick warning, this only applies to the US, Mexico and Canada I believe, the vast majority of countries use 50Hz systems, the UK and the rest of the EU included.

EDIT: Just found this:[http://en.wikipedia.org/wiki/List_of_countries_with_mains_power_plugs,_voltages_and_frequencies]("http://en.wikipedia.org/wiki/List_of_countries_with_mains_power_plugs,_voltages_and_frequencies")
Seems there are a few south american countries that use 60Hz too, but most of the world is 50Hz.

---

### Post by teaker1s on 2007-03-10
Watts =volts x amps 
[ohms law]("http://en.wikipedia.org/wiki/Ohm's_law")

---

### Post by billdotson on 2007-03-10
ok thanks guys

---

