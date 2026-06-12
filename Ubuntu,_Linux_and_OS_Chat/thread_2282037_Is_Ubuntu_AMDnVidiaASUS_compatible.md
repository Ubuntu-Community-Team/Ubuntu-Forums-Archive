---
title: "Is Ubuntu AMD/nVidia/ASUS compatible?"
date: 2015-06-11
forum: Ubuntu, Linux and OS Chat
---

### Post by odog86 on 2015-06-11
Does anyone know if Ubuntu has an issue with my hardware architecture. It runs more or less fine but there is a lot more weird bugs and glitches than when compared to my Dell laptops from the moment I install. Does anyone see anything wrong with this setup:


[LIST]
[*]**Processor: **AMD FX(tm)-6300 Six-Core Processor
[*]**Graphics:** nVidia GeForce GTX 760/PCIe/SSE2
[*]**Motherboard:** ASUS M5A78L-M LX PLUS
[*]**RAM:** 8gb
[*]**OS type:** 64-bit
[/LIST]

**EDIT:** I was wrong to title my thread just AMD. I really meant is it compatible with my setup.

---

### Post by LastDino on 2015-06-11
Ubuntu should work with that setup. Also, I don't have the system itself but I think you might need to use xserver-xorg-video-nouveau drivers because of your graphic card in case of problems with default ones.

---

### Post by QIII on 2015-06-11
Two of my machines are AMD:  one runs an FX-8350 with an R9 290X and the other a Phenom II 1100T with an HD 5870.  Both work every bit as well as my Intel machines.

We may be able to help you with your little glitches if you would care to explain a bit.

---

### Post by Bucky Ball on 2015-06-11
*Thread moved to** Ubuntu, Linux & OS Chat**.*

AMD processors work fine (you are using an AMD64bit kernel). Perhaps post a new thread(s) specific to any issues you have. Graphics card might need a bit of tweaking but we can help you with that.

Post a thread for each new issue, not five support questions in one thread. Gets confusing. Thanks and good luck with it. :)

---

### Post by wildmanne39 on 2015-06-11
I have ran all AMD processors on ubuntu for the last 7 years, if anything causes an issue it is usually the video card.

---

### Post by kurt18947 on 2015-06-11
Video card would be my guess as well. I have an AMD MoBo/processor using an Nvidia G210 card. I have the best luck using Nvidia's proprietary driver. The Nouveau driver has caused suspend/resume problems for me.

---

### Post by v3.xx on 2015-06-11
**Processor: **AMD FX(tm)-6300 Six-Core Processor

Didn't get a lot of forum hits on it, which is good in this case :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=amd+fx-6300&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=amd+fx-6300&sa=Search&cof=FORID:9)

---

### Post by odog86 on 2015-06-12
> **Bucky Ball said:**
> *Thread moved to** Ubuntu, Linux & OS Chat**.*

AMD processors work fine (you are using an AMD64bit kernel). Perhaps post a new thread(s) specific to any issues you have. Graphics card might need a bit of tweaking but we can help you with that.

Post a thread for each new issue, not five support questions in one thread. Gets confusing. Thanks and good luck with it. :)

My only hesitancy was trying to figure out the issue source and graphics driver seems consistent with my research. The only reason I haven't called out direct issues is it seems to change all the time things just work or don't periodically and I often have boot troubles. Weird messages or displays during boot that I wouldn't normally see. Will look into it.

---

