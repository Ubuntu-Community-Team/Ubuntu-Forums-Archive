---
title: "cpu (Ryzen?) for best audio virtualization for qemu Windows 10 guest ?"
date: 2017-09-26
forum: Virtualisation
---

### Post by Coder88 on 2017-09-26
What is the best cpu (or perhaps cpu + motherboard) combo to have the best chance at near native audio for a virtualized (using qemu, or whatever is the best virtualization platform) Winows 10 guest on linux? My ultimate goal is to see if i can do music composing on a virtual guest Windows 10 using NI Kontakt and various sample libraries [e.g. Symphobia, Cinematic Strings, EWQL Orchestra] with a digital audio workstation (Reaper.fm). I have tried this in the past but the audio latency is so poor, crackles and such; but that has been on my AMD A-10 7850K cpu (12 computer cores, 4C+8G).  I am willing to build a new cpu and motherboard, my preference being something like the AMD Ryzen 7 which would be leaps and bounds beyond my A-10 cpu, if there is a chance i could o composing on a guest Windows 10 system inside of Linux. So frustrating-- I need Windows 10 for the composing, which means mostly booting into Windows; I would much prefer Linux as my main boot into OS and then have a virtualized Windows 10 as a guest, but the audio needs to be fast. I have tried Virtualbox in the past, just not good enough with my cpu  (and 16GB ram; I will willing to upgrade to 32GB ram with a newer cpu); I thought I would try QEMU as I have read it can do some sort of hardware passthrough including possibly audio chip hardware passthrough which might greatly help with a virtual guest that requires fast audio processing. Any help or thoughts greatly appreciated.

---

