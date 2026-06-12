---
title: "Hexter stops sound"
date: 2014-12-13
forum: Ubuntu Studio
---

### Post by andreas30 on 2014-12-13
Hey guys,
I'm new to ubuntu studio and i have the following problem.

I open Hexter and patchage, in order to make my USB midi keyboard to work and make sound.
But then, I can't play any other sounds from my computer (soptify, youtube e.t.c.)
Even when i quit the programs, I have to restart my laptop in order for anything else to work.

Any advice on that?

---

### Post by jejeman on 2014-12-13
When JACK is started there should be no sound outside JACK.
Only JACKaware applications are making sound, while JACK is running.

When quiting applications that are using JACK, make shure that JACK is dead too.

---

### Post by andreas30 on 2014-12-16
I see... So i guess now that Hexter runs JACK... And how do I stop Jack after that?

---

### Post by jejeman on 2014-12-16
Kill it.

---

