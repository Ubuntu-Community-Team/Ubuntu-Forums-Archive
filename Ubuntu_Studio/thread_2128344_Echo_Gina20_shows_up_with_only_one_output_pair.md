---
title: "Echo Gina20 shows up with only one output pair"
date: 2013-03-22
forum: Ubuntu Studio
---

### Post by hungryforbread on 2013-03-22
So I have an Echo Gina 20 PCI audio interface, with the 8 outs and 2 ins on the breakout box. Ubuntu Studio 12.04 recognized it right away on install, but I can't seem to access more than the first pair of outputs. In Windows I could pick a driver for some app, and I would have four different drivers for the four different output pairs. Now I just get the Gina20 showing up as a single device, and I can't seem to choose between outputs. I want to be able to use the individual outs in programs like Renoise, where normally you can select which output each track or bus goes out to.

I am completely new to Linux. I am motivated to get good at this stuff, but I basically know nothing about this operating system.

Any ideas?

---

### Post by jejeman on 2013-03-23
If you use pulseaudio go to soundpreferences and look on hardware tab for diffrent profile. If it has profiles, choose profile you need e.g. 8 out 2 in.
If you don't use pulseaudio look in alsamixer for switch to setup diffrent channel configurations.

---

### Post by zequence on 2013-04-04
Check out [https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro)

---

