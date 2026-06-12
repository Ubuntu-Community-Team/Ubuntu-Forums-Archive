---
title: "LED circuit help"
date: 2010-05-11
forum: The Cafe
---

### Post by hambone79 on 2010-05-11
I need some help from an electronics guru...

I have a circuit that I'm trying to build that uses a non-mercury tilt switch to turn on an LED. It is a 12V circuit that uses a 470 ohm resistor and a red LED, but I'm running into a small issue with false positives from the tilt switch. I need some way to control the LED so that it will only turn on after the switch is active for X amount of time. Also, I need to build this as cheap as possible and without the aid of a micro controller.

Any ideas?

---

### Post by detroit/zero on 2010-05-11
There's any number of solutions, and they all depend on how much you can spend and how many components you want to use.

A switch with a timed input threshold could easily be accomplished using a 555 Timer set as a one-shot (monostable multivibrator) with an RC time constant of your choosing - 500ms, 1sec, 5sec, whatever. 

Thing about a one-shot is you'd have to latch the output. (And then how to control the turn-off time? You'd need a second timer, a second latch... or manually reset it, or have it stay on for a timed duration, up to you, really.) 

You could use a latch (easily made with two NOR gates), you could use an op-amp (voltage follower), a flip-flop..

Given your 12V source, CMOS would be required unless you produce a 5V source for TTL circuitry. If you use CMOS, it can source enough current to drive an LED, but if you use TTL, you'd need another transistor to provide the current to avoid loading down the logic chips - though a single LED shouldn't really be a problem, better safe than smoky.

Those are just a few quick ideas. If you have schematics or more details on what you're doing, please provide them. I can be more specific the more I know about what I'm working with.

---

### Post by cookiecruncher on 2010-05-11
This IS the community Cafe, so I guess anything goes :D

---

### Post by standingwave on 2010-05-11
[Debouncing a switch]("http://www.all-electric.com/schematic/debounce.htm")

The value of the capacitor controls the sensitivity.

---

### Post by Zoot7 on 2010-05-11
Another vote for the usage of a 555 timer with maybe the likes of a D Flip Flop with its input tied to logic high to set the on time. 

As for false positives on the switch, switch debouncing is a must. You can be very surprized with the amount of bouncing that can occur with some switches, I found in the past some Push-To-Make ones can bounce for in or around a microsecond. 

Here's another more elegent way than the above one to debounce a switch using an S-R Latch (See Figure 3)
[http://www.elexp.com/t_bounc.htm](http://www.elexp.com/t_bounc.htm)

---

