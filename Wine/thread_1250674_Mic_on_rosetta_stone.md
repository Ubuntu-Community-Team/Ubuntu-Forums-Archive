---
title: "Mic on rosetta stone"
date: 2009-08-26
forum: Wine
---

### Post by robbypaul on 2009-08-26
I have installed Rosetta stone and the language correctly, But i cant find how to get the microphone to work.:(

---

### Post by Mia1990 on 2009-08-27
I run Rosetta stone v3.2 it has work great better then it does in windows.I have heard that some have had problems with v2 but the set up for the mic goes the same on v3 as it does in windows.What version of wine and Rosetta stone do you have?You may look on [wineHQ]("http://appdb.winehq.org/") to see if there have been anyone else with the same problem your having.I found that wine 1.1.26 runs v3 the best you can download a deb of 1.1.26 from there website also.

---

### Post by obscenic on 2010-01-09
I have it working. Here's my theory.

Rosetta stone's mic setup attempts to adjust the windows volume control for the mic input. It required a perfect attenuation to think that it's working.  This adjustment doesn't translate through wine.

You'll need to adjust the mic gain yourself in ubuntu's sound settings panel (or mixer on ubuntu versions lower than 9.10) and then try the mic setup in Rosetta again.  It took about 7 or 8 tries for me, but now it works like a charm!

---

### Post by hypatia on 2010-06-09
Apologies for the thread necromancy, but I just wanted to report that in Ubuntu 10.04 with Wine 1.1.42 and RS 3.3.5, all I needed to do to get sound working was indeed to adjust the volume down in settings.  Thanks!

---

### Post by prince.buster on 2010-06-24
is this true? rosetta not detecting mics in wine has been a HUGE issue for quite a while now. could you please describe exactly how you got it to work by adjusting the volume?

see also the [winehq bug report]("http://bugs.winehq.org/show_bug.cgi?id=14559") - registering, confirming and voting for this bug will contribute to it being fixed ASAP

---

### Post by lindude on 2010-07-29
> **prince.buster said:**
> is this true? rosetta not detecting mics in wine has been a HUGE issue for quite a while now. 

I second that been trying every fix I can find and nothing works.
Might have to go back to windoz :-(

---

### Post by lindude on 2010-07-29
> **Mia1990 said:**
> .I found that wine 1.1.26 runs v3 the best you can download a deb of 1.1.26 from there website also.

Hi, I downloaded 1.1.26 for [9.04]("http://wine.budgetdedicated.com/archive/index.html") I couldn't find a version for 10.04.
It recognised my internal and usb mic but still they wouldn't record sound.
Also, this is a first the sound wouldn't go through usb headset even though the sound was set to go through there in my sound preferences.
Any ideas?
Do you know if there is a 1.1.26 for 10.04?
Thanks

---

