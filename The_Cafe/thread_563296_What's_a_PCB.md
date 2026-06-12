---
title: "What's a PCB?"
date: 2007-09-29
forum: The Cafe
---

### Post by drndrw on 2007-09-29
Hey guys. I did a few Wikipedia searches on a PCB (printed circut board), but I still don't get a few thing about them. Firsts of all, what do they do? Second, is a motherboard or can motherboards be a PCB? Third, what else can you make out of a PCB? Thanks.

---

### Post by stalker145 on 2007-09-29
> **drndrw said:**
> Hey guys. I did a few Wikipedia searches on a PCB (printed circut board), but I still don't get a few thing about them. Firsts of all, what do they do? Second, is a motherboard or can motherboards be a PCB? Third, what else can you make out of a PCB? Thanks.

YES!! FINALLY!! My area of expertise :)

OK, PCB's (AKA CCA's - Circuit Card Assembly) are in just about any form of modern electronics that we use today. Computers, cell phones, alarm clocks, and a ton of other things. Yes, a mother board is a PCB.

The job of a PCB is to hold the components within a given item and allow those components to do their jobs. Such as, you have a number of capacitors, transformers, and resistors set on a PCB in a certain layout to make either a step-up or step-down transformer. You might have some inductors, diodes, and resistors laid out to make a series of filters to remove unwanted noise from your stereo.

Blah - it's all a pain in the rear if you ask me, but it works.

What exactly are you wishing to do and how can we help?

---

### Post by HermanAB on 2007-09-29
It is a laminate of plastic, glass and copper and connects everything together.  It really is the 'board' of a mother board.

---

### Post by regomodo on 2007-09-29
Printed circuit board.

Basically a fibreglass board with multiple layers of copper (if you want) to signify different layers of a circuit (if you want/can afford it)

So far i have only designed dual sided boards ( 8 mil route/pad/gap rules) but you can put more than that if you want/know/can afford

@staler145=- you've complicated the issue.Basically, if you can shrink your design to more than 1 layer (side plus extras) then you are efficiently using a pcb. Saying that you may not want separate projects on sheet of PCB

TBH, if you have no idea what a PCB is, don't create a gerber file, send it to a PCB manuf' house and expect it to be correct. Unless you are sharp/ lucky/ flukey, it won't. Use breadboards instead

---

### Post by stalker145 on 2007-09-29
> **regomodo said:**
> @staler145=- you've complicated the issue.Basically, if you can shrink your design to more than 1 layer (side plus extras) then you are efficiently using a pcb. Saying that you may not want separate projects on sheet of PCB

Sorry, just giving a few minor examples in the face of a lack of information. 

I am aware, though, that it's best practice to combine functions. In fact, I work mostly on multilayer boards repairing laminate, relaying runs, and replacing components after first troubleshooting via ATE or multimeter/schematics. My typical day consists of microminiature SMD's (attached if you don't know) that make me yearn for the comfort of a padded cell.

As before: I wonder what the intent is of the OP.

---

### Post by slimdog360 on 2007-09-29
> **drndrw said:**
> Hey guys. I did a few Wikipedia searches on a PCB (printed circut board), but I still don't get a few thing about them. Firsts of all, what do they do? 
a board which uses conductive copper paths (as opposed to big thick wires) on it to connect resistors etc together.
> **drndrw said:**
> Second, is a motherboard or can motherboards be a PCB?
yes
> **drndrw said:**
> 
 Third, what else can you make out of a PCB? Thanks

space ships and toasters, nothing else!!!1

---

### Post by drndrw on 2007-09-29
Okay, cool. Someone mentioned a breadboard also. I think I've seen those. They are already etched or something, so you can just slip the little chips into place, correct? But would one of those actually function if you were to say build a motherboard on it? And is there any welding invloved in building either of these?

---

### Post by John.Michael.Kane on 2007-09-29
> **drndrw said:**
> Okay, cool. Someone mentioned a breadboard also. I think I've seen those. They are already etched or something, so you can just slip the little chips into place, correct? But would one of those actually function if you were to say build a motherboard on it? And is there any welding invloved in building either of these?

Breadboarding is a method used to make temporary circuits for testing, and for trying out an idea. No soldering is required so it is easy to change connections.

Another method that is sometimes employed is what's known as Point-to-point construction or free-form construction. Theres also the use of Stripboard.

---

### Post by drndrw on 2007-09-30
Ah, okay. So you could use EPROM things and whatnot on a breadboard? But then you would need wires, correct?

---

### Post by John.Michael.Kane on 2007-09-30
> **drndrw said:**
> Ah, okay. So you could use EPROM things and whatnot on a breadboard?
Yes, you can connect capacitors ic's  led's, and depending on the design it can powered via 9v .

> **drndrw said:**
> But then you would need wires, correct?

Yes breadboarding still requires the use of solid (not stranded) wire usually 22AWG or smaller,


You know it might be easier if you told us what your trying to do.

---

### Post by hockey97 on 2007-09-30
A PCB is  used to shrink circuits.. 

well for example,  like if your making a custom computer, you make the mother board, and you have a small case that the mother board would be put inside it, well first off pcb is just one sheet of fiberglass, with copper you etch the copper using chemicals to match your circuits the traces, so if the computer has hundreds or hundereds different circuits,
if you put that on one sheet , the size of the mother board would be as big as a room depending on how much circuitry you are doing.
so in order to make it fit in that case, you would need a multi layered pcb which has like 7 or as many as you want but it's like taking 7 sheet's of circuits and smooshing them as one.

a pcb is nothing but a fiberglass board with underit has copper traces.
motherboards use mutilayered pcb's.

if you go to radio shack they have these just one sheet pcb, where on top you put the components and the botton has a plate of copper, you get a thing sheet of transparent paper print your schematic on the transparent sheet of paper,  cut the schematic traces out like closely cut along your traces,, so then you get the etching solution radio has this, you then tap the your schematic  onto the plate of copper then use the etcher, this will eat the copper and if you put the schematic on right then you should haver after done etching nothing put the traces left over, in copper.

---

### Post by jpkotta on 2007-09-30
Once you get into a certain performance regime, breadboards are ineffective.  They're simply too noisy (so are badly designed PCBs).  When they start to fail depends on what you're doing (analog vs. digital, clock speed, voltage level, etc.).  You cannot build a motherboard on a breadboard, at least not anything comparable to even an old PC.  You might use a breadboard to test a filter circuit for the power supply, or a temperature sensor, but not a memory bus.

---

### Post by hardyn on 2007-09-30
it is also a class of chemical compounds, Polychlorinated biphenyls (PCB)... just to confuse people.

---

