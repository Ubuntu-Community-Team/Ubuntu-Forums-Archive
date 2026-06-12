---
title: "Qmidiroute giving strange signals from drum channel"
date: 2015-04-30
forum: Ubuntu Studio
---

### Post by Veli_Martin on 2015-04-30
Hi!
I am using qmidiroute and seq24 on Ubuntu together with Yamaha MX49 synth.
I take keyboard note on messages from channel 1 and 2 and then with qmidiroute I send these to other channels.
The problem is that when I play the drum pattern on MX, it gives some note on data on channel 1 although the drums are on channel 10.
With some drum patterns this means  I get accidental notes messing up my live playing on channel 1. I use the Jack midi connection tool.

I am also using the MX with Reaper on Windows 7. Nothing comes in from channel 1 if only the drums are playing. So it seems the fault is in qmidiroute or Jack midi connections...

Also there's another bug in qmidiroute. If you try to send control messages with exact values, they get screwed up. Instead, you need to send relative values. For example, when I want midi note 100 to trigger a volume change (control 7), I must choose a relative value -93 instead an exact value 7.

Any assistance is welcome!

---

