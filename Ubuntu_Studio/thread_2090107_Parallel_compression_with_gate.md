---
title: "Parallel compression with gate"
date: 2012-12-01
forum: Ubuntu Studio
---

### Post by Thinkin on 2012-12-01
We have been having a tough time with sound variation/volume between viddos and audio.  is there a tuorial on using jack and/or calf which can assist with expanding or compressing the audio before it gets to the sound board?

---

### Post by AstroLlama on 2012-12-03
what sound programs are you running? Audacious has built in functionality for compression (uses same LADSPA plugin).

Even if it's for other programs it shouldn't be too difficult. You'll basically be running your output into the desired effects chain (jackarack or Lv2rack) then sending that output to the final master out. 

if it's for multiple uses you can make "permanent" connections through the patchbay dialog. Sorry I don't have time to make a tutorial for you!

---

