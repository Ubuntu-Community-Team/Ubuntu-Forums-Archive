---
title: "No Sound with Hydrogen"
date: 2009-10-16
forum: Ubuntu Studio
---

### Post by vaughnm on 2009-10-16
Hi guys, 

I have an issue with Hydrogen.
I get no sound with it.
I'm using an Edirol audio interface and in my sound preferences i have it set correctly. I'm using Jaunty with no rt kernel.
Can anyway one give me a hand?

---

### Post by vaughnm on 2009-10-18
anyone?

---

### Post by PorkyPie on 2009-10-18
Have you configured it in Hydrogen? Go to File -> Preferences -> Audio System and configure it there. Hope it helps.

---

### Post by sgx on 2009-10-18
> **vaughnm said:**
> Hi guys, 

I have an issue with Hydrogen.
I get no sound with it.
I'm using an Edirol audio interface and in my sound preferences i have it set correctly. I'm using Jaunty with no rt kernel.
Can anyway one give me a hand?

Need more info, are you getting sounds from other apps?
Are you using patchbay software like qjackctl, patchage, or
kaconnect/qjackconnect to connect Hydrogen to the proper output?

You must have jackd running, start it with the qjackctl gui. You may need to set up the edirol first, if you get no sound from your other apps.

Then start hydrogen, by default, it should connect to 'system' in the audio tab that appears when you press the 'connect' button, in the bottom left of the qjackctl interface. 

load a demo song, press play on the transport.

When making your own beats, each instrument plays when you place it on your grid. Keep the pattern playing as you audition what where and when to add to your masterpiece. Change the resolution higher, for more precision/variety of sound placement.

Timemachine is handy to record a few bars (in .w64 format) if you want
to make loops, or just let it record longer as needed.

(Click the little  +  signs in qjackctl to see more detail of each item.)

Cheers

---

