---
title: "Distributed Computing Projects"
date: 2005-08-29
forum: The Cafe
---

### Post by jdong on 2005-08-29
I've just added front and rear thermoresistor fans, and verified that the cooling system is acceptably quiet and effective during sustained loads. Excellent. Now, I don't want my CPU just sitting there idle 80% of the times when I'm not doing Backports, so I need some distributing computing stuff to do. Anyone know of a good project to donate to? I have some criteria:


1) It has to be for a good cause. I'm thinking of like a Folding@Home or disease-curing type project, **not looking for aliens...** ;)

2) It has to run under Linux... duh! I'd prefer it to have some sort of GUI readout so I can monitor it if I'm bored, but that's purely optional!

3) Preferably I'd like AMD64 binaries available, or source for me to make AMD64 binaries.... but that's optional, too!


I know about Folding@Home... any others I should know about?

---

### Post by majikstreet on 2005-08-29
[QUOTE=jdong]I've just added front and rear thermoresistor fans, and verified that the cooling system is acceptably quiet and effective during sustained loads. Excellent. Now, I don't want my CPU just sitting there idle 80% of the times when I'm not doing Backports, so I need some distributing computing stuff to do. Anyone know of a good project to donate to? I have some criteria:


1) It has to be for a good cause. I'm thinking of like a Folding@Home or disease-curing type project, **not looking for aliens...** ;)

2) It has to run under Linux... duh! I'd prefer it to have some sort of GUI readout so I can monitor it if I'm bored, but that's purely optional!

3) Preferably I'd like AMD64 binaries available, or source for me to make AMD64 binaries.... but that's optional, too!


I know about Folding@Home... any others I should know about?[/QUOTE]
 google search distrubuted computing...

heres one: [http://distributedcomputing.info/projects.html](http://distributedcomputing.info/projects.html)

---

### Post by parktownprawn on 2005-08-29
[QUOTE=jdong]I've just added front and rear thermoresistor fans, and verified that the cooling system is acceptably quiet and effective during sustained loads. Excellent. Now, I don't want my CPU just sitting there idle 80% of the times when I'm not doing Backports, so I need some distributing computing stuff to do. Anyone know of a good project to donate to?[/QUOTE]

The [Boinc](http://boinc.berkeley.edu/) project is great. Its a framework for controling multiple distributed computing projects. You can decide which projects your computer will work on and how much time it will spend on each. available projects (other than SETI) include 

- Climateprediction.net: study climate change 
- Einstein@home: search for gravitational signals coming from pulsars
- LHC@home: improve the design of the CERN LHC particle accelerator
- Predictor@home: investigate protein-related disease

---

### Post by jdong on 2005-08-30
Alright, currently I'm running Folding 32-bit, which seems good enough for now :)

After about 24 hours of folding @ 2000MHz (turned off CnQ), CPU temp is stable at 55 degrees C. That concerned me initially, but further investigation showed that this temperature is largely due to my motherboard's auto fan control, which tries to maintain the temp around 55 degrees. The chip usually runs low loads at 55, too, since it goes into passive cooling. From my research, the Athlon64 ClawHammer 3000+'s can withstand 60 degrees with stability, and you don't risk permanent damage until at least into the 80's.

Seeing how I've been at 55 degrees for 23 hours now, I don't think it'd rise by much, so I'm hoping it's safe to continue. We shall see :)


Starting my second WU now.

---

### Post by majikstreet on 2005-08-30
[QUOTE=jdong]Alright, currently I'm running Folding 32-bit, which seems good enough for now :)

After about 24 hours of folding @ 2000MHz (turned off CnQ), CPU temp is stable at 55 degrees C. That concerned me initially, but further investigation showed that this temperature is largely due to my motherboard's auto fan control, which tries to maintain the temp around 55 degrees. The chip usually runs low loads at 55, too, since it goes into passive cooling. From my research, the Athlon64 ClawHammer 3000+'s can withstand 60 degrees with stability, and you don't risk permanent damage until at least into the 80's.

Seeing how I've been at 55 degrees for 23 hours now, I don't think it'd rise by much, so I'm hoping it's safe to continue. We shall see :)


Starting my second WU now.[/QUOTE]
 hmm-- i tried folding using the client from the site and it never progressed on me... maybe it's just my computer (not thaaaaaaaaaaaaat fast)

---

### Post by jdong on 2005-08-30
I've just heated my room from 78 to 82 degrees F, and it's officially declared unbearable. Folding will resume during the winter :)

---

