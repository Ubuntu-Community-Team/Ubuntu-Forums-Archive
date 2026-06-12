---
title: "quick question"
date: 2009-10-24
forum: The Cafe
---

### Post by mamamia88 on 2009-10-24
i plan on building a gaming pc sometime soon.  i plan to hook it up to my hdtv and use the built in speakers.  the motherboard i plan on using has onboard audio and video and has hdmi.  i plan on using a radeon 5750 as videocard which has hdmi.  if i connect it my tv via hdmi to the videocard will i get audio through the built in speakers and if not how will i?

---

### Post by Paqman on 2009-10-24
> **mamamia88 said:**
> will i get audio through the built in speakers and if not how will i?

I've never really used by ATI cards on Linux, but i'd say probably not. If not then depending on what audio in ports your TV has you can just connect from the PC to one of those.

Personally I go from S/PDIF out on my media centre PC's sound card to the optical in on my home cinema and use that for sound, with the video over HDMI straight into the TV.

---

### Post by Xbehave on 2009-10-24
ATI+linux gaming = your at the whim of flgrx and I do not know where you'd get the feature-set for that, I suspect it will include audio over hdmi, but other say flgrx is a PITA to use (I stuck with opensource for stability).

The opensource drivers do not support it yet (they don't support your car much at all tbh), here is what i wrote while figuring it out which may be relevant for people in a similar situation.

> If you dual boot for gaming then you can use radeonHD driver under linux and [this]("http://xorg.freedesktop.org/wiki/RadeonFeature") (uses chipnumbers that i don't know how to convert to cards) says that 
[RS690]("http://en.wikipedia.org/wiki/RS690") - works
[R500]("http://en.wikipedia.org/wiki/Radeon_R500")  - doesn't work
[R600]("http://en.wikipedia.org/wiki/Radeon_R600")  - Work in progras (e.g doesn't work yet)
[R700]("http://en.wikipedia.org/wiki/Radeon_R700")  - works
[evergreen]("http://en.wikipedia.org/wiki/Evergreen_%28GPU_family%29") - doesn't work (what 5750 uses)

If you are happy to use prop driver, then nvida is the way to go for linux gaming ATM (open ati drivers are coming and it may be worth putting up with ati prop drivers until they arive)

---

### Post by mamamia88 on 2009-10-24
i was planning on using windows 7

---

