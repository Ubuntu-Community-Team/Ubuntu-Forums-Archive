---
title: "[SOLVED] hydrogen not connecting to JACK"
date: 2008-09-06
forum: Ubuntu Studio
---

### Post by zsoltyV on 2008-09-06
I've been unable to get hydrogen connected to JACK. I get the following when starting up hydrogen while JAck is already running:

Error starting audio driver
and
Jack driver: cannot connect output port 

I changed the JACK port name in hydrogen.defaults.conf from "alsa_pcm" to "system", as per some instructions from the hydrogen website's community forum.  But it didn't seem to help anything.

Anyone else seen the same problem?  Or have any ideas how to fix this?

thanks

m

---

### Post by zsoltyV on 2008-09-10
Has anyone seen these errors in Hydrogen before?

---

### Post by cb951303 on 2008-09-10
is it just hydrogen? did you try another application?

---

### Post by Stochastic on 2008-09-10
From what I recall, you need to make sure that Hydrogen **does not** try to "auto-connect" itself to jack.  This can be changed as a check mark box in Hydrogen's properties.  Once Hydrogen is opened, then go into qjackctl or patchage and manually connect its outputs to your soundcard.

There may also need to be identical Jack parameters in both your jack setup options and in Hydrogen's sound setup options (buffer size, sample rate, etc...).

---

### Post by zsoltyV on 2008-09-18
OK got it.  I just had to uncheck the "connect to default output pair" checkbox.  

thanks for the input

---

