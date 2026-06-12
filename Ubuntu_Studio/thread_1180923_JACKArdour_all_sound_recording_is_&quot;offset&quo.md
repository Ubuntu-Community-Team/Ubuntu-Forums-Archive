---
title: "JACK/Ardour: all sound recording is &quot;offset&quot;"
date: 2009-06-07
forum: Ubuntu Studio
---

### Post by Nathan_M on 2009-06-07
Hi,
Whenever I try and record anything in Ardour, the sound is offset... that is, the centre isn't where it should be. If I stop JACK, and record in Audacity, there isn't a problem. I'm using the real-time kernel (but without JACK having real-time priority... separate issue which I'll try and solve later). Any ideas?

---

### Post by kayosiii on 2009-06-07
It's hard to know exactly what you mean by offset...

Do you mean the waveform is has a DC offset - I think you can use a ladspa plugin to remove this... 

or do you mean offset in time - in which case you need to make your frames/period value smaller in jackctl.

---

### Post by Nathan_M on 2009-06-09
> **kayosiii said:**
> It's hard to know exactly what you mean by offset...

Do you mean the waveform is has a DC offset - I think you can use a ladspa plugin to remove this... 

or do you mean offset in time - in which case you need to make your frames/period value smaller in jackctl.

Sorry, DC offset is what I meant. The problem is it's quite a big offset, so it dramatically decreases my headroom. Using post-recording processing is fine, but I'd like to make full use of the available dynamic range.

---

