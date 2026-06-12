---
title: "Microphone volume on gateway t-1623"
date: 2009-05-31
forum: Ubuntu Studio
---

### Post by Geomancer626 on 2009-05-31
Hey all, I'm attempting to set up the built-in mic for my Gateway T-1623 notebook, but the volume level is incredibly low and I can't seem to find how to raise this. I've upped the levels of all recording devices through "sudo alsamixer" in the terminal, but no dice.

---

### Post by kayosiii on 2009-06-01
Many internal soundcards implement a microphone boost that can be set at a couple of different levels. Sometimes this will be implemented as a switch rather than a slider.

---

### Post by Geomancer626 on 2009-06-01
So what should I do to correct the problem?

---

### Post by MichaelSammels on 2009-06-01
Try opening terminal and type:

```
alsamixer
``` to increase the volume.

---

### Post by Geomancer626 on 2009-06-01
> **Geomancer626 said:**
> I've upped the levels of all recording devices through "sudo alsamixer" in the terminal, but no dice.

Already tried that. Thank you though.

---

