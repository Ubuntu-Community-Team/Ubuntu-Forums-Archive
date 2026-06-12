---
title: "4k output from bonw9 with trusty"
date: 2016-12-15
forum: System76 Support
---

### Post by neogeek83 on 2016-12-15
As a programmer, I like my desktop real estate, so i recently bought a 43" 4K TV (Vizio E43u-D2) with the plan of using it as a monitor (yes, I know it's no go for gaming, refresh rates, etc). When I plugged it it, bingo, 4k output from my laptop to the TV, everything is great that whole day, so much workspace!

I leave the laptop on for the night running some background tasks but turn the TV off figuring I don't need to waste power.

Next morning, I come back into the office and switch the TV back on, only to be greeted with a big "No Signal" on the HDMI input I'm using. I check the Displays on the laptop, shows it's output to the TV @ 4k still. Restart TV->"No Signal". Disable/re-enable output from laptop display again->same "No Signal". Restart Laptop -> TV's back to accepting the 4K input. Okay cool. Same deal the next day. So now I'm back to forced restarting my laptop daily.

The question: Is there anyway to force the graphics driver to re-sync with the TV via HDMI while it's running? Like it does on startup? I've searched around in the **Displays** window as well as the **NVIDIA X Server Setting. **I did notice that when it's working nvidia reports refresh rate @ 29.997Hz, but when it's not it's reporting 30Hz.

Any thoughts folks? I tried to search around but didn't get a single hit in the forum search for 4k, I can't imagine I'm the first one to try this!

---

### Post by neogeek83 on 2016-12-15
Oh, couple other details I forgot to mention:
 - Suspending and then resuming the box also works to resync the hdmi output.
 - some versions:
   + Graphics card: GeForce GTX 970M
   + nvidia driver v367.57
   + System76 Driver v14.04.32
   + Up to date on updates as of this morning, running 14.04 but with the updated 4.x kernel( Linux pc-hostname 4.4.0-53-generic #74~14.04.1-Ubuntu SMP Fri Dec 2 03:43:31 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux )
   + High quality shielded HDMI cable
 - Didn't mention it before, but unplugging / replugging the cable doesn't help

---

