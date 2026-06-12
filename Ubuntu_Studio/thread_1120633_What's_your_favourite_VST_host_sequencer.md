---
title: "What's your favourite VST host sequencer?"
date: 2009-04-09
forum: Ubuntu Studio
---

### Post by aXXo on 2009-04-09
Recording engineers, music to video engineers, music producers...
What's your weapon of choice?


If possible give me your:

1.Fave Linux compatible

2.Fave Microsoft compatible

---

### Post by simtaalo on 2009-04-09
linux compatible = lmms supports vst effects + vsti, and is the reason why ardour can now ship vst support as part of the binary file because they reverse engineered the steinberg sdk.

microsoft compatible = i'd have to say ableton, not because of vst support but because of everything else its capable of.

---

### Post by af20001 on 2009-04-09
Linux compatible - Renoise, closely followed by Qtractor.

Windows compatible - Reaper (runs on Wine).

---

### Post by thorgal on 2009-04-09
I make my VSts standalone jack clients with FST or dssi-vst as hosts. Since I only use 2 VSTi's (no dynamic effect VSTs), this works great. I redirect MIDI sequence events (from say rosegarden, or muse or seq24) to the VSTi MIDI input, and dump the VSTi audio output to ardour for recording. Sequencer and mutlitrack recorder can be synchronized via the jack transport mode. I can add some more apps as well, that understand this transport mode (hydrogen, etc).

---

### Post by Stochastic on 2009-04-09
FST
Ardour (if you compile it to be)
Renoise

(I guess that last one is MS compatible, but I couldn't care less)

Really I find VST to be a poor plugin format for Linux as it has integration issues that aren't likely to be fixed anytime soon (even with the vestige header).  LV2, dssi, and ladspa (plugins and instruments) all get used way more than any VST stuff on my system.

---

### Post by kayosiii on 2009-04-10
Is there anything on the linux side that works well on the 64bit version of Ubuntu

---

### Post by simtaalo on 2009-04-10
as i mentioned in the other thread about production, if you use lmms doesn't matter whether you use 32-bit or 64-bit, you can still use vst effects and instruments.

---

### Post by barisurum on 2009-04-10
> Really I find VST to be a poor plugin format for Linux as it has integration issues that aren't likely to be fixed anytime soon (even with the vestige header). LV2, dssi, and ladspa (plugins and instruments) all get used way more than any VST stuff on my system.

You mentioned using LV2 plugins, which ones? Because I can't find decent LV2 instrument or effect plugins anywhere. Are they present and I don't know it? Can anyone tell about the recent developments in LV2?

---

### Post by neu2buntu on 2009-04-11
i have found package lv2core in synaptic (not sure about installing it yet until i read up on it) and the site is [[COLOR=Red]here[/COLOR]]("http://lv2plug.in/")
 
(1) lmms
(2) flstudio8 (although i have demo working in wine,wont take reg code as yet)

---

