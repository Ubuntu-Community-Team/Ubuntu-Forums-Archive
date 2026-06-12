---
title: "Sound card and monitoring"
date: 2009-10-26
forum: Ubuntu Studio
---

### Post by Sylos on 2009-10-26
Hello all.
Im looking into buying a decent quality audio interface PCI card. I have my eye on an M Audio Delta 66 card which appears to be well supported. However, I have noticed that the card doesnt have the normal output mini jack sockets you get on a bog standard sound card. I currently have the headphone socket on my onboard sound hooked up to my stereo which i how I listen back. 
Is it possible to use the onboard to listen back to the sound/monitor rather than the outputs of M Audio?
If I have the M audio installed then when I boot into my normal ubuntu (rather than the studio set up) can I still use the onboard sound for watching films, listening to music etc.

I realise these are probabbly pretty simple and obvious questions but I am totally new to the computer recording set up.

Many thanks

---

### Post by gareththegeek on 2009-10-27
If you are using jack to manage sound you can select the onboard card for output and the delta card for input.

However if you want to enable low latency recording to get the most out of your delta card your onboard card will probably be unable to play back without causing xruns in jack.

This is the problem I had so I just bought a cable to adapt the large jack sockets of my Delta 44 to my speakers.

---

