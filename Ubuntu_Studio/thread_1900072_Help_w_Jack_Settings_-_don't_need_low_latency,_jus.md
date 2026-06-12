---
title: "Help w/ Jack Settings - don't need low latency, just reliability"
date: 2011-12-25
forum: Ubuntu Studio
---

### Post by decomp on 2011-12-25
Hi All!

I'm doing a mix in ardour and having problem with skipping and crackling - my computer can't keep up! I have worked out what settings I need to get low latency for recording - but for mixing I don't care if it takes a whole minute to start playing, just that it doesn't skip/crackle while playing. 

It's about 10 tracks each with their own compressors and eq's and such applied, so thats why its such a big load. without effects my computer can play it fine. Anyone have any suggestions?

---

### Post by jejeman on 2011-12-25
What is your cpu?

---

### Post by decomp on 2011-12-25
Intel Centrino Duo 1.83 Ghz

---

### Post by jejeman on 2011-12-26
Well, it's not that fast cpu. What is the precentage for cpu use? What number for samples did you set in jack, and what latency it gives you?

I use about 25 channels in Muse on 2.3 Ghz Core 2 Duo, not all of them has effects right now, with around 50% cpu usage. I used group channel to apply effects on multiple channels, to lower the cpu use. Maybe you can try something like that.

---

### Post by Sylos on 2011-12-26
Hello.

In adition to jejemans suggestion you could also try bouncing several tracks down to a single track with the effects already on - then once you have them on a single track you can delete the originals. It's a bit of an art and does mean you loose the ability to adjust the bounced tracks individually but it will help free up some resources. I do this on my current system as it is too slow - I start by bouncing like tracks together - get all the cymbals on one track, then all the toms on another etc. Its the way things used to be when people were limited to 8 tracks on hi8 tape.

---

