---
title: "Audacity and Ardour won't record from my Scarlett 2i2"
date: 2015-05-02
forum: Ubuntu Studio
---

### Post by adam142 on 2015-05-02
I have the 2i2 selected as the input device and interface in QjackCtl, which I assume means that Jack recognizes it. However, when I attempt to record my guitar in either Ardour or Audacity, nothing is picked up. The connection between the guitar and the 2i2 seems to be working because the gain light is lighting up appropriately. I'm completely new to recording music in linux obviously, so I'm not sure what to do next.

---

### Post by jejeman on 2015-05-04
Give us
```
aplay -l
```
Can you monitor the sound via JACK by conecting directly capture and playback?

---

