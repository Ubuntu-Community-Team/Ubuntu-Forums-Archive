---
title: "Sound issues in Oblivion (using OSS)"
date: 2010-10-09
forum: Wine
---

### Post by FrankTheTankC on 2010-10-09
Since sound doesn't work properly using ALSA with oblivion (or at least in my experience,) i'm using OSS. Sound's all good, problem is, it's coming out of my crummy laptop speakers instead of my surround sound USB headset. Does anyone know how I could possibly fix that, or have oblivion playing nice with ALSA?

---

### Post by Progressive on 2010-10-10
Do your headphones work usually? Did you check which audio channel is set to the master channel in the ubuntu audio settings configuration?

If so, I would just try different settings in the audio tab of winecfg. Like changing from Hardware Accelerated to Emulation. Make sure OSS is the one checked, etc.

---

