---
title: "The BEST for Editing"
date: 2010-02-15
forum: Ubuntu Studio
---

### Post by drndrw on 2010-02-15
Hey everyone. I recently purchased a Pentax K20d with a few goodies. I run strictly Linux, and knowing all of the software written, I'm looking for different photo editors, RAW processors and toner mappers for post processing my images. Does anyone have any recommendations? If you say GIMP, could you suggest a plugin or two to make it a bit more like photoshop? Thanks a bunch.

---

### Post by Aphorism on 2010-02-17
Best is obviously subjective to audience.

Seeing as how you spent money on an SLR, I'll assume that you are not in the beginner range of audience. These are assumptions based on that:

1) GIMP is out of the question. There is no deep colour manipulation in GIMP. Period. In short, it's useless for photo manipulation. If you need to see why exactly, Google posterization. Basically it amounts to data that is in your Pentax DNG or RAW format that is completely unaccessible in GIMP. There is _no_ way to overcome this, despite people believing you can 'sandwich' elements together. That sentiment is the approach of someone that is seriously lacking in experience.

2) Your RAW processing needs are likely met with one of the following applications:
2.1) dcraw. This is the backbone of everything. It is CLI based, but offers a good deal of useful output you cannot get anywhere else. Such things include chromatic aberration correction, 16 bit linear 1.0 gamma output, etc. It also will harness the full data set of your RAW photo.
2.2) ufraw. A pretty reliable 'whole image' processing set. It operates using full RAW bit depth, but is unfortunately not deep. More complex for some audience members than rawstudio. No marquee etc. Slightly above intermediate grade of toolset as a guess.
2.3) rawstudio. Batch oriented. Offers an intermediate grade quality series of tools. Another whole image application. You cannot marquee etc.

Strictly speaking, those should be enough to get you started.

If you need any further aid, feel free to email me. I rarely roam these parts.

Hope that at least gets you pointed in the right direction...

---

