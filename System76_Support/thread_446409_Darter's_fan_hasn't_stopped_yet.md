---
title: "Darter's fan hasn't stopped yet"
date: 2007-05-16
forum: System76 Support
---

### Post by perce on 2007-05-16
Hello,

my new Darter has just arrived. It has been on for 15 minutes about, and the fan hasn't stopped yet. That's sad, since I've red in the forum that it's supposed to be a quiet machine. Any suggestion?

---

### Post by Rotarychainsaw on 2007-05-16
Something may not be right, my darters fan is not usually on. You have it on a carpet or something?

---

### Post by perce on 2007-05-16
No, on a hard table. But the noise and he air don't come from the grid un the bottom, but from the one on the right.

All ACPI seems badly broken: I've tried suspend once and hybernate twice and they have never worked. This is not what I expected when I decided to buy a laptop with Linux preinstaled.

---

### Post by thomasaaron on 2007-05-17
> But the noise and he air don't come from the grid un the bottom, but from the one on the right.

That's the way it is supposed to be.

> I've tried suspend once and hybernate twice and they have never worked.
You should follow this bug report. [https://bugs.launchpad.net/system76/+bug/114675](https://bugs.launchpad.net/system76/+bug/114675)
I think something came down from Ubuntu that hosed something. This has not always been a problem with the Darter.

I now have suspend working on our test darter. Still working on hibernate. Then we will send the fix down.

> It has been on for 15 minutes about, and the fan hasn't stopped yet.
How about now? Does it seem to be cycling?

Best,
Tom

---

### Post by perce on 2007-05-17
> **thomasaaron said:**
> 

How about now? Does it seem to be cycling?



The noise, which I assume is the fan, is almost always very low, so probably the fan is almost always at minimum speed, but it never stop. It's not an issue if I'm in a room with other noises, but it becomes annoying if the room is silent. I really hope to have it fixed, because what convinced me to buy a Darter was hat I read in he forum that it is (supposed to be) quieter than the average.

I will try the bugfix later.

---

### Post by perce on 2007-05-17
I haven't tried the bugfix, however I don't expect it will work: trying to resume I don't get a black screen, but a black screen with some random coloured strips and a distorted mouse cursor on the top leftmost  corner. 

And what about the noise?

---

### Post by thomasaaron on 2007-05-17
If the fan speed is cycling, it is probably OK.
I'm having difficulty understanding the level of noise you are hearing.

Regardless, I'm not sure it can be made quieter...
When my Darter's fan is running on low, I can't hear it -- but my office is not completely silent.

---

### Post by Rotarychainsaw on 2007-05-17
My fan is off most of the time, no air from the side at all. I guess its possible somehow.

---

### Post by cowbean on 2007-05-17
> **perce said:**
> The noise, which I assume is the fan, is almost always very low, so probably the fan is almost always at minimum speed, but it never stop. It's not an issue if I'm in a room with other noises, but it becomes annoying if the room is silent. I really hope to have it fixed, because what convinced me to buy a Darter was hat I read in he forum that it is (supposed to be) quieter than the average.

I will try the bugfix later.

You might want to install sensors-applet (which might also require lm-sensors, not sure), and add that to your panel.  Then you can see if the fan is on because your machine is running hot... I find that the machine is pretty much silent at 51 C, and at 53 C the fan kicks in (or up a notch) to start cooling.  If there's some processor-hungry task running constantly, the temperature will want to edge upwards all the time.

---

### Post by perce on 2007-05-17
> **thomasaaron said:**
> If the fan speed is cycling, it is probably OK.
I'm having difficulty understanding the level of noise you are hearing.

Regardless, I'm not sure it can be made quieter...
When my Darter's fan is running on low, I can't hear it -- but my office is not completely silent.

It's difficult to quantify a noise. Say a little as someone breathing.  Probably I'm being too picky. I've definitely seen much louder laptops, but today I've checked a Mac, and it was completely silent.

---

### Post by perce on 2007-05-18
The saga goes on: now the disk too is making some noise at intervals of few seconds. It didn't do that yesterday. I remember someone else had a similar problem too. How can I see what program 
is using the disk?

Thank you

---

### Post by perce on 2007-05-20
> **cowbean said:**
> You might want to install sensors-applet (which might also require lm-sensors, not sure), and add that to your panel.  Then you can see if the fan is on because your machine is running hot... I find that the machine is pretty much silent at 51 C, and at 53 C the fan kicks in (or up a notch) to start cooling.  

I've installed sensors-applet and lm-sensors. The applet displays only the temperaure from ACPI, it is constantly between 51 and 53. The cycling of the fan doesn't seem related to the temperature displayed by the applet, and in any case I can always hear the noise of the fan, even at 51. However the intensity of the noise changes. When the noise is at the minimum, I don't feel any air coming out of the grid on the right. 

Even if I've installed lm-sensors, the applet doesn't display any data from it.

Also, the file /proc/acpi/fan/FN00/state always says "off". I don't know if it is the same on yours, but I really suspect that there is something wrong in mine, either in ACPI or in the BIOS,

---

### Post by perce on 2007-05-26
I've just upgraded the BIOS from 302 to 305, and the computer seems much noisier now. It looks like it's trying to stay below 50 C, while before it was allowed to go to 52-52 C without increasing the fan speed. Staying at a lower temperature is probably better for the components, but it's not better for my ears.

---

