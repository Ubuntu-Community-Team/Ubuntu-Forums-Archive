---
title: "Bad sound quality with hda-intel"
date: 2009-11-26
forum: Ubuntu Studio
---

### Post by Yorirou on 2009-11-26
Hi all

I installed the Ubuntu Studio packages to my Kubuntu because I want to use my laptop as a guitar amp / multieffect.

I have a hda-intel card in my ThinkPad R500, I directly connected my guitar to the line in. Tuning works fine, but I have some problem with the effects: the quality of the sound is horrible. However on Windows with asio4all + guitar rig the sound quality is quite good (for a laptop with an integrated card of course :) ).

I started jack with qjackctl and I am using creox.

Does anyone knows anything about this problem?

---

### Post by bluesscream on 2009-11-26
did you try rakarrack as an alternative? There should be debs around but it's easy to compile it from sources.
[http://rakarrack.sourceforge.net/](http://rakarrack.sourceforge.net/)

---

### Post by eric71 on 2009-11-27
I use a Thinkpad with hda-intel (I think it's an AD1980) for recording. One trick that is necessary to get the best performance with jack with this chip is to set periods/buffer to 3 in qjackctl. I usually use 48000 for the sample rate and 512 frames per buffer. Doesn't give super low latency, but it is usable. This is with wineasio and Reaper. I'm sure you could go a little lower (i.e. 128 fpb) with a native Linux app.

---

### Post by sgx on 2009-11-28
Another vote for Rakarrack, but keep your volume low as you test it, some of the 70 odd presets are LOUD! Creox can also yield great results, its distortion units requires knowledge of terminology, and then experience. The rest of its modules are fine, and easy to get good results. You can route pretty much anything to anything, limited mainly by your computer spec. 
Cheers

---

