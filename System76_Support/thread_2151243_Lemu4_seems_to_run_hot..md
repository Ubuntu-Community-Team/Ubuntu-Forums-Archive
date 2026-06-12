---
title: "Lemu4 seems to run hot."
date: 2013-06-03
forum: System76 Support
---

### Post by pete04 on 2013-06-03
Hi,
I'm a very happy owner of a Lemu4, but the machine always seems to run hotter than it should. 

With Thunderbird, half a dozen Chromium tabs open, and LibreOffice, the temperature will climb over 70 degrees C (monitored using sensors in the terminal). The fan will run pretty heavy for extended periods of time, though no part of the laptop feels hot to the touch.

Running Ubuntu 13.04

Thunderbird seems to be the main culprit (aside from Chromium). Replaced with Evolution, the temperature settles to a warm mid 60 degrees. 

So my question is, should this machine run that warm this regularly? It's not hitting critical temps, so it seems OK. The interesting thin is I don't see any activity on the System Monitor that looks like the system is getting taxed. No cores spiking at 100% or anything. I do notice that the machine will hit swap, even though at it's most taxed I use maybe 60+ percent of its 4gb RAM. If this is too warm, what are possible solutions?

Thanks

---

### Post by isantop on 2013-06-04
It shouldn't get critical (IIRC about 90C). If it does, that indicates a cooling problem (likely either a clogged heat sink or failing fan.) That said, 70C isn't worrying to me unless the temperature easily spikes above that or the fan isn't running.

---

### Post by pete04 on 2013-06-04
Thanks, Yeah I'm not worried either... Machine never gets hot to the touch. Just runs warm. and the fan runs. It's more a slight annoyance than anything.

It definitely seems to be tied to memory use. If I run a Firefox/Evolution tandem instead of Chromium and Thunderbird, I fare much better. Machine stays quiet. Running right now at 64 degrees.

Thanks for the reply.

---

### Post by TNFrank on 2013-06-05
Look up the specs on the machine and see what it's Critical temp is.  On my ol' HP laptop critical for the CPU is 105*C and runs in the mid'40's to mid 50's most of the time.  When I kick on my virus scan it'll go up to 80*C but then cools back down after the scan is finished.  Still, 80*C is a long way from the 110*C critical temp.  Also, most systems have a built in safety feature where they'll shut down rather then melt soemthing down.  I'd think you'll be ok but just keep an eye on temp.

---

### Post by pete04 on 2013-06-05
Critical appears to be 120 degrees, so I'm pretty safe.

---

### Post by TNFrank on 2013-06-06
Yep, if your critical is 120*C and you're at 70*C when you're running you've still got 50*C of wiggle room before you shut down.  Still, it's good that you care enough to actual monitor stuff like that.

---

