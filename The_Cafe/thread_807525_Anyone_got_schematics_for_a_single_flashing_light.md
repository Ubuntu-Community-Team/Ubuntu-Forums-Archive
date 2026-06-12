---
title: "Anyone got schematics for a single flashing light?"
date: 2008-05-25
forum: The Cafe
---

### Post by Jordanwb on 2008-05-25
Does anyone have schematics for a single flashing light. I found one online for two, but it won't work for me. A requirement is no programmable/complicated ICs.

---

### Post by NovaAesa on 2008-05-25
What about simple ICs? Are you allowed to have them? You could use a 74LS74 (JK Flip Flops) and just make a very simple finite state machine.


EDIT: Maybe this approach wouldn't work to well. For this you would need a clock pulse anyway, which I get the impression is what you trying to create.

---

### Post by aimran on 2008-05-25
How bout a flip-flop circuit? Just don't connect the other LED.

---

### Post by ZylGadis on 2008-05-26
What you are looking for is called a multivibrator. You need two transistors, four resistors, two capacitors, and a power source (and the light, of course). Look it up on wikipedia or wherever.

---

### Post by tamoneya on 2008-05-26
I second the multivibrator idea.  If you tell us what the frequency or period is that you want we can make it even more complete if you arent able to do out the equations.

---

### Post by ssam on 2008-05-26
[555]("http://en.wikipedia.org/wiki/555_timer_IC") chips are quite commonly used for flashing things.

if you want a stable 1Hz source, see [http://www.hackaday.com/2007/02/04/cheap-1-hz-clock-source/](http://www.hackaday.com/2007/02/04/cheap-1-hz-clock-source/)

---

### Post by mips on 2008-05-26
> **ssam said:**
> [555]("http://en.wikipedia.org/wiki/555_timer_IC") chips are quite commonly used for flashing things.

if you want a stable 1Hz source, see [http://www.hackaday.com/2007/02/04/cheap-1-hz-clock-source/](http://www.hackaday.com/2007/02/04/cheap-1-hz-clock-source/)


trip5 (as we called 555ics) was also the first thing that sprang to my mind. If I recall correctly you could change the frequency with a simple pot/varistor.

---

### Post by Jordanwb on 2008-05-26
> **ZylGadis said:**
> What you are looking for is called a multivibrator. You need two transistors, four resistors, two capacitors, and a power source (and the light, of course). Look it up on wikipedia or wherever.

I have schematics for that, but that schematic is for two alternating lights. I want a single flashing light that flashes at 1Hz.

---

### Post by aimran on 2008-05-26
Dont use one LED? And set the half cycle to 1Hz :P

---

### Post by Jordanwb on 2008-05-26
I guess that would work. I'm gonna keep looking though.

---

### Post by Bungo Pony on 2008-05-26
Exactly what you wanted:

[http://www.geocities.com/SiliconValley/2072/proj2.htm](http://www.geocities.com/SiliconValley/2072/proj2.htm)

---

### Post by Jordanwb on 2008-05-26
I'll take a look at that one too.

---

