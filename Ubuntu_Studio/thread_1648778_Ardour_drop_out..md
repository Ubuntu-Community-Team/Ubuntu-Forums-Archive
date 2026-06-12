---
title: "Ardour drop out."
date: 2010-12-19
forum: Ubuntu Studio
---

### Post by treed1134 on 2010-12-19
I am using a Dell Oplitlex 170L 2g ram with Ubuntu Studio. I have a Prsonus FP10. I have everything installed correctly and I can get the fp10 to turn on and track audio, but upon playback I get major dropout. This exact setup worked fine when I had windows 7 and sonar installed with no dropout problems. I am assuming it is a configuration problem I just can't figure out. I am very new to Ubuntu Studio. Any help would be much appreciated!
thank you
Tony

---

### Post by Pablo_F on 2010-12-19
Hi, 

How are you starting the jack server? Audio configuration tab of ardour or qjackctl (aka Jack Control)?

---

### Post by treed1134 on 2010-12-19
I'm pretty sure it's with the jack control, but I am not 100% sure. I am very new at this.
Thanks!

---

### Post by Pablo_F on 2010-12-20
Hi, 

Sound and Video Menu, Jack Control. You setup the jack server by means of the setup button and start the server by means of the Start button. Then you launch ardour.

Please give the terminal output of the following informative commands (copy and paste):

**ffado-diag**

**ffado-test ListDevices**
[B]
cat ~/.jackdrc[/B]

**jackd -V**

I think this is enough to start trying helping you, if not myself, someone else will chime in. 

Cheers, Pablo

---

