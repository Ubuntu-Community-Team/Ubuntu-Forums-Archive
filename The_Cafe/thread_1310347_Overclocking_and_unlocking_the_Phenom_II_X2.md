---
title: "Overclocking and unlocking the Phenom II X2"
date: 2009-11-01
forum: The Cafe
---

### Post by semitone36 on 2009-11-01
A round of cigars for everyone! I just ordered all the parts for my very first rig! Heres the specs:

-Mobo: MSI 790fx-gd70
-CPU:  AMD Phenom II X2 Black Ed. 3.1 ghz
-GPU:  x2 Radeon HD 4870
-Case: Antec P193 (some people think this looks god aweful but I LOVE its look!)

I just had a few questions for all the verteran (or retired) system tweakers out there:
1) Has anybody had success in turning this CPU into a quad core? If so, how high were you able to (stably) overclock it?

2) What programs are there for Ubuntu to test the stability of an overclocked CPU? I know about Memtest86 but im looking for something more like prime95 and also something similar to CPU-Z.

Thanks for the replies and GOD I CANT WAIT TO BUILD THIS!

---

### Post by CharmyBee on 2009-11-01
Unlocking a defective quad out of an X2 then expecting to overclock with it is not going to get you far.

I wish I could even use AMD's tools with a Kuma Athlon64 X2 7750 BE (Phenom X2). There seems to be a support gap between Phenom X3/X4 and Phenom II :(

---

### Post by Skripka on 2009-11-01
Huh?  What CPU specifically are you talking about?


The only CPU that I know of with an unlockable core, is my PhenomII720x3...which I've unlocked into a quad core.  That being said, it was quick and easy, and really provides more spunk.

---

### Post by semitone36 on 2009-11-01
[QUOTE=CharmyBee]Unlocking a defective quad out of an X2 then expecting to overclock with it is not going to get you far.
[/QUOTE]
I have heard that there are a lot of X2's that really are defective and cant be unlocked but its only like 1 out of every 5 or so... I like my odds :)

[QUOTE=Skripka]Huh? What CPU specifically are you talking about?
[/QUOTE]
AMD Phenome II X2 550 BE

---

### Post by Skripka on 2009-11-01
> **semitone36 said:**
> I have heard that there are a lot of X2's that really are defective and cant be unlocked but its only like 1 out of every 5 or so... I like my odds :)


AMD Phenome II X2 550 BE

Such settings jacks are dependent on what CPU batch # you get from, as well as the specific North Bridge, and BIOS and version on BIOS.  From what I've read both the 550x2 and 720x3 unlocks are dependent on setting the Auto-Clock-Calibration setting correctly...and after that is is a bit of luck, and correct choice of components as to if it works, and how stable it is.


In the case of the 720x3 unlock, AMD clamped down on the BIOS setting which allowed it-once word reached the internet about it.  I could overclock my FrankenCPU more, but my memory config is getting in the way, and I have no reason/want to jack it up any higher.

---

### Post by semitone36 on 2009-11-01
> **Skripka said:**
> Such settings jacks are dependent on what CPU batch # you get from, as well as the specific North Bridge, and BIOS and version on BIOS.  From what I've read both the 550x2 and 720x3 unlocks are dependent on setting the Auto-Clock-Calibration setting correctly...and after that is is a bit of luck, and correct choice of components as to if it works, and how stable it is.


In the case of the 720x3 unlock, AMD clamped down on the BIOS setting which allowed it-once word reached the internet about it.  I could overclock my FrankenCPU more, but my memory config is getting in the way, and I have no reason/want to jack it up any higher.
Thats why i went with the MSI 790fx.  They have supported the ACC feature in their BIOS since the release of v1.5 (it might still be in beta though.)

---

### Post by LowSky on 2009-11-01
I have the same chip and board. First thing to do is upgrade the BIOS, its a must. Otherwise you cant unlock it to 4 cores. Once you do it will be called a B50 instead of a 550.

I have mine overclocked to 3500.275 MHz, any higher and its unstable without a voltage increase or better heatsink

 dont believe me here is a screen picture

---

### Post by semitone36 on 2009-11-01
> **LowSky said:**
> I have the same chip and board. First thing to do is upgrade the BIOS, its a must. Otherwise you cant unlock it to 4 cores. Once you do it will be called a B50 instead of a 550.

I have mine overclocked to 3500.275 MHz, any higher and its unstable without a voltage increase or better heatsink

 dont believe me here is a screen picture

That is fantastic news! I designed my rig to be cold as ice and i have plenty of voltage standing by with a 750W psu.  Can you say 3.7+ ghz quad core for $100??

---

### Post by Skripka on 2009-11-01
> **LowSky said:**
> I have the same chip and board. First thing to do is upgrade the BIOS, its a must. Otherwise you cant unlock it to 4 cores. Once you do it will be called a B50 instead of a 550.

I have mine overclocked to 3500.275 MHz, any higher and its unstable without a voltage increase or better heatsink

 dont believe me here is a screen picture

Yep.  My Franken-Quad needs a Zalman aftermarket (air) cooler in order to clock it up to 3.65.  The stock AMD HSF and thermal compound stinks.

---

### Post by Skripka on 2009-11-01
> **semitone36 said:**
> That is fantastic news! I designed my rig to be cold as ice and i have plenty of voltage standing by with a 750W psu.  Can you say 3.7+ ghz quad core for $100??

FYI-My FrankenCPU is a bit less stable under Windows under load...and some gfx intensive games don't like it very much.  Since W7 final, I've played with going back to x3, for stability under Windows.

---

### Post by semitone36 on 2009-11-01
> **Skripka said:**
> FYI-My FrankenCPU is a bit less stable under Windows under load...and some gfx intensive games don't like it very much.  Since W7 final, I've played with going back to x3, for stability under Windows.

Oh really? Darn thats a little disappointing... Oh well maybe ill have better luck.

Anybody have an answer to my second question?

---

### Post by Skripka on 2009-11-01
> **semitone36 said:**
> Oh really? Darn thats a little disappointing... Oh well maybe ill have better luck.

Anybody have an answer to my second question?

For a CPU-Z like program, we Archers found and use:

[http://www.overclock.net/linux-unix/212320-perlmon-cpu-z-like-program-linux.html](http://www.overclock.net/linux-unix/212320-perlmon-cpu-z-like-program-linux.html)

I think they offer a Debian pkg.

I haven't played/bothered with extended stress testing my rig.  Usually if it POSTs and boots Linux/W7 without errors, it is good enuff.  My bad luck with stability has mainly been Fallout3...FWIW-Under linux I can clock and stay stable to higher frequencies than under Windows.

---

### Post by Regenweald on 2009-11-01
[http://www.frostytech.com/articleview.cfm?articleID=2461](http://www.frostytech.com/articleview.cfm?articleID=2461)

Came across this recently, thought you boys would like this for cooling. I'd definitely buy it.

---

### Post by semitone36 on 2009-11-01
Is that even on the market yet? I looked everywhere but couldnt find it. Wouldnt fit in my case anyways. The tallest I could fit would be 140mm

---

