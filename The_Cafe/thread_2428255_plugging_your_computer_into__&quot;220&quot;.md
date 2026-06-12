---
title: "plugging your computer into  &quot;220&quot;"
date: 2019-10-01
forum: The Cafe
---

### Post by Skaperen on 2019-10-01
in another thread, someone who was probably having microphone feedback was reporting a hum sound.  this comes from electrical power being unbalanced with respect to ground.  in North America and a few other places with similar single-phase power (not Mexico) the 120 volt circuits are out of balance but the 240 volt circuits are balanced (people still call them "220").  many audio studios have balance circuits to eliminate the hum.  they do it with expensive equipment to give them 120 volts balanced.  but in other places with true singe-phase power, 240 volts is balanced and may be cheaper to use.  computers and other equipment using similar switch-mode power supply units can operate over the voltage range of 100 to 240 volts (100 volts for Japan, 240 volts for the rest of the world).  so, your computer should (check the ratings to be sure) be fine on 240 volts.  if there is a voltage switch, it probably needs to be changed.  then you might be eliminating hum in your audio.

where power is directly derived from three-phase power, which is common in Mexico and in some places in the rest of North America, the hum won't be eliminated, but it will be reduced to about half.  in Europe, Australia and most of Africa, Asia, balanced power is generally not cheaply available at voltage levels computers can operate on.

places with 120 volts use a pair of opposite phase live wires together to get 240 volts.  this is the balancing of power.  the balance comes from the averaging, relative to ground, being zero (or very near that).  the 120 volt circuit (one live wire and one neutral wire) has an average of 60 volts which can raise the voltage coupling of many parts to 60 volts.  that's not something you would be shocked by because almost no current can flow, but it can couple hum into unbalanced audio circuits (almost no audio equipment has balanced audio circuits throughout)..

---

### Post by uRock on 2019-10-01
I used to have an old Gibson amp that would give me a shock when wearing socks, but no shoes. The previous owner had opened it up and replaced the three prong cable with a two prong. I was the ground. I could also hear it as I walked around.

I couldn't imagine the cost of upgraded the home circuits to 240. The permits and inspections would be a nightmare.

My pool pump had the ability to be wired either way. They run cooler on 240 as less amperage is needed for that 120 gallon per minute speed. I had also learned that the capacitors, which are the likely culprit when it stops working, burn up much more frequently when using 110.

---

### Post by jeremy31 on 2019-10-01
I am not sure how using the 220V switch will work out.  In Europe the 220V is single phase with one hot wire, in the US it is single phase but the 2 120V hot wires are 90 degrees out of phase, IIRC

---

### Post by uRock on 2019-10-01
> **jeremy31 said:**
> I am not sure how using the 220V switch will work out.  In Europe the 220V is single phase with one hot wire, in the US it is single phase but the 2 120V hot wires are 90 degrees out of phase, IIRC

You're correct on the US side of it. I'm too lazy to Google the European side, lol. [https://makezine.com/2016/11/02/understanding-240v-ac-power-heavy-duty-power-tools/](https://makezine.com/2016/11/02/understanding-240v-ac-power-heavy-duty-power-tools/)

---

### Post by jeremy31 on 2019-10-01
I could wire up a normal outlet on 220V in the garage and plug my old desktop computer in, grab a fire extinguisher and press the power button

---

### Post by Skaperen on 2019-10-01
> **jeremy31 said:**
> I am not sure how using the 220V switch will work out.  In Europe the 220V is single phase with one hot wire, in the US it is single phase but the 2 120V hot wires are 90 degrees out of phase, IIRC

they are 180 degrees out of phase if it comes from one single-phase transformer with a center tap that is grounded.  this is the most common for homes and small non-industrial businesses in USA and Canada.  2nd common is 2 legs of a 208/120 three-phase system which are 120 degrees out of phase, giving 120*sqrt(3) volts (207.84609690826525 or about 208 volts).  the mid-point of the latter is still 60 volts above ground, leaving a significant amount of voltage coupling to take place.  if you connected these 2 legs of power to a center tapped transformer or inductor winding, the center tap to ground would be 60 volts and 90 degrees out of phase relative to the 208 volts between those 2 legs.  if you really want power with a 90 degree phasing, that's the simplest way to get it.  the actual power distribution does not have any 90 degree power.

---

### Post by jeremy31 on 2019-10-01
Yes, that is correct, each inductor produces a 90 degree change of phase, so the 2 make it 180.  I went to powerline distribution school 30 years ago and haven't used it much so that memory can be a bit rusty

---

### Post by Skaperen on 2019-10-01
if everything is wired correctly and the computer is switched correctly if it needs to be and has no faulty parts, you won't need to use the fire extinguisher.  you can buy a [power cord with the correct plug type]("https://www.amazon.com/NEMA-6-15P-C13-Power-Cord/dp/B004WJM2V0") for 240 volts (NEMA 6-15P to ISO-60320 C13).  a 6-15P fits in a 6-15R and 6-20R and even a 14-15R (these are nearly impossible to find).

---

### Post by Skaperen on 2019-10-01
> **jeremy31 said:**
> Yes, that is correct, each inductor produces a 90 degree change of phase, so the 2 make it 180.  I went to powerline distribution school 30 years ago and haven't used it much so that memory can be a bit rusty

that's *not* what an inductor does.  an inductor has an up to 90 degree phase difference (at power factor 1.0) _between voltage and current_.  a center tapped inductor behaves like a single phase transformer.  powered on 2 taps it can produce a voltage on the other taps.

to get the 90 degree voltage difference, the inductor will be powered at taps 1 and 3 from A and B of the three-phase secondary (208 volts).  taps 1 to 2 and 3 to 2 will have 104 volts each and the phase angle of taps 1 to 2 will be 330 degrees from N to A (N is grounded but not connected for this).  N to A is 120 volts as is N to B though these 2 are 120 degrees apart.  the sum of N to A and 1 to 2 will be 60 volts.  also N to B and 3 to 2 will be 60 volts at 180 degrees difference.  the phase angle between A to B (208 volts) and 2 to N (60 volts) will be 90 degrees.  you don't need the inductor to get the hum.  the coupled voltages (acting as capacitors so flip the phase pairings ... it still averages out the same) will still leave an average of 60 volts relative to air (ground), so there will still be hum at 90 degrees relative to the 208 volt power being supplied.

i wish i had the right kind of drawing tools to show a phase diagram for this.

---

### Post by Skaperen on 2019-10-01
> **uRock said:**
> You're correct on the US side of it. I'm too lazy to Google the European side, lol. [https://makezine.com/2016/11/02/understanding-240v-ac-power-heavy-duty-power-tools/](https://makezine.com/2016/11/02/understanding-240v-ac-power-heavy-duty-power-tools/)

in Europe they basically have the same thing but only one live wire instead of two and it is 230 volts relative to neutral (the other wire, which is grounded).  if their transformers were 460 volts center tapped, they could still get 230 volts, but with both wires, they would get 460 volts. which is too much for home computers.  the places that do get extra voltage get it from the 400/230 three-phase systems so they would get 400 volts (formerly 380 so it might still be called "380" by some).  i have seen large UPSes rated for 400 volts.

Europe also runs at 50 Hz which requires larger transformer cores to avoid saturation at the same voltage.  a transformer big enough to handle 400 volts at 50 Hz can handle 480 volts at 60 Hz.  these are common industrial voltages in Europe and North America, respectively.  the Canadians also have a 600 volt system.  another thing different between Europe and North America are the breakers in the breaker panels.  North America runs them vertical (usually 2 columns) and Europe runs them horizontally (1, 2, or 3 rows as needed).  the breakers flip horizontal in North America and vertical in Europe (makes more sense to me).

---

### Post by Shibblet on 2019-10-02
> **uRock said:**
> I used to have an old Gibson amp that would give me a shock when wearing socks, but no shoes. The previous owner had opened it up and replaced the three prong cable with a two prong. I was the ground. I could also hear it as I walked around.

***[SIZE=5]Rock and Roll Bruh![/SIZE]***

[ATTACH=CONFIG]284127[/ATTACH]

---

### Post by uRock on 2019-10-02
> **Shibblet said:**
> ***[SIZE=5]Rock and Roll Bruh![/SIZE]***

[ATTACH=CONFIG]284127[/ATTACH]

:guitar: :guitar: :guitar: :guitar: :guitar:

---

### Post by poorguy on 2019-10-02
> **uRock said:**
> I used to have an old Gibson amp that would give me a shock when wearing socks, but no shoes. The previous owner had opened it up and replaced the three prong cable with a two prong. I was the ground. I could also hear it as I walked around.


Perhaps these will explain.

[http://bustedgear.com/faq_Amp_shocks.htm](http://bustedgear.com/faq_Amp_shocks.htm)

[https://www.gearslutz.com/board/so-many-guitars-so-little-time/91481-how-ground-old-guitar-amp.html](https://www.gearslutz.com/board/so-many-guitars-so-little-time/91481-how-ground-old-guitar-amp.html)

[https://robrobinette.com/Tube_Amp_Safety.htm](https://robrobinette.com/Tube_Amp_Safety.htm)

---

### Post by uRock on 2019-10-02
> **poorguy said:**
> Perhaps these will explain.

[http://bustedgear.com/faq_Amp_shocks.htm](http://bustedgear.com/faq_Amp_shocks.htm)

[https://www.gearslutz.com/board/so-many-guitars-so-little-time/91481-how-ground-old-guitar-amp.html](https://www.gearslutz.com/board/so-many-guitars-so-little-time/91481-how-ground-old-guitar-amp.html)

[https://robrobinette.com/Tube_Amp_Safety.htm](https://robrobinette.com/Tube_Amp_Safety.htm)

Yup, I got what I paid for it. I think I traded in a few crappy Nintendo games for it. In the mid 90's I bought a Peavey Studio Pro 112 TransTube amp. The thing's old enough to drink, has been half way around the world and back, and yet, it still sounds good. I've had to crack it open and use contact cleaner on the knobs, but haven't had to replace any burnt out components.

---

### Post by poorguy on 2019-10-02
> **uRock said:**
> Yup, I got what I paid for it. I think I traded in a few crappy Nintendo games for it. In the mid 90's I bought a Peavey Studio Pro 112 TransTube amp. The thing's old enough to drink, has been half way around the world and back, and yet, it still sounds good. I've had to crack it open and use contact cleaner on the knobs, but haven't had to replace any burnt out components.
Vintage tube amps,*** a sound all of their own*** I prefer it. ;)

---

### Post by mastablasta on 2019-10-03
> **jeremy31 said:**
> I could wire up a normal outlet on 220V in the garage and plug my old desktop computer in, grab a fire extinguisher and press the power button

also add a video camera and hit record. :)

---

### Post by poorguy on 2019-10-03
> **mastablasta said:**
> also add a video camera and hit record. :)

[IMG]https://media.tenor.com/images/824841e665055dd2f9db767ab8030c49/tenor.gif[/IMG]

---

### Post by uRock on 2019-10-03
> **mastablasta said:**
> also add a video camera and hit record. :)

Also, drop a link here and go live with that feed.

---

