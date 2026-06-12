---
title: "Focusrite Firewire midi out issue"
date: 2013-07-11
forum: Ubuntu Studio
---

### Post by goodvibrations1984 on 2013-07-11
I'm doing some tests with my saffire pro 40 audio interface with the latest ubuntu studio version 13.04 x64.


Everything works fine in the audio world! I think it seems to work better than in windows 7. Latency is very low and, despite jack shows a lot of Xruns, the audio don't seems to have any artifacts. The mixer works fine too. It gets the values that I set up in the Windows mixer perfectly! The only thing that doesn't work in the mixer is master volume knob, who don't move when you turn the physical knob up and down, as happens in Windows. But this isn't relevant to me. 


My trouble is with midi. I have a Access Virus KB keyboard, and I use to record midi and as a sound module. In windows everything works ok with midi in and out.


In linux the interface midi out seems to have some problem. The midi input works ok. I tested it even with Reaper via Wine, using the a2jmidid to emulate the ports in alsa to be recognized by wine and it works! The problem is with the midi out. When I turn off my keyboard local control, to use the sequencer routing, some notes seems to be sustained forever. Some play, other not. I did tests with Ardour, to use the real jack midi ports and the problem was the same. So, to try to isolate the problem I just connected the midi in to midi out directly in jack control without any DAW open and the problem was the same. So, I think there's a problem with the midi out port driver. What can I do to help to solve this issue? I think just a few people are using midi hardware as sound module today. 


My system is a Intel core 2 duo with Intel Mother board. My  PCI firewire card is 


FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)


Thanks






Att,
Jose Sousa
Sound Designer
produtorjosesousa.blogspot.com.br

---

