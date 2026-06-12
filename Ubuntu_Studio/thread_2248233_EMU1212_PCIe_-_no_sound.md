---
title: "EMU1212 PCIe - no sound"
date: 2014-10-13
forum: Ubuntu Studio
---

### Post by bnilsson on 2014-10-13
Hi!

I am running Ubuntu Studio 14.04LTS, 64-bit.

I have a EMU1010 PCIe + 0202 sound card, and I cannot get any sound out.
After what I can see, the card is properly recognized by the system.

lspci: 
06:04.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value


I can capture ok using Audacity.
The pulse audio control shows all settings properly, and the sound monitor bar flickers as it should.

I guess the problem lies in the connection matrix with the different DSP's and to the 0202 DAC and ADC channels.
I have tried all combinations I can think of, but no success.

Capture works with this:
DSP 0 [0202 ADC Left]
DSP 1 [0202 ADC Right]

Playback should(?) work with this:
0202 DAC Left [DSP 0]
0202 DAC Right [DSP 1] 
but it does not. 
I have set all "analog" controls to 100%.
I have made sure I have sound out by touching the cables, getting the 50Hz hum.

Interestingly, I borrowed an older EMU1010 PCI (not PCIe) and there it worked!

Any suggestions?

Note: Hardware Gigabyte motherboard GA-880GMA-UD2H+Athlon X2

---

### Post by bnilsson on 2014-11-07
Solved by changing motherboard to Gigabyte GA-Q87M-D2H + Intel i3-4330.
Now all is fine.

---

