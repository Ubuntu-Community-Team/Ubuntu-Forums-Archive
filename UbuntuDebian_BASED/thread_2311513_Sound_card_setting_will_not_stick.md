---
title: "Sound card setting will not stick"
date: 2016-01-27
forum: Ubuntu/Debian BASED
---

### Post by Miss_M on 2016-01-27
Hello!  I figured I'd be signing up here eventually.  I just installed Vinux (Ubuntu 14.04) on my mom's computer about a week ago, and this is my first-ever experience with Linux of any sort.  I did do a search, but couldn't find my particular issue.

My installation is on an old computer.  It has onboard sound, but also a SoundBlaster Live! Value sound card.

I keep setting the hardware preferences to use the sound card for everything, and it keeps switching back to onboard sound.  The card does work fine while the setting is correct.

How can I keep the setting on the sound card?  I am just learning all of the Linux lingo, so take it easy on me.  :)

Thank you!

---

### Post by howefield on 2016-01-27
Thread moved to the "*Ubuntu/Debian BASED*" sub forum.

---

### Post by Rob Sayer on 2016-01-29
It may be something related to the desktop environment.  Which DE do you have there?

---

### Post by Miss_M on 2016-02-04
I'm terribly sorry I took so long to get back!  (Been working on taxes.)

I am running the MATE environment.

---

### Post by bcschmerker on 2016-02-05
Is it possible to disable the planar sound chip in BIOS Setup?  ALSA must be detecting it first, making it default rather than what I presume your Creative Laboratories® CT4670 PCI audio card (E-MU®/Creative Technology EMU10K1-NDF DSP).

---

### Post by Miss_M on 2016-02-05
I will try this later today and give an update.  Thank you!

---

### Post by Miss_M on 2016-02-07
Thank you,  				 				 					 						 	**[COLOR=#000000]bcschmerker[/COLOR]**, this seems to have done the trick!  Now that the SoundBlaster is the only sound option, it is using it.  I can't see any reason why it wouldn't stick this time... I've never seen the BIOS change a setting I did.

Thanks again!!

---

